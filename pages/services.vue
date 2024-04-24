<template>
    <div class="flex flex-col gap-4 w-full col-span-full">
        <div class="w-full relative md:h-[300px]">
            <img src="/images/services/hero.webp" alt="" class="object-cover object-bottom h-full w-full">
            <div class="absolute inset-0 flex items-center justify-center z-[2]">
                <div class="relative w-fit p-6 overflow-hidden rounded-xl">
                    <p class="text-4xl text-white font-Comfortaa z-[1] relative">Услуги</p>
                    <div class="absolute inset-0 backdrop-blur-md"></div>
                </div>
            </div>
        </div>
        <div class="flex items-center gap-2 font-Comfortaa text-lg wrapper mx-auto w-full px-[15px] sm:px-5">
            <NuxtLink to="/" class="relative after:absolute after:w-0 after:h-px after:bg-[#665E5E] after:bottom-0 after:left-0 after:transition-all after:duration-500 hover:after:w-full">Главная</NuxtLink>
            <p>/</p>
            <p>Услуги</p>
        </div>
    </div>
    <div class="flex flex-col gap-6">
        <p class="text-3xl font-Comfortaa text-[#569E0B]/70">Пересадка растений</p>
        <p class="text-lg">
            Наши специалисты пересадят растения в подходящий качественный грунт с консультацией по подходящему объему горшка.
        </p>
        <div class="grid grid-cols-1 md:grid-cols-2 xl:grid-cols-4 gap-6">
           <Card v-for="service in services" v-bind="service"></Card>
        </div>
    </div>
    <div class="flex flex-col gap-6">
        <p class="text-3xl font-Comfortaa text-[#569E0B]/70">Гостиница для растений</p>
        <p class="text-lg">
            Мы готовы взять на себя заботу о ваших растениях на время вашего отпуска, командировки.
            Во время пребывания растений в гостинице они получат профессиональный уход, обработку от вредителей.
            В летний период времени возможно размещение растений на открытом воздухе, что способствует увеличению их иммунитета.
        </p>
        <div class="flex flex-col gap-4 items-center md:w-2/3 lg:w-1/2 mx-auto">
            <img src="/images/services/rent.webp" alt="" class="aspect-video object-cover rounded-xl">
            <FormKit type="form" :actions="false" messages-class="hidden" form-class="flex flex-col gap-4 w-full items-center">
                <div class="flex items-start gap-2 w-full">
                    <FormKit type="date" validation="required" messages-class="text-[#E9556D] font-Comfortaa" name="Начальная дата" outer-class="max-md:w-full md:w-1/2" input-class="px-4 py-2 border border-[#569E0B]/70 rounded-l-xl focus:outline-none w-full"/>
                    <FormKit type="date" validation="required" messages-class="text-[#E9556D] font-Comfortaa" name="Конечная дата" outer-class="max-md:w-full md:w-1/2" input-class="px-4 py-2 border border-[#569E0B]/70 rounded-r-xl focus:outline-none w-full"/>
                </div>
                <div class="flex items-start gap-2 w-full">
                    <FormKit type="text" validation="required|number" messages-class="text-[#E9556D] font-Comfortaa" name="Количество растений" outer-class="max-md:w-full md:w-1/3" input-class="px-4 py-2 border border-[#569E0B]/70 rounded-xl focus:outline-none w-full" placeholder="Количество"/>
                    <FormKit type="text" validation="required|number|length:11" messages-class="text-[#E9556D] font-Comfortaa" name="Номер телефона" outer-class="max-md:w-full md:w-2/3" input-class="px-4 py-2 border border-[#569E0B]/70 rounded-xl focus:outline-none w-full" placeholder="Номер телефона"/>
                </div>
                <FormKit type="textarea" validation="required" messages-class="text-[#E9556D] font-Comfortaa" name="Адрес доставки" outer-class="w-full" input-class="px-4 py-2 border border-[#569E0B]/70 rounded-xl focus:outline-none w-full" placeholder="Адрес доставки"/>
                <button type="submit" class="px-4 py-2 bg-[#569E0B] text-white rounded-full shrink-0 w-[160px]">Заказать услугу</button>
            </FormKit>
        </div>
    </div>
</template>

<script setup>
    /* подключение БД */
    const supabase = useSupabaseClient() 

    const { data: services, error } = await supabase
    .from('products')
    .select('*')
</script>