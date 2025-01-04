<template>
  <div>
    <h2>ÇOK SATANLAR</h2>
    
    <!-- Kaydırılabilir Alan -->
    <div class="slider-container">
      <!-- Kaydırma Butonları -->
      <div class="slider-buttons left" @click="scrollLeft"> < </div>
      <div class="slider-buttons right" @click="scrollRight"> > </div>
      
      <!-- Kartlar Dinamik Olarak Yüklenecek -->
      <div class="cards-container" ref="cardsContainer">
        <div v-for="(card, index) in visibleCards" :key="index" class="card">
          <img :src="card.img" class="card-img-top" alt="Example Image">
          <div class="card-body">
            <div class="stars">
              <span class="star">&#9733;</span>
              <span class="star">&#9733;</span>
              <span class="star">&#9733;</span>
              <span class="star">&#9733;</span>
              <span class="star">&#9733;</span>
            </div>
            <p class="name">{{ card.name }}</p>
            <p class="card-text">
              {{ card.publisher }}<br>{{ card.author }}
            </p>
            <a href="#" class="btn btn-primary" :data-price="card.price">{{ card.price }}</a>

            
          </div>
        </div>
      </div>
    </div>

    <!-- Navigasyon Yuvarlakları -->
    <div class="navigation-dots">
      <span v-for="(dot, index) in totalPages" :key="index" 
            :class="['dot', { active: currentIndex === index }]" 
            @click="goToPage(index)">
      </span>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      cards: [
    { img: '/icons/bulbul-kapani-1-hediyeli-ozel-kutu-920473-49-K 1.jpg', name: 'Bülbül Kapanı 1', publisher: 'Ephesus Yayınları', author: 'Loresima',price:'249.99TL'},
    { img: '/icons/menu4_files/yasamak-139530-171631-13-O.jpg', name: 'Yaşamak', publisher: 'Jaogur Kitap', author: 'Yu Hua',price:'99.99TL' },
    { img: '/icons/3.jpg', name: 'Efsaneler ve Lanetler ', publisher: 'Ephesus Yayınları', author: 'Loresima',price:'249.99TL' },
    { img: '/icons/4.png', name: 'Şehadet Vatan İçin', publisher: 'İthaki Yayınları', author: 'Loresima',price:'50TL' },
    { img: '/icons/5.jpg', name: 'Siyam', publisher: 'Ephesus Yayınları', author: 'Loresima',price:'150TL' },
    { img: '/icons/6.png', name: 'Medusa Ve Ölü Kumları', publisher: 'Can Yayınları', author: 'MARAL ATMACA',price:'150TL' },
    { img: '/icons/7.png', name: 'İmpratorluk Kılıcı', publisher: 'Ephesus Yayınları', author: 'Loresima',price:'50TL' },
    { img: '/icons/8.png', name: 'Yırtıcı Kuşar Zamanı', publisher: 'Ephesus Yayınları', author: 'AHMET ÜMİT',price:'150TL' },
    { img: '/icons/9.png', name: 'Oyunbaz', publisher: 'Ephesus Yayınları', author: 'Loresima' ,price:'50TL'},
    { img: '/public/icons/10.jpg', name: 'Beyaz leke', publisher: 'Ephesus Yayınları', author: 'Loresima' ,price:'150TL'},
    { img: '/icons/11.png', name: 'Bir Kibritle Yok olmak ', publisher: 'Ephesus Yayınları', author: 'Loresima',price:'99.99TL' },
    { img: '/icons/12.jpg', name: 'Biliçaltının gücü ', publisher: 'Ephesus Yayınları', author: 'Loresima' ,price:'150TL'},
    { img: '/icons/13.jpg', name: 'Rezonans kanunu ', publisher: 'Ephesus Yayınları', author: 'Loresima' ,price:'350TL'},
    { img: '/icons/14..jpg', name: 'Cumhuriyet\'in ilk sabahı ', publisher: 'Ephesus Yayınları', author: 'Loresima',price:'150TL' },
    { img: '/icons/14.png', name: 'Dikkat zengin yapabilir', publisher: 'Ephesus Yayınları', author: 'Loresima',price:'158TL' },
    { img: '/icons/15.jpg', name: 'İnsanlığımı yitirirken', publisher: 'Ephesus Yayınları', author: 'VICTOR HUGO',price:'20TL' },
    { img: '/icons/16.jpg', name: 'Bir idam mahkumunun son günü', publisher: 'Ephesus Yayınları', author: 'VICTOR HUGO',price:'99.99TL' },
    { img: '/icons/17.jpg', name: 'Martın eden', publisher: 'Ephesus Yayınları', author: 'Loresima',price:'99.99TL' },
    { img: '/icons/18.png', name: 'Gece Yarısı Kütüphanesi', publisher: 'Ephesus Yayınları', author: 'Loresima' ,price:'79.99TL'},
    { img: '/icons/19.png', name: 'intermezzo', publisher: 'Ephesus Yayınları', author: 'Loresima' ,price:'99.99TL'},
    { img: '/icons/20.jpg', name: 'insanlar', publisher: 'Ephesus Yayınları', author: 'Loresima' ,price:'79.99TL'},
    { img: '/icons/ihtilal-2-922514-49- 2.png', name: 'ölmek', publisher: 'Ephesus Yayınları', author: 'Loresima' ,price:'99.99TL'}
],

      currentIndex: 0, // Başlangıçta görünen kartlar
    };
  },
  computed: {
    // Görünen 6 kart
    visibleCards() {
      return this.cards.slice(this.currentIndex, this.currentIndex + 6);
    },
    totalPages() {
      return Math.ceil(this.cards.length / 6); // Toplam sayfa sayısını hesaplar
    }
  },
  methods: {
    // Sola kaydırma
    scrollLeft() {
      if (this.currentIndex > 0) {
        this.currentIndex -= 1; // 1 kart geri kaydır
      }
    },
    // Sağa kaydırma
    scrollRight() {
      if (this.currentIndex + 1 < this.cards.length) {
        this.currentIndex += 1; // 1 kart ileri kaydır
      }
    }
  },
};
</script>


