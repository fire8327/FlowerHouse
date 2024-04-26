<template>
    <div class="flex items-center justify-center gap-6 max-lg:flex-col w-full">
        <img :src="props.products.img" alt="" v-if="props.products.type == 'product'" class="object-cover aspect-[7/10] lg:w-1/4 rounded-xl">
        <img :src="props.products.img" alt="" v-if="props.products.type == 'service'" class="object-cover aspect-video lg:w-1/4 rounded-xl">
        <div class="flex flex-col gap-4 lg:w-1/3">
            <p class="text-2xl font-Comfortaa">{{ props.products.title }}</p>
            <p class="text-xl font-semibold">{{ props.products.price.toLocaleString() }} ₽</p>      
            <div class="flex items-center justify-center gap-6 px-4 py-1.5 w-[160px] rounded-xl border border-[#665E5E]">
                <button @click="minusCard" class="text-2xl">-</button>
                <p>{{ countProduct }}</p>
                <button @click="plusCard" class="text-2xl">+</button>
            </div>    
            <button type="button" @click="deleteProduct" v-if="props.products.type == 'product'" class="px-4 py-2 border border-[#569E0B] text-[#569E0B] rounded-full shrink-0 w-[160px]">Удалить товар</button>
            <button type="button" @click="deleteProduct" v-if="props.products.type == 'service'" class="px-4 py-2 border border-[#569E0B] text-[#569E0B] rounded-full shrink-0 w-[160px]">Удалить услугу</button>
        </div>    
    </div>
</template>

<script setup>
    /* props */
    const props = defineProps({
        id: Number,
        count: Number,
        products: Object
    })
    const countProduct = ref(props.count)


    /* управление количеством и БД */
    const supabase = useSupabaseClient()     
    const plusCard = async () => {
        countProduct.value++

        const { data, error } = await supabase
        .from('cart')
        .update({ count: `${countProduct.value}` })
        .eq('id', `${props.id}`)
        .select()  
    }
    const minusCard = async () => {
        if (countProduct.value > 1) {
            countProduct.value--

            const { data, error } = await supabase
            .from('cart')
            .update({ count: `${countProduct.value}` })
            .eq('id', `${props.id}`)
            .select() 
        }
    }


    /* создание сообщений и роутера */
    const { messageTitle, messageType } = storeToRefs(useMessagesStore())


    /* удаление товара и роут */
    const deleteProduct = async () => {
        const { error } = await supabase
        .from('cart')
        .delete()
        .eq('id', `${props.id}`)

        if(error) {
            messageTitle.value = 'Произошла ошибка!', messageType.value = false 
            setTimeout(() => {
                messageTitle.value = null
            }, 3000)             
        } else {
            messageTitle.value = 'Удалено!', messageType.value = true 
            setTimeout(() => {
                messageTitle.value = null
            }, 3000)             
        }
    }
</script>