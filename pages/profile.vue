<template>
    <div class="flex flex-col gap-4 w-full col-span-full">
        <div class="w-full relative md:h-[300px]">
            <img src="/images/profile/hero.webp" alt="" class="object-cover h-full w-full object-bottom">
            <div class="absolute inset-0 flex items-center justify-center z-[2]">
                <div class="relative w-fit p-6 overflow-hidden rounded-xl">
                    <p class="text-4xl text-white font-Comfortaa z-[1] relative">Профиль</p>
                    <div class="absolute inset-0 backdrop-blur-md"></div>
                </div>
            </div>
        </div>
        <div class="flex items-center gap-2 font-Comfortaa text-lg wrapper mx-auto w-full px-[15px] sm:px-5">
            <NuxtLink to="/" class="relative after:absolute after:w-0 after:h-px after:bg-[#665E5E] after:bottom-0 after:left-0 after:transition-all after:duration-500 hover:after:w-full">Главная</NuxtLink>
            <p>/</p>
            <p>Профиль</p>
        </div>
    </div>
    <div class="flex flex-col gap-6">
        <p class="text-3xl font-Comfortaa text-[#569E0B]/70">Контактные данные</p>
        <FormKit @submit="updateUser" type="form" :actions="false" messages-class="hidden" form-class="flex flex-col gap-4 items-center justify-center">
            <div class="flex items-center lg:items-start gap-4 max-lg:flex-col md:w-2/3 lg:w-1/2">
                <FormKit type="text" v-model="user.name" validation="required" messages-class="text-[#E9556D] font-Comfortaa" name="Фамилия" outer-class="w-full lg:w-1/3" input-class="px-4 py-2 border border-[#569E0B]/70 rounded-xl focus:outline-none w-full" placeholder="Фамилия"/>
                <FormKit type="text" v-model="user.surname" validation="required" messages-class="text-[#E9556D] font-Comfortaa" name="Имя" outer-class="w-full lg:w-1/3" input-class="px-4 py-2 border border-[#569E0B]/70 rounded-xl focus:outline-none w-full" placeholder="Имя"/>
                <FormKit type="text" v-model="user.patronymic" validation="required" messages-class="text-[#E9556D] font-Comfortaa" name="Отчество" outer-class="w-full lg:w-1/3" input-class="px-4 py-2 border border-[#569E0B]/70 rounded-xl focus:outline-none w-full" placeholder="Отчество"/>
            </div>
            <div class="flex items-center lg:items-start gap-4 max-lg:flex-col md:w-2/3 lg:w-1/2">
                <FormKit type="text" v-model="user.login" validation="required" messages-class="text-[#E9556D] font-Comfortaa" name="Логин" outer-class="w-full lg:w-1/2" input-class="px-4 py-2 border border-[#569E0B]/70 rounded-xl focus:outline-none w-full" placeholder="Логин"/>
                <FormKit type="text" v-model="user.password" validation="required|length:6" messages-class="text-[#E9556D] font-Comfortaa" name="Пароль" outer-class="w-full lg:w-1/2" input-class="px-4 py-2 border border-[#569E0B]/70 rounded-xl focus:outline-none w-full" placeholder="••••••"/>
            </div>            
            <button type="submit" class="px-4 py-2 bg-[#569E0B] text-white rounded-full w-[160px] text-center">Обновить данные</button>
            <button type="button" @click="messageTitle = null" class="fixed top-10 right-10 z-[11] cursor-pointer flex items-center gap-4 px-6 py-2 rounded-2xl w-fit bg-white shadow-[0px_0px_13px_-7px_black]" :class="messageType ? ' text-[#569E0B]/70' : 'text-red-500'" v-if="messageTitle">
                <span>{{messageTitle}}</span>
            </button>
        </FormKit>
    </div>
    <div class="flex flex-col gap-6">
        <p class="text-3xl font-Comfortaa text-[#569E0B]/70">Выход из аккаунта</p>
        <button type="button" @click="logout" class="px-4 py-2 bg-[#569E0B] text-white rounded-full w-[160px] text-center">Выход</button>
    </div>
    <div class="flex flex-col gap-6" v-if="role == 'user'">
        <p class="text-3xl font-Comfortaa text-[#569E0B]/70">Список заказов</p>
        <div class="flex flex-col gap-8 text-lg rounded-xl border border-[#569E0B]/70 p-4 relative lg:w-1/2" v-for="order in ordersArray">
            <div class="flex flex-col gap-4">
                <p><span class="font-Comfortaa">Номер заказа:</span> <span class="font-bold">{{ order[0].orderId }}</span></p>
                <p><span class="font-Comfortaa">Статус заказа:</span> <span class="font-bold">{{ order[0].status }}</span></p>
                <p><span class="font-Comfortaa">Адрес:</span> <span class="font-bold">{{ order[0].address }}</span></p>
                <p><span class="font-Comfortaa">Итоговая цена:</span> <span class="font-bold">{{ sums[ordersArray.indexOf(order)].toLocaleString() }} ₽</span></p>
            </div>
            <div class="flex flex-col gap-4 rounded-xl shadow-[0px_0px_13px_-7px_black] p-4" v-for="o in order">
                <p><span class="font-Comfortaa">Наименование товара:</span> <span class="font-bold">{{ o.products.title }}</span></p>
                <img :src="o.products.img" alt="" class="rounded-xl w-[160px]">
                <p><span class="font-Comfortaa">Количество товара:</span> <span class="font-bold">{{ o.count }}</span></p>
                <p><span class="font-Comfortaa">Цена за единицу:</span> <span class="font-bold">{{ o.price }}</span></p>
            </div>
            <button v-if="order[0].status == 'Новый'" @click="deleteOrder(order[0].orderId)" class="absolute top-4 right-4 text-red-500">
                <Icon class="text-3xl" name="ic:baseline-close"/>
            </button>
        </div>
    </div>
    <div class="flex flex-col gap-6" v-if="role == 'user'">
        <p class="text-3xl font-Comfortaa text-[#569E0B]/70">Заявки на аренду</p>
        <div class="flex flex-col gap-4 text-lg rounded-xl border border-[#569E0B]/70 p-4 relative w-fit" v-for="rent in rents">
            <p><span class="font-Comfortaa">Номер заказа:</span> <span class="font-bold">{{ rent.id }}</span></p>
            <div class="flex items-start max-md:flex-col gap-4 w-full">
                <p><span class="font-Comfortaa">Начальная дата:</span> <span class="font-bold">{{ rent.dateFrom }}</span></p>
                <p><span class="font-Comfortaa">Конечная дата:</span> <span class="font-bold">{{ rent.dateTo }}</span></p>
            </div>
            <p><span class="font-Comfortaa">Количество растений:</span> <span class="font-bold">{{ rent.count }}</span></p>
            <div class="flex items-start max-md:flex-col gap-4 w-full">
                <p><span class="font-Comfortaa">Телефон:</span> <span class="font-bold">{{ rent.phone }}</span></p>
                <p><span class="font-Comfortaa">Адрес:</span> <span class="font-bold">{{ rent.address }}</span></p>
            </div>
            <p><span class="font-Comfortaa">Статус заказа:</span> <span class="font-bold">{{ rent.status }}</span></p>
            <button v-if="rent.status == 'Новая'" @click="deleteRent(rent.id)" class="absolute top-4 right-4 text-red-500">
                <Icon class="text-3xl" name="ic:baseline-close"/>
            </button>
        </div>
    </div>
