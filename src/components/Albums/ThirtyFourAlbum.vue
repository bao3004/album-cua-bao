<template id="web">
  <HeaderComp />
  <Description1Comp v-bind:content="popupContent" />
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

import HeaderComp from "../Headers/Header7Comp.vue";
import FooterComp from "../FooterComp.vue";
import PaginationComp from "../PaginationComp.vue";
import Description1Comp from "../Description/Description1Comp.vue";

export default {
  name: "GalleryComponent",
  components: {
    HeaderComp,
    FooterComp,
    PaginationComp,
    Description1Comp,
  },
  data() {
    return {
      popupContent:
        "<br><b>&#10149; Name:</b> 30 - 4<br><b>&#10149; Combo:</b> Canon 5d3 + Tamron 70 - 300<br><b>&#10149; Time:</b> 27-04-2025<br><br> 50 năm mới có 1 lần, bỏ lỡ thì tiếc lắm. Mãi ❤️ VN",
      images: [
        {
          src: "https://res.cloudinary.com/ddhyr7ejn/image/upload/w_800,q_auto,f_auto/v1746732012/FE7A2162_ewzmpe.jpg",
          href: "https://res.cloudinary.com/ddhyr7ejn/image/upload/v1746732012/FE7A2162_ewzmpe.jpg",
        },
        {
          src: "https://res.cloudinary.com/ddhyr7ejn/image/upload/w_800,q_auto,f_auto/v1746732011/FE7A2167_wwxqio.jpg",
          href: "https://res.cloudinary.com/ddhyr7ejn/image/upload/v1746732011/FE7A2167_wwxqio.jpg",
        },
        {
          src: "https://res.cloudinary.com/ddhyr7ejn/image/upload/w_800,q_auto,f_auto/v1746731741/FE7A2262_ioxnoj.jpg",
          href: "https://res.cloudinary.com/ddhyr7ejn/image/upload/v1746731741/FE7A2262_ioxnoj.jpg",
        },
        {
          src: "https://res.cloudinary.com/ddhyr7ejn/image/upload/w_800,q_auto,f_auto/v1746731740/FE7A2259_u2obxx.jpg",
          href: "https://res.cloudinary.com/ddhyr7ejn/image/upload/v1746731740/FE7A2259_u2obxx.jpg",
        },
        {
          src: "https://res.cloudinary.com/ddhyr7ejn/image/upload/w_800,q_auto,f_auto/v1746731738/FE7A2233_ddkm2p.jpg",
          href: "https://res.cloudinary.com/ddhyr7ejn/image/upload/v1746731738/FE7A2233_ddkm2p.jpg",
        },
        {
          src: "https://res.cloudinary.com/ddhyr7ejn/image/upload/w_800,q_auto,f_auto/v1746731738/FE7A2238_yfts7l.jpg",
          href: "https://res.cloudinary.com/ddhyr7ejn/image/upload/v1746731738/FE7A2238_yfts7l.jpg",
        },
        {
          src: "https://res.cloudinary.com/ddhyr7ejn/image/upload/w_800,q_auto,f_auto/v1746731737/FE7A2217_fc9dcs.jpg",
          href: "https://res.cloudinary.com/ddhyr7ejn/image/upload/v1746731737/FE7A2217_fc9dcs.jpg",
        },
        {
          src: "https://res.cloudinary.com/ddhyr7ejn/image/upload/w_800,q_auto,f_auto/v1746731737/FE7A2231_xqhqmy.jpg",
          href: "https://res.cloudinary.com/ddhyr7ejn/image/upload/v1746731737/FE7A2231_xqhqmy.jpg",
        },
        {
          src: "https://res.cloudinary.com/ddhyr7ejn/image/upload/w_800,q_auto,f_auto/v1746731736/FE7A2216_cz9yba.jpg",
          href: "https://res.cloudinary.com/ddhyr7ejn/image/upload/v1746731736/FE7A2216_cz9yba.jpg",
        },
        {
          src: "https://res.cloudinary.com/ddhyr7ejn/image/upload/w_800,q_auto,f_auto/v1746731736/FE7A2207_yd03pn.jpg",
          href: "https://res.cloudinary.com/ddhyr7ejn/image/upload/v1746731736/FE7A2207_yd03pn.jpg",
        },
        {
          src: "https://res.cloudinary.com/ddhyr7ejn/image/upload/w_800,q_auto,f_auto/v1746731735/FE7A2214_el8nav.jpg",
          href: "https://res.cloudinary.com/ddhyr7ejn/image/upload/v1746731735/FE7A2214_el8nav.jpg",
        },
        {
          src: "https://res.cloudinary.com/ddhyr7ejn/image/upload/w_800,q_auto,f_auto/v1746731724/FE7A2043_orxr7x.jpg",
          href: "https://res.cloudinary.com/ddhyr7ejn/image/upload/v1746731724/FE7A2043_orxr7x.jpg",
        },
        {
          src: "https://res.cloudinary.com/ddhyr7ejn/image/upload/w_800,q_auto,f_auto/v1746731733/FE7A2179_dzwrwx.jpg",
          href: "https://res.cloudinary.com/ddhyr7ejn/image/upload/v1746731733/FE7A2179_dzwrwx.jpg",
        },
        {
          src: "https://res.cloudinary.com/ddhyr7ejn/image/upload/w_800,q_auto,f_auto/v1746731731/FE7A2197_n5mftq.jpg",
          href: "https://res.cloudinary.com/ddhyr7ejn/image/upload/v1746731731/FE7A2197_n5mftq.jpg",
        },
        {
          src: "https://res.cloudinary.com/ddhyr7ejn/image/upload/w_800,q_auto,f_auto/v1746731732/FE7A2198_rokf6i.jpg",
          href: "https://res.cloudinary.com/ddhyr7ejn/image/upload/v1746731732/FE7A2198_rokf6i.jpg",
        },
        {
          src: "https://res.cloudinary.com/ddhyr7ejn/image/upload/w_800,q_auto,f_auto/v1746731732/FE7A2199_qoepel.jpg",
          href: "https://res.cloudinary.com/ddhyr7ejn/image/upload/v1746731732/FE7A2199_qoepel.jpg",
        },
        {
          src: "https://res.cloudinary.com/ddhyr7ejn/image/upload/w_800,q_auto,f_auto/v1746731733/FE7A2201_hzzly9.jpg",
          href: "https://res.cloudinary.com/ddhyr7ejn/image/upload/v1746731733/FE7A2201_hzzly9.jpg",
        },
        {
          src: "https://res.cloudinary.com/ddhyr7ejn/image/upload/w_800,q_auto,f_auto/v1746731729/FE7A2193_toi3hp.jpg",
          href: "https://res.cloudinary.com/ddhyr7ejn/image/upload/v1746731729/FE7A2193_toi3hp.jpg",
        },
        {
          src: "https://res.cloudinary.com/ddhyr7ejn/image/upload/w_800,q_auto,f_auto/v1746731728/FE7A2145_teegw6.jpg",
          href: "https://res.cloudinary.com/ddhyr7ejn/image/upload/v1746731728/FE7A2145_teegw6.jpg",
        },
        {
          src: "https://res.cloudinary.com/ddhyr7ejn/image/upload/w_800,q_auto,f_auto/v1746731727/FE7A2148_mdtwk4.jpg",
          href: "https://res.cloudinary.com/ddhyr7ejn/image/upload/v1746731727/FE7A2148_mdtwk4.jpg",
        },
        {
          src: "https://res.cloudinary.com/ddhyr7ejn/image/upload/w_800,q_auto,f_auto/v1746731727/FE7A2136_rijivf.jpg",
          href: "https://res.cloudinary.com/ddhyr7ejn/image/upload/v1746731727/FE7A2136_rijivf.jpg",
        },
        {
          src: "https://res.cloudinary.com/ddhyr7ejn/image/upload/w_800,q_auto,f_auto/v1746731727/FE7A2096_lsznxy.jpg",
          href: "https://res.cloudinary.com/ddhyr7ejn/image/upload/v1746731727/FE7A2096_lsznxy.jpg",
        },
        {
          src: "https://res.cloudinary.com/ddhyr7ejn/image/upload/w_800,q_auto,f_auto/v1746731727/FE7A2130_odph72.jpg",
          href: "https://res.cloudinary.com/ddhyr7ejn/image/upload/v1746731727/FE7A2130_odph72.jpg",
        },
        {
          src: "https://res.cloudinary.com/ddhyr7ejn/image/upload/w_800,q_auto,f_auto/v1746731725/FE7A2091_dj1rnd.jpg",
          href: "https://res.cloudinary.com/ddhyr7ejn/image/upload/v1746731725/FE7A2091_dj1rnd.jpg",
        },
        {
          src: "https://res.cloudinary.com/ddhyr7ejn/image/upload/w_800,q_auto,f_auto/v1746731725/FE7A2085_cmt6dy.jpg",
          href: "https://res.cloudinary.com/ddhyr7ejn/image/upload/v1746731725/FE7A2085_cmt6dy.jpg",
        },
        {
          src: "https://res.cloudinary.com/ddhyr7ejn/image/upload/w_800,q_auto,f_auto/v1746731725/FE7A2068_q3p9lg.jpg",
          href: "https://res.cloudinary.com/ddhyr7ejn/image/upload/v1746731725/FE7A2068_q3p9lg.jpg",
        },
        {
          src: "https://res.cloudinary.com/ddhyr7ejn/image/upload/w_800,q_auto,f_auto/v1746731724/FE7A2062_ikitey.jpg",
          href: "https://res.cloudinary.com/ddhyr7ejn/image/upload/v1746731724/FE7A2062_ikitey.jpg",
        },
        {
          src: "https://res.cloudinary.com/ddhyr7ejn/image/upload/w_800,q_auto,f_auto/v1746731723/FE7A2060_jqelzc.jpg",
          href: "https://res.cloudinary.com/ddhyr7ejn/image/upload/v1746731723/FE7A2060_jqelzc.jpg",
        },
        {
          src: "https://res.cloudinary.com/ddhyr7ejn/image/upload/w_800,q_auto,f_auto/v1746731723/FE7A2109_usqphg.jpg",
          href: "https://res.cloudinary.com/ddhyr7ejn/image/upload/v1746731723/FE7A2109_usqphg.jpg",
        },
        {
          src: "https://res.cloudinary.com/ddhyr7ejn/image/upload/w_800,q_auto,f_auto/v1746731723/FE7A2103_jq1umr.jpg",
          href: "https://res.cloudinary.com/ddhyr7ejn/image/upload/v1746731723/FE7A2103_jq1umr.jpg",
        },
      ],
      totalPages: 1,
      links: ["/304"],
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
  transform: translateX(-5%);
}

.grid-item:hover img {
  transform: translateX(0);
}

.grid-item:nth-child(3) {
  grid-row: span 2;
}

.grid-item:nth-child(6) {
  grid-row: span 2;
  grid-column: span 2;
}

.grid-item:nth-child(7) {
  grid-row: span 2;
  grid-column: span 1;
}

.grid-item:nth-child(12) {
  grid-column: span 2;
  grid-row: span 3;
}

.grid-item:nth-child(15) {
  grid-column: span 3;
}

.grid-item:nth-child(17) {
  grid-row: span 2;
}

.grid-item:nth-child(19) {
  grid-column: span 2;
}

.grid-item:nth-child(20) {
  grid-column: span 2;
}

.grid-item:nth-child(26),
.grid-item:nth-child(27),
.grid-item:nth-child(28) {
  grid-row: span 2;
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

@media (max-width: 500px) {
  .container {
    grid-template-columns: repeat(2, 1fr);
    grid-auto-rows: auto;
    padding: 0 15px;
  }

  .grid-item:nth-child(6) {
    grid-column: span 2;
    grid-row: span 2;
  }

  .grid-item:nth-child(15) {
    grid-column: span 2;
    grid-row: span 1;
  }

  .grid-item:nth-child(17) {
    grid-column: span 1;
    grid-row: span 2;
  }
  .grid-item:nth-child(19) {
    grid-column: span 2;
    grid-row: span 1;
  }
  .grid-item:nth-child(20) {
    grid-column: span 1;
  }
}
</style>
