<template>
    <Swiper :space-between="20" :loop="true" :modules="[SwiperAutoplay, SwiperPagination]" :autoplay="{delay: 3500}" :pagination="{clickable: true}" :slidesPerView="1" class="w-full col-span-full h-2/3 md:h-1/2">
        <SwiperSlide class="relative">
            <img src="/images/hero/1.webp" alt="" class="object-cover aspect-video">
            <div class="absolute inset-0 bg-black/30"></div>
            <div class="absolute inset-0 px-4 flex justify-center items-center text-white">
                <div class="flex flex-col relative gap-6 w-full md:w-1/2 lg:w-1/3 p-4 lg:p-6 rounded-2xl overflow-hidden">
                    <div class="absolute inset-0 backdrop-blur-sm"></div>
                    <p class="text-2xl font-Comfortaa z-[1]">Очарование природы</p>
                    <p class="opacity-80 text-lg">Приветствуют вас зеленые оазисы нашей гостиницы! Здесь каждое растение находит свой дом, обеспечивая комфорт и уют как для них, так и для наших гостей. Мы с гордостью поддерживаем экосистему, где каждое зеленое создание процветает благодаря заботе и вниманию. Наш дом становится их домом, а уход за растениями - нашим приоритетом, создавая гармонию и радость для всех, кто здесь останавливается.</p>
                </div>
            </div>
        </SwiperSlide>
        <SwiperSlide class="relative">
            <img src="/images/hero/2.webp" alt="" class="object-cover aspect-video">
            <div class="absolute inset-0 bg-black/30"></div>
            <div class="absolute inset-0 px-4 flex justify-center items-center text-white">
                <div class="flex flex-col relative gap-6 w-full md:w-1/2 lg:w-1/3 p-4 lg:p-6 rounded-2xl overflow-hidden">
                    <div class="absolute inset-0 backdrop-blur-sm"></div>
                    <p class="text-2xl font-Comfortaa z-[1]">Погружение в зеленые объятия</p>
                    <p class="opacity-80 text-lg">В нашей гостинице для растений каждая зеленая душа находит свое идеальное место, где она может процветать в соответствии со своей природой. Наше внимание к деталям и забота о каждом растении позволяют им чувствовать себя как дома, а наши гости наслаждаются уютом и спокойствием этого зеленого уголка.</p>
                </div>
            </div>
        </SwiperSlide>
        <SwiperSlide class="relative">
            <img src="/images/hero/3.webp" alt="" class="object-cover aspect-video">
            <div class="absolute inset-0 bg-black/30"></div>
            <div class="absolute inset-0 px-4 flex justify-center items-center text-white">
                <div class="flex flex-col relative gap-6 w-full md:w-1/2 lg:w-1/3 p-4 lg:p-6 rounded-2xl overflow-hidden">
                    <div class="absolute inset-0 backdrop-blur-sm"></div>
                    <p class="text-2xl font-Comfortaa z-[1]">Создайте свой зеленый уголок</p>
                    <p class="opacity-80 text-lg">Ваш дом для растений начинается здесь. От ярких, солнечных окон, наполняющих пространство светом, до тщательно подобранной системы полива, обеспечивающей растения влагой в нужном объеме. Каждое растение становится частью обширного экосистемы, придающей жизнь нашему дому и наполняющей его живым, дыханием природы.</p>
                </div>
            </div>
        </SwiperSlide>
    </Swiper>
</template>

<script setup>

</script>