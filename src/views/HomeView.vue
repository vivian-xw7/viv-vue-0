<!-- eslint-disable vue/no-parsing-error -->
<template>
  <div class="home">
    <div class="container px-20 pt-32 pb-20">
      <div class="row">
        <div
          class="col w-full lg:w-1/2 flex flex-col justify-center mb-12 lg:mb-0 text-center lg:text-left"
        >
          <div class="hero-banner__text-wrapper">
            <component
              :is="headingTag"
              v-if="
                pageContent.acf &&
                pageContent.acf.hero_banner_heading &&
                pageContent.acf.hero_banner_heading.text
              "
              class="hdg-5 mb-4"
            >
              {{ headingText }}
            </component>

            <component
              :is="subheadingTag"
              v-if="
                pageContent.acf &&
                pageContent.acf.hero_banner_subheading &&
                pageContent.acf.hero_banner_subheading.text
              "
              class="hdg-1"
            >
              {{ subheadingText }}
            </component>
          </div>
        </div>
        <div
          class="col w-full lg:w-1/2 flex flex-col justify-center items-center"
        >
          <div class="hero-banner__image-wrapper w-full md:w-3/5">
            <div class="hero-banner__image">
              <img :src="imageUrl" />
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// import axios from "axios";

// export default {
//   data() {
//     return {
//       pageContent: {},
//       imageUrl: "",
//       isMouseOver: false,
//     };
//   },
//   computed: {
//     headingTag() {
//       return this.pageContent.acf?.hero_banner_heading?.tag || "p";
//     },
//     headingText() {
//       return this.pageContent.acf?.hero_banner_heading?.text || "";
//     },
//     subheadingTag() {
//       return this.pageContent.acf?.hero_banner_subheading?.tag || "p";
//     },
//     subheadingText() {
//       return this.pageContent.acf?.hero_banner_subheading?.text || "";
//     },
//   },
//   methods: {
//     handleMouseEnter() {
//       this.isMouseOver = true;
//     },
//     handleMouseLeave() {
//       this.isMouseOver = false;
//     },
//   },
//   mounted() {
//     axios
//       .get("http://code-witch.local/wp-json/wp/v2/pages/11")
//       .then((response) => {
//         this.pageContent = response.data;

//         const imageId = this.pageContent.acf?.hero_banner_image || "";

//         if (imageId) {
//           axios
//             .get(`http://code-witch.local/wp-json/wp/v2/media/${imageId}`)
//             .then((imageResponse) => {
//               this.imageUrl = imageResponse.data?.source_url || "";
//             })
//             .catch((imageError) => {
//               console.error("Error fetching image:", imageError);
//             });
//         }
//       })
//       .catch((error) => {
//         console.error("Error fetching data:", error);
//       });
//   },
// };
</script>

<style scoped>
.hero-banner__image-wrapper {
  position: relative;

  &::before {
    content: "";
    display: block;
    padding-top: 115%;
  }

  .hero-banner__image {
    position: absolute;
    top: 0;
    left: 0;
    bottom: 0;
    right: 0;
    background-image: no-repeat;

    img {
      height: 100%;
      width: 100%;
      object-fit: cover;
    }
  }
}
</style>
