<template>
    <div class="flex flex-col gap-4 w-full col-span-full">
        <div class="w-full relative md:h-[300px]">
            <img src="/images/cart/hero.webp" alt="" class="object-cover h-full w-full object-center">
            <div class="absolute inset-0 flex items-center justify-center z-[2]">
                <div class="relative w-fit p-6 overflow-hidden rounded-xl">
                    <p class="text-4xl text-white font-Comfortaa z-[1] relative">Корзина</p>
                    <div class="absolute inset-0 backdrop-blur-md"></div>
                </div>
            </div>
        </div>
        <div class="flex items-center gap-2 font-Comfortaa text-lg wrapper mx-auto w-full px-[15px] sm:px-5">
            <NuxtLink to="/" class="relative after:absolute after:w-0 after:h-px after:bg-[#665E5E] after:bottom-0 after:left-0 after:transition-all after:duration-500 hover:after:w-full">Главная</NuxtLink>
            <p>/</p>
            <p>Корзина</p>
        </div>
    </div>
    <div class="flex flex-col gap-6 w-full">
        <p class="text-3xl font-Comfortaa text-[#569E0B]/70">Список товаров</p>
        <CartCard v-for="cart in carts" v-bind="cart"></CartCard>
        <p class="text-xl font-semibold"><span class="font-Comfortaa text-[#569E0B]/70">Итоговая цена: </span>Цена ₽</p>
    </div>
    <div class="flex flex-col gap-6">
        <p class="text-3xl font-Comfortaa text-[#569E0B]/70">Оформление заказа</p>
        <FormKit type="form" :actions="false" messages-class="hidden" form-class="flex flex-col gap-4 w-full items-center md:w-2/3 lg:w-1/2 md:mx-auto">
            <div class="flex items-start gap-2 w-full">
                <FormKit type="text" validation="required|number" messages-class="text-[#E9556D] font-Comfortaa" name="Номер карты" outer-class="max-md:w-full md:w-2/4" input-class="px-4 py-2 border border-[#569E0B]/70 rounded-xl focus:outline-none w-full" placeholder="Номер карты"/>
                <FormKit type="text" validation="required|number" messages-class="text-[#E9556D] font-Comfortaa" name="Срок действия" outer-class="max-md:w-full md:w-1/4" input-class="px-4 py-2 border border-[#569E0B]/70 rounded-xl focus:outline-none w-full" placeholder="YY/YY"/>
                <FormKit type="text" validation="required|number" messages-class="text-[#E9556D] font-Comfortaa" name="CVC" outer-class="max-md:w-full md:w-1/4" input-class="px-4 py-2 border border-[#569E0B]/70 rounded-xl focus:outline-none w-full" placeholder="CVC"/>
            </div>
            <FormKit type="textarea" validation="required" messages-class="text-[#E9556D] font-Comfortaa" name="Адрес доставки" outer-class="w-full" input-class="px-4 py-2 border border-[#569E0B]/70 rounded-xl focus:outline-none w-full" placeholder="Адрес доставки"/>
            <button type="submit" class="px-4 py-2 bg-[#569E0B] text-white rounded-full shrink-0 w-[160px]">Оформить заказ</button>
        </FormKit>
    </div>
</template>

<script setup>
    /* проверка входа */
    const { id } = storeToRefs(useUserStore())


    /* подключение к БД */
    const supabase = useSupabaseClient()     
    const { data: carts, error } = await supabase
    .from('cart')
    .select(`*, products (*)`)
    .eq('status', 'В корзине')
    .eq('userId', `${id.value}`)
</script>