<style scoped>
.cards-container {
  display: flex;
  overflow-x: auto; /* Yalnızca yatay kaydırma */
  gap: 5px; /* Kartlar arasındaki mesafe */
  justify-content: center; /* Kartları yatayda ortala */
  padding-left: 5px; /* Sol boşluk ekle */
  padding-right: 5px; /* Sağ boşluk ekle */
}

.card {
  width: 100%; /* Kart genişliği */
  max-width: 160px; /* Maksimum genişlik */
  min-width: 120px; /* Minimum genişlik */
  margin: 10px 5px; /* Kartlar arasındaki boşluğu daha da küçült */
  border: 1px solid #ddd; /* Hafif sınır */
  border-radius: 5px; /* Yuvarlatılmış köşeler */
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1); /* Gölge */
  display: flex;
  flex-direction: column; /* İçeriği dikey hizala */
  height: 440px; /* Kartın sabit yüksekliği */
  overflow: hidden; /* Taşmaları engeller */
  border-radius: 0; 
}

.card-img-top {
  width: 100%; /* Resmi kart genişliğine göre ayarla */
  height: 200px; /* Sabit resim yüksekliği */
  object-fit: cover; /* Resmi düzgün ölçeklendir */
  border-top-left-radius: 5px;
  border-top-right-radius: 5px;
}

.card-body {
  padding: 10px; /* Kart içeriği için boşluk */
  display: flex;
  flex-direction: column; /* Dikey hizalama */
  justify-content: flex-start; /* İçeriği başta hizalar */
  flex-grow: 1; /* İçeriğin kartı doldurmasını sağlar */
  padding-bottom: 40px;
}

.card-title {
  font-size: 14px; /* Yazı boyutunu küçült */
  margin-bottom: 10px; /* Başlık ile içerik arasında boşluk */
}

.card-text {
  font-size: 12px; /* Yazı boyutunu küçült */
  margin-bottom: 10px; /* Metin ile yıldızlar arasında boşluk */
}

.stars {
  display: flex;
  justify-content: center; /* Yıldızları ortala */
  margin: 5px 0; /* Yıldız ve diğer içerikler arasında boşluk */
}

.star {
  font-size: 18px; /* Yıldız boyutunu küçült */
  color: rgb(196, 193, 181); /* Yıldız rengi */
  margin: 0 2px; /* Yıldızlar arasında boşluk */
}

.name {
  text-align: center; /* Yazıyı ortala */
  font-weight: bold; /* Yazıyı kalın yap */
  color: #555; /* Gri yazı rengi */
  margin-top: 5px; /* Yıldızların altına boşluk bırak */
  font-size: 13px; /* Yazı boyutunu küçült */
}

/* Buton stili */
.btn {
  width: 100%; /* Buton genişliği */
  height: 45px;
  margin-top: auto; /* Butonu en alta it */
  text-align: center;
  padding: 1px; /* Buton içindeki boşluğu küçült */
  padding-top: 2px;
  padding-bottom: 2px;
  font-size: 14px; /* Buton yazı boyutunu küçült */
  margin-bottom: 1px; /* Butonun altındaki boşluğu küçült */
  background-color: rgb(120, 75, 162); /* Mor arka plan rengi */
  color: transparent; /* Başlangıçta yazı rengi görünmez yapar */
  border-radius: 5px; /* Köşeleri yuvarlar */
  border: none; /* Buton sınırlarını kaldırır */
  transition: all 0.3s ease; /* Geçiş efekti */
}

