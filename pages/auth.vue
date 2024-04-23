<template>
    <FormKit type="form" :actions="false" messages-class="hidden" form-class="flex flex-col gap-4 items-center justify-center grow">
        <p class="text-3xl font-Comfortaa text-[#569E0B]/70">Вход</p>
        <div class="flex items-center lg:items-start gap-4 max-lg:flex-col md:w-2/3 lg:w-1/2">
            <FormKit type="text" validation="required" messages-class="text-[#E9556D] font-Comfortaa" name="Логин" outer-class="w-full lg:w-1/2" input-class="px-4 py-2 border border-[#569E0B]/70 rounded-xl focus:outline-none w-full" placeholder="Логин"/>
            <FormKit type="text" validation="required" messages-class="text-[#E9556D] font-Comfortaa" name="Пароль" outer-class="w-full lg:w-1/2" input-class="px-4 py-2 border border-[#569E0B]/70 rounded-xl focus:outline-none w-full" placeholder="Имя"/>
        </div>
        <button class="px-4 py-2 bg-[#569E0B] text-white rounded-full w-[160px] text-center">Вход</button>
        <div class="flex items-center justify-center gap-4 w-full md:w-2/3 lg:w-1/2 my-10">
            <div class="w-1/3 h-px bg-[#569E0B]/70"></div>  
            <p class="font-Comfortaa text-[#569E0B]/70">или</p>
            <div class="w-1/3 h-px bg-[#569E0B]/70"></div>  
        </div>
        <NuxtLink to="/reg" class="mx-auto px-4 py-2 border border-[#569E0B] text-[#569E0B] rounded-full w-[160px] text-center">Регистрация</NuxtLink>
    </FormKit>
</template>

<script setup>

</script>