</template>

<script setup>
    /* название и язык страницы */
    useSeoMeta({
        title: 'Профиль',
        lang: 'ru'
	})
    

    /* подключение БД и проверка пользователя */
    const supabase = useSupabaseClient() 
    const { id, authenticated, role } = storeToRefs(useUserStore())

    const { data:users, error } = await supabase
    .from('users')
    .select('*')   
    .eq('id',`${id.value}`)  


    /* создание сообщений и роутера */
    const { messageTitle, messageType } = storeToRefs(useMessagesStore())
    const router = useRouter()


    /* создание формы пользователя */
    const user = ref({
        name: users[0].name,
        surname: users[0].surname,
        patronymic: users[0].patronymic,
        login: users[0].login,
        password: users[0].password
    }) 


    /* обновление данных */
    const updateUser = async () => {        
        const { data, error } = await supabase
        .from('users')
        .update({ name: `${user.value.name}`, surname: `${user.value.surname}`, patronymic: `${user.value.patronymic}`, login: `${user.value.login}`, password: `${user.value.password}`})
        .eq('id', `${id.value}`)
        .select()
          
        if(data) {
            console.log(data[0])
            messageTitle.value = 'Данные обновлены!', messageType.value = true 
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


    /* выход из аккаунта */
    const logout = () => {
        authenticated.value = false
        id.value = null
        role.value = ""
        messageTitle.value = 'Успешный выход!', messageType.value = true
        setTimeout(() => {
            messageTitle.value = null
        }, 3000)
        router.push("/")
    }


    /* заявка на аренду */
    const { data: rents, error:rentError } = await supabase
    .from('rent')
    .select('*')
    .eq('userId', `${id.value}`)

    const deleteRent = async (rentId) => {
        const { data, error } = await supabase
        .from('rent')
        .update({ status: 'Отменена'})
        .eq('id', `${rentId}`)
        .eq('status', `Новая`)
        .select()
          
        if(data) {
            console.log(data[0])
            messageTitle.value = 'Заявка отменена!', messageType.value = true 
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


    /* список заказов и проверка номеров */ 
    const orderNumbers = []
    const { data: carts } = await supabase
    .from('cart')
    .select(`*, products (*)`)
    .eq('userId',`${id.value}`)
    carts.forEach(el => {
        if(orderNumbers.indexOf(el.orderId) === -1) {
            orderNumbers.push(el.orderId)
        }
    })    

    const ordersArray = ref([])
    const sums = ref([])
    for (let i = 0; i < orderNumbers.length; i++) {
        const array = []
        let sum = 0
        carts.forEach(el => {
            if(el.orderId == orderNumbers[i]) {
                array.push(el)
                sum+= el.count * el.products.price
            }
        })
        ordersArray.value.push(array)
        sums.value.push(sum)
    }


    /* отмена заказа */
    const deleteOrder = async (orderId) => {
        const { data, error } = await supabase
        .from('cart')
        .update({ status: 'Отменён'})
        .eq('orderId', `${orderId}`)
        .eq('status', `Новый`)
        .select()
          
        if(data) {
            console.log(data[0])
            messageTitle.value = 'Заказ отменён!', messageType.value = true 
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
</script>