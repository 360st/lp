<script setup>
  // core version + navigation, pagination modules:
  import Swiper, { Navigation, Pagination } from 'swiper';
  // import Swiper and modules styles
  import 'swiper/css';
  import 'swiper/css/navigation';
  import 'swiper/css/pagination';

  // init Swiper:
  const swiper = new Swiper('.swiper', {
    // configure Swiper to use modules
    modules: [Navigation, Pagination],
   direction: 'vertical',
    loop: true,

    // If we need pagination
    pagination: {
      el: '.swiper-pagination',
    },

    // Navigation arrows
    navigation: {
      nextEl: '.swiper-button-next',
      prevEl: '.swiper-button-prev',
    },

    // And if we need scrollbar
    scrollbar: {
      el: '.swiper-scrollbar',
    },
  });
  let data = ref(null)

  try {
      const request = await fetch('/api/list.json')
      data.value = await request.json();
      console.log(data.value)
  } catch(err) {
      console.log(err);
  }

</script>
<template>
    <div id="app" class="container px-8 max-w-[1170px] mx-auto lg:px-0">
      <header class="  flex flex-col h-[140px] border border-black w-full justify-center items-center mb-8">
          <h1>
            container width: 1170px
          </h1>
          <h2>
            gutter: 30px
          </h2>
      </header>
      <main>
        <div class=" space-y-4 mb-8 lg:space-y-0 lg:grid lg:grid-cols-12 lg:gap-8">
          <div class=" h-[200px] lg:col-span-3 border border-black flex justify-center items-center">
            <p>1</p>
          </div>
          <div class=" h-[200px] lg:col-span-6 border border-black flex justify-center items-center">
            <p>2</p>
          </div>
          <div class=" h-[200px] lg:col-span-3 border border-black flex justify-center items-center">
            <p>3</p>
          </div>
        </div>
        <div class="space-y-4 mb-8 lg:space-y-0 lg:grid lg:grid-cols-8 lg:gap-8">
          <div class=" h-[200px] lg:col-span-3 border border-black flex justify-center items-center">
            <p>4</p>
          </div>
          <div class=" h-[200px] lg:col-span-3 border border-black flex justify-center items-center">
            <p>5</p>
          </div>
          <div class=" h-[200px] lg:col-span-2 border border-black flex justify-center items-center">
            <p>7</p>
          </div>
        </div>   
        <div class=" grid lg:grid-cols-2 gap-8 ">
          <div class=" grid grid-cols-6 gap-8 border border-black h-[577px]">
            <div class=" col-span-2 h-[160px] flex justify-center items-center bg-yellow-500">
              1
            </div>
            <div class=" col-span-2 h-[160px] order-3 flex justify-center items-center bg-yellow-500">
              2
            </div>
            <div class=" col-span-3 h-[280px] order-4 flex justify-center items-center self-end bg-yellow-500">
              3
            </div>
            <div class=" col-span-2 h-[160px] order-2 flex justify-center items-center bg-yellow-500">
              4
            </div>
          </div> 
          <div class=" grid items-start border border-black h-[577px]">
            <div class=" text-center w-full py-12 bg-yellow-500">
              1
            </div>
            <div class=" text-center  py-12 bg-yellow-500">
              2
            </div>
          </div> 
        </div>
        
        <div>
            <div class="swiper h-[300px] w-full">
              <!-- Additional required wrapper -->
              <div class="swiper-wrapper">
                <!-- Slides -->
                <div v-for="loop in data" :key="loop.id">
                    <div class="swiper-slide">{{loop.name}}</div>
                </div>
          
              </div>
              <!-- If we need pagination -->
              <div class="swiper-pagination"></div>

              <!-- If we need navigation buttons -->
              <div class="swiper-button-prev"></div>
              <div class="swiper-button-next"></div>

              <!-- If we need scrollbar -->
              <div class="swiper-scrollbar"></div>
            </div>
        </div>
    
      </main>
    </div>
</template>