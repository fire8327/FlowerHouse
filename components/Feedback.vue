<template>
    <div class="flex flex-col gap-6 w-full rounded-xl bg-[#569E0B]/20">
        <div class="w-full h-[2px] bg-[#569E0B]/50 mt-6"></div>
        <div class="flex flex-col items-center gap-4 px-6">
            <p class="text-4xl font-Comfortaa text-center">Остались вопросы?</p>
            <p class="text-2xl md:w-2/3 xl:w-1/2 text-center opacity-70 -mt-4">Оставьте заявку и мы свяжемся с вами в ближайшее время</p>
            <button @click="isFeedbackShow = true" class="px-4 py-1.5 rounded-xl bg-[#569E0B] text-white transition-all duration-500 hover:bg-[#665E5E] text-lg">Оставить заявку</button>
        </div>
        <div class="w-full h-[2px] bg-[#569E0B]/50 mb-6"></div>
        <div @click="isFeedbackShow = false" class="fixed bg-black/70 inset-0 z-[5] transition-all duration-500" :class="{'-translate-x-full' : !isFeedbackShow}"></div>
        <button @click="isFeedbackShow = false" class="fixed top-8 right-8 z-[6]" :class="{'hidden' : !isFeedbackShow}">
            <Icon class="text-3xl text-white" name="ic:baseline-close"/>
        </button>
        <div class="fixed z-[6] transition-all duration-500 left-1/2 top-1/2 -translate-y-1/2" :class="isFeedbackShow ? '-translate-x-1/2' : 'translate-x-[5000px]'">
            <FormKit type="form" :actions="false" form-class="p-4 bg-white flex flex-col gap-8 w-full max-w-[300px] rounded-xl" messages-class="text-[#E9556D] font-Comfortaa">
                <p class="text-xl font-Comfortaa">Форма обратной связи</p>
                <div class="flex flex-col gap-4">
                    <FormKit type="text" name="Имя" validation="required" messages-class="text-[#E9556D] font-Comfortaa" input-class="w-full rounded-xl bg-transparent focus:outline-none border border-[#569E0B] py-2 px-4" placeholder="Ваше имя"></FormKit>
                    <FormKit type="text" name="Номер телефона" validation="required" messages-class="text-[#E9556D] font-Comfortaa" input-class="w-full rounded-xl bg-transparent focus:outline-none border border-[#569E0B] py-2 px-4" placeholder="Ваш номер телефона"></FormKit>
                </div>
                <button class="px-4 py-1.5 rounded-xl bg-[#569E0B] text-white transition-all duration-500 hover:bg-[#665E5E] text-lg">Отправить</button>
            </FormKit>
        </div>
    </div>
</template>

<script setup>
    /* открытие формы */
    const isFeedbackShow = ref(false)
</script>