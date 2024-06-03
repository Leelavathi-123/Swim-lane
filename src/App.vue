<template>
<div class="main-div"><h1>Most-watched films</h1></div>
  <swiper
    :cssMode="true"
    :slidesPerView="6.5"
    :spaceBetween="20"
    :navigation="true"
    :pagination="{
      clickable: true,
    }"
    :mousewheel="true"
    :keyboard="true"
    :loop="true"
    :history="{
      key: 'slide',
    }"
  :breakpoints="{
  '320': {
    slidesPerView: 1,
  },
  '488': {
    slidesPerView: 2 ,
  },
  '768': {
    slidesPerView: 3,  
    spaceBetween:10,  
  },
  '1200':{
    slidesPerView: 6.5, 
    spaceBetween:20, 
  }
  }"
    :modules="modules"
    class="mySwiper"
  >
     <swiper-slide
      v-for="(movie, index) in movies"
      :key="index"
      :data-history="movie.history"
    >
      <div class="slide-content">
        <img v-bind:src="movie.img" />
        <div v-if="movie.new" class="new-button">New</div>
        <h1>{{ movie.title }}</h1>
      </div>
    </swiper-slide>
  </swiper>
</template>
<script>

  import { Swiper, SwiperSlide } from 'swiper/vue';
  import 'swiper/css';
  import 'swiper/css/navigation';
  import 'swiper/css/pagination';

  import './style.css';
  import { Navigation, Pagination, History, Mousewheel, Keyboard } from 'swiper/modules';

  export default (await import('vue')).defineComponent({
    components: {
      Swiper,
      SwiperSlide,
    },
    setup() {
      const movies = [
        { history: 1, img:('../src/assets/i1.png'), title: 'Oppenheimer' },
        { history: 2, img: '../src/assets/i2.png', title: 'Past Lives' },
        { history: 3, img: '../src/assets/i3.png', title: 'Polite Society' },
        { history: 4, img: '../src/assets/i4.png', title: 'Robots' },
        { history: 5, img: '../src/assets/i5.png', title: 'Sanctuary' },
        { history: 6, img: '../src/assets/i6.png', title: 'Talk To Me' },
        { history: 7, img: '../src/assets/i7.png', title: 'About My Father', new: true },
        { history: 8, img: '../src/assets/i8.png', title: 'Air' },
        { history: 9, img: '../src/assets/i9.png', title: 'Are You There God? It’s Me, Margaret.', new: true },
        { history: 10, img: '../src/assets/i10.png', title: 'Guardians of the Galaxy: Volume 3' },
        { history: 11, img: '../src/assets/i11.png', title: 'Big George Foreman' },
        { history: 12, img: '../src/assets/i12.png', title: 'Beau Is Afraid' },
      ];

      return {
        movies,
        modules: [Navigation, Pagination, History, Mousewheel, Keyboard],
      };
    },
  });
</script>