/* Başlangıçta fiyat görünür */
.btn::before {
  content: attr(data-price);  /* Fiyatı başlangıçta gösterir */
  display: block; /* Fiyatı block yaparak gösterir */
  color: white; /* Fiyat rengi beyaz */
  font-size: 16px;
  font-weight: bold;
}

/* Hover (üzerine gelindiğinde) durumu */
.btn:hover {
  background-color: rgb(120, 75, 162); /* Üzerine gelindiğinde renk mor kalacak */
  color: white; /* Yazı beyaz olacak */
}

/* Hover durumunda sadece "Sepete Ekle" yazısı gösterilecek, fiyat gizlenir */
.btn:hover::before {
  content: "SEPETE EKLE"; /* Fiyatın yerine Sepete Ekle yazısı gelir */
  font-size: 14px;
  color: white; /* Sepete Ekle yazısı beyaz olacak */
  font-weight: normal; /* Yazı kalınlığı normal olacak */
}
/* Hover üzerinde sadece "Sepete Ekle" yazısını gösterir */
.btn:hover::after {
  content: "Sepete Ekle"; /* Üzerine gelindiğinde yazıyı ekler */
  display: block; /* Yazıyı göstermek için block yapar */
  color: white; /* Sepete Ekle yazısını beyaz yapar */
}
/* Başlangıçta yalnızca fiyatı gösterir */
.btn::after {
  content: "249,99TL"; /* Başlangıçta fiyat görünür */
  display: block; /* Fiyatı block yaparak gösterir */
  color: white; /* Fiyat rengi beyaz */
}
.card-text {
  color: rgb(116, 82, 185); /* Metin rengini mor yapar */
}
.slider-container {
  position: relative; /* İçerik için referans konumlandırma */
  display: flex;
  justify-content: center; /* Kartları ortalar */
}

.cards-container {
  display: flex;
  overflow-x: auto; /* Yalnızca yatay kaydırma */
  gap: 10px; /* Kartlar arasındaki mesafe */
  justify-content: center; /* Kartları merkezde hizalar */
  padding: 0 50px; /* Kartların etrafına sağ ve sol boşluk ekleriz */
  max-width: 100%; /* Container'ın genişliğini sınırlıyoruz */
}

.navigation-dots {
  display: flex;
  justify-content: center;
  margin-top: 10px;
}

.dot {
  width: 10px;
  height: 10px;
  border-radius: 50%;
  background-color: gray;
  margin: 0 5px;
  cursor: pointer;
}

.dot.active {
  background-color: rgb(214, 128, 48);
}

.slider-buttons {
  position: absolute;
  top: 40%; /* Dikeyde ortalar */
  background-color: rgba(241, 231, 231, 0.5); /* Butonların arka planı */
  color: rgb(172, 165, 165);
  font-size: 24px;
  padding: 15px; /* Butonun içine boşluk ekler */
  border-radius: 50%; /* Tam yuvarlak yapar */
  cursor: pointer;
  z-index: 2; /* Kartların önünde olacak */
  transition: background-color 0.3s ease;
  width: 20px;  /* Butonun genişliği */
  height: 20px; /* Butonun yüksekliği */
  display: flex;
  justify-content: center;
  align-items: center; /* Ok işaretini ortalar */
}




/* Sol buton - ilk kartın hemen solunda */
.slider-buttons.left {
  left: calc(50% - 510px); /* Kartların ortasına ve ilk karta yakın olacak */
  transform: translateY(-50%); /* Dikeyde tam ortada hizalar */
}

/* Sağ buton - son kartın hemen sağında */
.slider-buttons.right {
  right: calc(50% - 513px); /* Kartların ortasına ve son karta yakın olacak */
  transform: translateY(-50%); /* Dikeyde tam ortada hizalar */
}
.card-img-top {
  width: 100%; /* Resmi kart genişliğine göre ayarla */
  height: 200px; /* Sabit resim yüksekliği */
  object-fit: cover; /* Resmi düzgün ölçeklendir */
  border-top-left-radius: 5px;
  border-top-right-radius: 5px;
  transition: transform 0.3s ease; /* Yumuşak geçiş efekti */
}

.card-img-top:hover {
  transform: scale(1.1); /* Hover durumunda resmi %10 büyüt */
}
h2{
  color: #892c93;
  text-align: center;
}

</style>