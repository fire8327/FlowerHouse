<template>
    <div class="flex flex-col gap-4 w-full col-span-full">
        <div class="w-full relative md:h-[300px]">
            <img src="/images/FAQ/hero.webp" alt="" class="object-cover object-center h-full w-full">
            <div class="absolute inset-0 flex items-center justify-center z-[2]">
                <div class="relative w-fit p-6 overflow-hidden rounded-xl">
                    <p class="text-4xl text-white font-Comfortaa z-[1] relative">FAQ</p>
                    <div class="absolute inset-0 backdrop-blur-md"></div>
                </div>
            </div>
        </div>
        <div class="flex items-center gap-2 font-Comfortaa text-lg wrapper mx-auto w-full px-[15px] sm:px-5">
            <NuxtLink to="/" class="relative after:absolute after:w-0 after:h-px after:bg-[#665E5E] after:bottom-0 after:left-0 after:transition-all after:duration-500 hover:after:w-full">Главная</NuxtLink>
            <p>/</p>
            <p>FAQ</p>
        </div>
    </div>
    <div class="flex flex-col gap-6 text-lg">
        <p class="text-3xl font-Comfortaa text-[#569E0B]/70">Гарантия</p>
        <div class="flex flex-col gap-2">
            <p class="text-xl font-Comfortaa text-[#569E0B]/70">• Гарантия на качественный уход</p>
            <p>Персонал гостиницы будет обеспечивать все оптимальные и благоприятные условия для роста и развития растений, включая полив, удобрения, обрезку и защиту от вредителей.</p>
        </div>
        <div class="flex flex-col gap-2">
            <p class="text-xl font-Comfortaa text-[#569E0B]/70">• Гарантия на сохранность растений</p>
            <p>Все растения будут здоровы и сохранят свою декоративность во время пребывания в гостинице. В случае увядания или изменения цвета, цветочная гостиница обязуется предпринять необходимые меры для восстановления внешнего вида растения.</p>
        </div>
        <div class="flex flex-col gap-2">
            <p class="text-xl font-Comfortaa text-[#569E0B]/70">• Гарантия на возмещение ущерба</p>
            <p>Возмещается ущерб в размере платы за пребывания в гостинице в случае повреждения или гибели растений в результате ненадлежащего обращения или ухода.</p>
        </div>
    </div>
    <div class="flex flex-col gap-6 text-lg">
        <p class="text-3xl font-Comfortaa text-[#569E0B]/70">Доставка</p>
        <div class="flex flex-col">
            <p>Бесплатная доставка не распространяется на услугу по аренде мест в цветочном отеле. Доставка растений в  гостиницу и из гостиницы рассчитывается менеджером в зависимости от количества растений и размера горшка. </p>
            <p>Если Вы не смогли связываться с сотрудниками доставки и перенести дату доставки в течение 5 дней после оформления заказа, то заказ будет аннулирован менеджером и осуществлен возврат денежных средств.</p>
            <p>После истечения срока аренды, если Вы не смогли принять доставку в назначенный день, Вам необходимо связаться с менеджером и продлить Ваш срок аренды. </p>
            <p>В случае некачественной доставки необходимо проинформировать менеджера для возмещения ущерба.</p>
        </div> 
    </div>
    <div class="flex flex-col gap-6 text-lg">
        <p class="text-3xl font-Comfortaa text-[#569E0B]/70">Часто задаваемые вопросы</p>
        <div class="flex flex-col gap-2">
            <p class="text-xl font-Comfortaa text-[#569E0B]/70">• Какие виды растений доступны для аренды в вашей цветочной гостинице?</p>
            <p>Все виды растения доступны для аренды в нашей цветочной гостинице. Стоимость аренды зависит только от количества и размера горшка.</p>
        </div>
        <div class="flex flex-col gap-2">
            <p class="text-xl font-Comfortaa text-[#569E0B]/70">• Какие дополнительные услуги доступны для растений?</p>
            <p>В стоимость аренды включены полив, удобрение, обрезка и защита от вредителей. Наши специалисты обеспечат качественный уход Вашим растениям!</p>
        </div>
        <div class="flex flex-col gap-2">
            <p class="text-xl font-Comfortaa text-[#569E0B]/70">• Что произойдет с растениями в случае, если они забудут забрать их?</p>
            <p>В случае если Вы не смогли забрать свои растения в течение месяца, не заплатив за продление аренды, цветочная гостиница будет вправе распорядиться этими растениями по своему усмотрению.</p>
        </div>
    </div>
</template>

<script setup>
    /* название и язык страницы */
    useSeoMeta({
        title: 'FAQ',
        lang: 'ru'
	})
</script>