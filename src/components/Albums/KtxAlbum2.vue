<template id="web">
  <HeaderComp />
  <div class="container" ref="container">
    <div class="grid-item" v-for="(image, index) in images" :key="index">
      <a
        :href="image.href"
        data-fancybox="gallery"
        :data-caption="image.caption"
      >
        <img
          :data-src="image.src"
          :alt="image.caption"
          class="lozad blur-up"
          :width="image.width"
          :height="image.height"
        />
      </a>
    </div>
  </div>
  <PaginationComp
    :totalPages="totalPages"
    :links="links"
    @page-changed="handlePageChange"
  />
  <FooterComp />
</template>

<script>
import { Fancybox } from "@fancyapps/ui";
import lozad from "lozad";

import HeaderComp from "../Headers/Header2Comp.vue";
import FooterComp from "../FooterComp.vue";
import PaginationComp from "../PaginationComp.vue";

export default {
  name: "GalleryComponent",
  components: {
    HeaderComp,
    FooterComp,
    PaginationComp,
  },
  data() {
    return {
      // w_800,q_auto,f_auto
      images: [
        {
          src: "https://res.cloudinary.com/ddhyr7ejn/image/upload/w_800,q_auto,f_auto/v1722277972/FE7A0809_lyev5b.jpg",
          href: "https://res.cloudinary.com/ddhyr7ejn/image/upload/v1722277972/FE7A0809_lyev5b.jpg",
        },
        {
          src: "https://res.cloudinary.com/ddhyr7ejn/image/upload/w_800,q_auto,f_auto/v1722277974/FE7A0817_e88rhn.jpg",
          href: "https://res.cloudinary.com/ddhyr7ejn/image/upload/v1722277974/FE7A0817_e88rhn.jpg",
        },
        {
          src: "https://res.cloudinary.com/ddhyr7ejn/image/upload/w_800,q_auto,f_auto/v1722277975/FE7A9881_cibccl.jpg",
          href: "https://res.cloudinary.com/ddhyr7ejn/image/upload/v1722277975/FE7A9881_cibccl.jpg",
        },
        {
          src: "https://res.cloudinary.com/ddhyr7ejn/image/upload/w_800,q_auto,f_auto/v1722277974/FE7A9903_qrceyv.jpg",
          href: "https://res.cloudinary.com/ddhyr7ejn/image/upload/v1722277974/FE7A9903_qrceyv.jpg",
        },
        {
          src: "https://res.cloudinary.com/ddhyr7ejn/image/upload/w_800,q_auto,f_auto/v1722277975/IMG_2217_hjy3xs.jpg",
          href: "https://res.cloudinary.com/ddhyr7ejn/image/upload/v1722277975/IMG_2217_hjy3xs.jpg",
        },
        {
          src: "https://res.cloudinary.com/ddhyr7ejn/image/upload/w_800,q_auto,f_auto/v1722277976/IMG_2255_bohgzp.jpg",
          href: "https://res.cloudinary.com/ddhyr7ejn/image/upload/v1722277976/IMG_2255_bohgzp.jpg",
        },
        {
          src: "https://res.cloudinary.com/ddhyr7ejn/image/upload/w_800,q_auto,f_auto/v1730742969/FE7A9985_hwypv1.jpg",
          href: "https://res.cloudinary.com/ddhyr7ejn/image/upload/v1730742969/FE7A9985_hwypv1.jpg",
        },
        {
          src: "https://res.cloudinary.com/ddhyr7ejn/image/upload/w_1200,q_auto,f_auto/v1730742969/FE7A0019_cbglsd.jpg",
          href: "https://res.cloudinary.com/ddhyr7ejn/image/upload/v1730742969/FE7A0019_cbglsd.jpg",
        },
        {
          src: "https://res.cloudinary.com/ddhyr7ejn/image/upload/w_800,q_auto,f_auto/v1730742969/FE7A0584_qgkwhi.jpg",
          href: "https://res.cloudinary.com/ddhyr7ejn/image/upload/v1730742969/FE7A0584_qgkwhi.jpg",
        },
        {
          src: "https://res.cloudinary.com/ddhyr7ejn/image/upload/w_800,q_auto,f_auto/v1730742970/FE7A9986_fple7v.jpg",
          href: "https://res.cloudinary.com/ddhyr7ejn/image/upload/v1730742970/FE7A9986_fple7v.jpg",
        },
        {
          src: "https://res.cloudinary.com/ddhyr7ejn/image/upload/w_800,q_auto,f_auto/v1730742972/FE7A9993_dxnuj4.jpg",
          href: "https://res.cloudinary.com/ddhyr7ejn/image/upload/v1730742972/FE7A9993_dxnuj4.jpg",
        },
        {
          src: "https://res.cloudinary.com/ddhyr7ejn/image/upload/w_800,q_auto,f_auto/v1730742973/FE7A0047_lez3ug.jpg",
          href: "https://res.cloudinary.com/ddhyr7ejn/image/upload/v1730742973/FE7A0047_lez3ug.jpg",
        },
        {
          src: "https://res.cloudinary.com/ddhyr7ejn/image/upload/w_800,q_auto,f_auto/v1730742973/FE7A9946_ojffgf.jpg",
          href: "https://res.cloudinary.com/ddhyr7ejn/image/upload/v1730742973/FE7A9946_ojffgf.jpg",
        },
        {
          src: "https://res.cloudinary.com/ddhyr7ejn/image/upload/w_800,q_auto,f_auto/v1730742972/FE7A9989_x85qdc.jpg",
          href: "https://res.cloudinary.com/ddhyr7ejn/image/upload/v1730742972/FE7A9989_x85qdc.jpg",
        },
        {
          src: "https://res.cloudinary.com/ddhyr7ejn/image/upload/w_500,q_auto,f_auto/v1730742972/FE7A9996_owwhxb.jpg",
          href: "https://res.cloudinary.com/ddhyr7ejn/image/upload/v1730742972/FE7A9996_owwhxb.jpg",
        },
        {
          src: "https://res.cloudinary.com/ddhyr7ejn/image/upload/w_800,q_auto,f_auto/v1741602212/FE7A1326_zu2zu5.jpg",
          href: "https://res.cloudinary.com/ddhyr7ejn/image/upload/v1741602212/FE7A1326_zu2zu5.jpg",
        },
        {
          src: "https://res.cloudinary.com/ddhyr7ejn/image/upload/w_800,q_auto,f_auto/v1746896327/FE7A2310_ubhajn.jpg",
          href: "https://res.cloudinary.com/ddhyr7ejn/image/upload/v1746896327/FE7A2310_ubhajn.jpg",
        },
        {
          src: "https://res.cloudinary.com/ddhyr7ejn/image/upload/w_800,q_auto,f_auto/v1746896212/FE7A2306_iokji8.jpg",
          href: "https://res.cloudinary.com/ddhyr7ejn/image/upload/v1746896212/FE7A2306_iokji8.jpg",
        },
        {
          src: "https://res.cloudinary.com/ddhyr7ejn/image/upload/w_800,q_auto,f_auto/v1746896209/FE7A2301_gwjh3a.jpg",
          href: "https://res.cloudinary.com/ddhyr7ejn/image/upload/v1746896209/FE7A2301_gwjh3a.jpg",
        },
        {
          src: "https://res.cloudinary.com/ddhyr7ejn/image/upload/w_800,q_auto,f_auto/v1746896208/FE7A2294_t93hw6.jpg",
          href: "https://res.cloudinary.com/ddhyr7ejn/image/upload/v1746896208/FE7A2294_t93hw6.jpg",
        },
      ],
      totalPages: 2, // Số trang tổng cộng, có thể thay đổi
      links: ["/ktx", "/ktx2"],
    };
  },
  methods: {
    fetchImageDimensions(image) {
      return new Promise((resolve) => {
        const img = new Image();
        img.src = image.src;
        img.onload = () => {
          resolve({ width: img.width, height: img.height });
        };
      });
    },
    async updateImageDimensions() {
      const updatedImages = await Promise.all(
        this.images.map(async (image) => {
          const dimensions = await this.fetchImageDimensions(image);
          return { ...image, ...dimensions };
        })
      );
      this.images = updatedImages;
    },
  },
  mounted() {
    this.updateImageDimensions().then(() => {
      Fancybox.bind(this.$refs.container, "[data-fancybox]", {
        Carousel: {
          infinite: true,
        },
        Thumbs: {
          type: "classic",
          transition: "slide",
        },
        Toolbar: {
          display: {
            left: ["infobar"],
            right: [
              "slideshow",
              "thumbs",
              "zoomIn",
              "zoomOut",
              "fullscreen",
              "close",
            ],
          },
        },
        wheel: "zoom",
        defaultType: "ajax",
      });

      // Sử dụng Lozad để lazy load ảnh
      const observer = lozad(".lozad", {
        load: function (el) {
          el.src = el.dataset.src;
          el.onload = function () {
            el.classList.add("fade");
          };
        },
      });
      observer.observe();
    });
  },
  unmounted() {
    Fancybox.destroy();
  },
  activated() {
    console.log("Component activated");
  },
  deactivated() {
    console.log("Component deactivated");
  },
};
</script>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  background-color: var(--bg-color);
}

