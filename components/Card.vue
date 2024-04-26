<template>
    <div class="flex flex-col gap-6">
        <button @click="isProductShow = true" class="overflow-hidden rounded-xl" v-if="props.type == 'product'">
            <img :src="props.img" alt="" class="transition-all duration-500 hover:scale-125 object-cover aspect-[7/10]">
        </button>
        <img :src="props.img" alt="" class="rounded-xl object-cover aspect-video" v-else>
        <div class="flex flex-col grow">
            <p class="text-2xl font-Comfortaa">{{ props.title }}</p>
            <p class="text-lg" v-if="props.type == 'service'">{{ props.desc }}</p>
        </div>
        <p class="text-xl font-semibold">{{ props.price.toLocaleString() }}₽</p>        
        <div class="flex items-center gap-2 text-lg" v-if="authenticated && role == 'user'">
            <div class="flex items-center justify-center gap-6 px-4 py-1.5 grow rounded-xl border border-[#665E5E]">
                <button class="text-2xl" @click="minusCount">-</button>
                <p>{{ cardCount }}</p>
                <button class="text-2xl" @click="plusCount">+</button>
            </div>    
            <button @click="addCart" class="w-3/5 px-4 py-2 text-center bg-[#569E0B] transition-all duration-500 hover:bg-[#665E5E] text-white rounded-xl">В корзину</button>
        </div>
    </div>
    <div class="fixed inset-0 bg-white z-[7] flex items-center justify-center transition-all duration-500" :class="{'translate-y-[3000px]' : !isProductShow}" v-if="props.type == 'product'">
        <div class="flex items-center max-lg:flex-col gap-8 p-6 lg:w-2/3">
            <img :src="props.img" alt="" class="rounded-xl max-lg:aspect-video lg:aspect-[7/10] object-cover max-lg:object-bottom md:w-2/3 lg:w-1/2">
            <div class="flex flex-col gap-6 lg:w-1/2">
                <p class="text-2xl font-Comfortaa">{{ props.title }}</p>
                <p class="text-xl font-semibold">{{ props.price.toLocaleString() }}₽</p>
                <div class="flex items-center gap-2 text-lg" v-if="authenticated && role == 'user'">
                    <div class="flex items-center justify-center gap-6 px-4 py-1.5 grow rounded-xl border border-[#665E5E]">
                        <button class="text-2xl" @click="minusCount">-</button>
                        <p>{{ cardCount }}</p>
                        <button class="text-2xl" @click="plusCount">+</button>
                    </div>    
                    <button @click="addCart" class="w-3/5 px-4 py-2 text-center bg-[#569E0B] transition-all duration-500 hover:bg-[#665E5E] text-white rounded-xl">В корзину</button>
                </div>
                <p class="text-lg">{{ props.desc }}</p>
            </div>
        </div>
        <button @click="isProductShow = false" class="fixed top-8 right-8 z-[8]">
            <Icon class="text-3xl" name="ic:baseline-close"/>
        </button>
    </div>
</template>

<script setup>
    /* управление количеством */
    const cardCount = ref(1)

    const plusCount = () => {
        cardCount.value++
    }
    const minusCount = () => {
        if (cardCount.value > 1) {
            cardCount.value--
        }
    }


    /* props */
    const props = defineProps({
        id: Number,
        type: String,
        title: String,
        price: Number,
        desc: String,
        img: String,
        productType: String,
        created_at: String
    })


    /* товар подробно */
    const isProductShow = ref(false)


    /* проверка входа */
    const { authenticated, id, role } = storeToRefs(useUserStore())


    /* создание сообщений */
    const { messageTitle, messageType } = storeToRefs(useMessagesStore())


    /* подключение к БД и добавление в корзину */
    const supabase = useSupabaseClient()     

    const addCart = async () => {
        const { data: carts, error } = await supabase
        .from('cart')
        .select(`*, products (*)`)
        .eq('status', 'В корзине')
        .eq('userId', `${id.value}`)
        .eq('productId', `${props.id}`)

        console.log(carts)

        if(carts.length>0) {
            const { data, error } = await supabase
            .from('cart')
            .update({ count: `${Number(carts[0].count)+cardCount.value}` })
            .eq('status', 'В корзине')
            .eq('userId', `${id.value}`)
            .eq('productId', `${props.id}`)
            .select()      
        
            messageTitle.value = 'Количество обновлено!', messageType.value = true
            setTimeout(() => {
                messageTitle.value = null
            }, 3000)
        } else {            
            const { data, error } = await supabase
            .from('cart')
            .insert([
                { userId: `${id.value}`, productId: `${props.id}`, status: 'В корзине', count: `${cardCount.value}` },
            ])
            .select()       
            
            if(data) {
                messageTitle.value = 'Добавлено в корзину!', messageType.value = true
                setTimeout(() => {
                    messageTitle.value = null
                }, 3000)
            } else {
                messageTitle.value = 'Произошла ошибка!', messageType.value = false
                setTimeout(() => {
                    messageTitle.value = null
                }, 3000) 
            }            
        }
    }
</script>