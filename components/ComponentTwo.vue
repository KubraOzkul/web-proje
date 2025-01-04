<template>
  <div class="container">
    <!-- First Row with 3 Images -->
    <div class="row">
      <div class="col-12 col-sm-12 col-md-12 col-lg-4 col-xl-4 mb-2 d-flex" v-for="(item, index) in items" :key="index">
        <nuxt-link :to="item.link" class="w-100 d-block border-round position-relative effect-wrapper" :aria-label="item.ariaLabel">
          <picture class="w-100 h-100 d-flex overflow-hidden">
            <source :media="item.mediaQuery" :srcset="item.srcset" width="354.8" height="192.74">
            <img :src="item.imgSrc" :data-src="item.imgSrc" class="w-100 fit-cover hover-scale ls-is-cached lazyloaded" loading="lazy" width="354.8" height="192.74" :alt="item.altText">
          </picture>
        </nuxt-link>
      </div>
    </div>

    <!-- Second Row with a Full-Width Image -->
    <div class="row">
      <div class="col-12 mb-2">
        <picture class="w-100 h-100 d-flex overflow-hidden effect-wrapper">
          <img src="https://www.kitapsepeti.com/Data/BlockUploadData/banner/img1/328/cocuk-kitaplari-1-tr-tr-1.jpg?1732712208"
               data-src="https://www.kitapsepeti.com/Data/BlockUploadData/banner/img1/328/cocuk-kitaplari-1-tr-tr-1.jpg?1732712208"
               class="w-100 fit-cover hover-scale lazyloaded"
               loading="lazy"
               width="1124.4"
               height="241.21"
               alt="Çocuk Kitapları">
        </picture>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      // Data for the first 3 images
      items: [
        {
          link: 'https://www.kitapsepeti.com/cok-satan-kitaplar',
          ariaLabel: 'Çok Satan Kitaplar',
          mediaQuery: '(min-width:576px)',
          srcset: 'https://www.kitapsepeti.com/Data/BlockUploadData/banner/img1/327/cok-satan-kitaplar-1-tr-tr-1.jpg?1732712208',
          imgSrc: 'https://www.kitapsepeti.com/Data/BlockUploadData/banner/img2/327/cok-satan-kitaplar-1-tr-tr-1.jpg?1732712208',
          altText: 'Çok Satan Kitaplar'
        },
        {
          link: 'https://www.kitapsepeti.com/yeni-cikan-kitaplar',
          ariaLabel: 'Yeni Çıkan Kitaplar',
          mediaQuery: '(min-width:576px)',
          srcset: 'https://www.kitapsepeti.com/Data/BlockUploadData/banner/img1/327/yeni-cikan-kitaplar-2-tr-tr-2.jpg?1732712208',
          imgSrc: 'https://www.kitapsepeti.com/Data/BlockUploadData/banner/img2/327/yeni-cikan-kitaplar-2-tr-tr-2.jpg?1732712208',
          altText: 'Yeni Çıkan Kitaplar'
        },
        {
          link: 'https://www.kitapsepeti.com/sinavlara-hazirlik-kitaplari',
          ariaLabel: 'Sınavlara Hazırlık Kitapları',
          mediaQuery: '(min-width:576px)',
          srcset: 'https://www.kitapsepeti.com/Data/BlockUploadData/banner/img1/327/sinavlara-hazirlik-kitaplari-3-tr-tr-3.jpg?1732712208',
          imgSrc: 'https://www.kitapsepeti.com/Data/BlockUploadData/banner/img2/327/sinavlara-hazirlik-kitaplari-3-tr-tr-3.jpg?1732712208',
          altText: 'Sınavlara Hazırlık Kitapları'
        }
      ]
    };
  }
};
</script>

<style scoped>
.container {
  margin-top: 20px;
}

.effect-wrapper {
  position: relative;
  overflow: hidden;
}

.effect-wrapper img {
  transition: transform 0.3s ease, opacity 0.3s ease;
}

.effect-wrapper:hover img {
  transform: scale(1.05); /* Enlarge image on hover */
  opacity: 0.9; /* Slightly fade the image */
}

@media (max-width: 576px) {
  .effect-wrapper img {
    transform: scale(1); /* Enlarge effect on mobile */
  }
}

.picture img {
  transition: transform 0.3s ease, opacity 0.3s ease;
}

.picture:hover img {
  transform: scale(1.05);
  opacity: 0.9;
}
</style>


  