.container {
  padding-top: 50px !important;
  padding-bottom: 50px !important;
  width: 100%;
  margin: 0 auto;
  padding: 0px 90px;
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  grid-auto-rows: 250px;
  grid-auto-flow: dense;
  grid-gap: 20px;
}

#loader {
  position: fixed;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  z-index: 9999;
  background: #2c3e50 url("https://i.gifer.com/ZZ5H.gif") no-repeat center
    center;
  background-size: 10%;
}

#website {
  display: none;
}

.grid-item {
  background-color: var(--bg-color);
  overflow: hidden;
  position: relative;
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.19), 0 6px 6px rgba(0, 0, 0, 0.23);
}

.grid-item img {
  width: 110%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.4s ease;
  transform: translateX(-7%);
}

.grid-item:hover img {
  transform: translateX(0.1px);
}

.grid-item:nth-child(1) {
  grid-row: span 1;
  grid-column: span 2;
}

.grid-item:nth-child(2) {
  grid-column: span 3;
  grid-row: span 1;
}
.grid-item:nth-child(3) {
  grid-row: span 2;
  grid-row: span 1;
}
.grid-item:nth-child(4) {
  grid-row: span 2;
}

.grid-item:nth-child(5) {
  grid-row: span 2;
  grid-column: span 2;
}

.grid-item:nth-child(6) {
  grid-row: span 2;
  grid-column: span 2;
}

.grid-item:nth-child(7) {
  grid-row: span 2;
  grid-column: span 1;
}

.grid-item:nth-child(8) {
  grid-row: span 2;
  grid-column: span 2;
}

.grid-item:nth-child(11) {
  grid-row: span 1;
  grid-column: span 2;
}

.grid-item:nth-child(12) {
  grid-column: span 1;
}

.grid-item:nth-child(15) {
  grid-row: span 1;
  grid-column: span 1;
}
.grid-item:nth-child(16) {
  grid-column: span 2;
}

.grid-item:nth-child(17) {
  grid-row: span 2;
}

.grid-item:nth-child(19) {
  grid-column: span 2;
}

.grid-item:nth-child(20) {
  grid-column: span 3;
}

@keyframes fade {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}

.fade {
  animation-name: fade;
  animation-duration: 1s;
  display: block;
}

@media (max-width: 996px) {
  .grid-gallery {
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    grid-auto-rows: 280px;
  }
}

@media (max-width: 640px) {
  .grid-item:nth-child(1n) {
    grid-row: unset;
    grid-column: unset;
  }
}

@media (max-width: 576px) {
  .container {
    grid-template-columns: repeat(2, 1fr);
    grid-auto-rows: auto;
    padding: 0 15px;
  }

  .grid-item:nth-child(2) {
    grid-column: span 2;
    grid-row: span 1;
  }

  .grid-item:nth-child(6) {
    grid-column: span 2;
    grid-row: span 2;
  }
  .grid-item:nth-child(8) {
    grid-column: span 2;
    grid-row: span 2;
  }
  .grid-item:nth-child(10) {
    grid-column: span 1;
    grid-row: span 2;
  }
  .grid-item:nth-child(14) {
    grid-column: span 1;
    grid-row: span 2;
  }
  .grid-item:nth-child(15) {
    grid-column: span 1;
    grid-row: span 1;
  }
  .grid-item:nth-child(16) {
    grid-column: span 2;
  }
}
</style>
