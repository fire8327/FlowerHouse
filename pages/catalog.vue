<template>
    <div class="flex flex-col gap-4 w-full col-span-full">
        <div class="w-full relative md:h-[300px]">
            <img src="/images/catalog/hero.webp" alt="" class="object-cover h-full w-full">
            <div class="absolute inset-0 flex items-center justify-center z-[2]">
                <div class="relative w-fit p-6 overflow-hidden rounded-xl">
                    <p class="text-4xl text-white font-Comfortaa z-[1] relative">Каталог</p>
                    <div class="absolute inset-0 backdrop-blur-md"></div>
                </div>
            </div>
        </div>
        <div class="flex items-center gap-2 font-Comfortaa text-lg wrapper mx-auto w-full px-[15px] sm:px-5">
            <NuxtLink to="/" class="relative after:absolute after:w-0 after:h-px after:bg-[#665E5E] after:bottom-0 after:left-0 after:transition-all after:duration-500 hover:after:w-full">Главная</NuxtLink>
            <p>/</p>
            <p>Каталог</p>
        </div>
    </div>
    <div class="flex items-center lg:justify-between gap-6 max-lg:flex-col p-4 shadow-[0px_0px_13px_-7px_black] rounded-xl">
        <div class="flex items-center gap-6 max-lg:flex-col max-lg:w-full">
            <div class="flex items-center gap-2 max-lg:w-full">
                <FormKit type="text" v-model="filters.minPrice" name="От" outer-class="w-1/2" input-class="px-4 py-2 border border-[#569E0B]/70 rounded-l-xl focus:outline-none w-full" placeholder="От"/>
                <FormKit type="text" v-model="filters.maxPrice" name="До" outer-class="w-1/2" input-class="px-4 py-2 border border-[#569E0B]/70 rounded-r-xl focus:outline-none w-full" placeholder="До"/>
            </div>
            <FormKit v-model="filters.products" type="select" :options="selectOptions" outer-class="max-lg:w-full" input-class="px-4 py-2 border border-[#569E0B]/70 rounded-xl focus:outline-none w-full bg-white"/>
            <FormKit type="text" v-model="filters.title" name="Название" outer-class="max-lg:w-full" input-class="px-4 py-2 border border-[#569E0B]/70 rounded-xl focus:outline-none w-full" placeholder="Название"/>
        </div>
        <div class="flex items-center gap-4">
            <button type="button" @click="filterProducts" class="px-4 py-2 w-fit bg-[#569E0B] text-white rounded-xl">Применить</button>
            <button type="button" @click="cancelFilters" class="px-4 py-2 w-fit border border-[#569E0B] text-[#569E0B] rounded-xl">Отменить</button>
        </div>    
    </div>
    <div class="grid grid-cols-1 md:grid-cols-2 xl:grid-cols-4 gap-6">
       <Card v-for="product in products" v-bind="product"></Card>
    </div>
</template>

<script setup>
    /* подключение БД */
    const supabase = useSupabaseClient() 

    const { data, error } = await supabase
    .from('products')
    .select('*')   
    .eq('type','product')
    .order('title', { ascending: true })    

    const products = ref(data)   

    
    /* управление select'ом */
    const selectOptions = ref(['Все'])
    products.value.forEach(el => {
        if(selectOptions.value.indexOf(el.productType) === -1) {
            selectOptions.value.push(el.productType)
        }
    })

    /* создание фильтров */    
    const filters = ref({
        minPrice: "",
        maxPrice: "",
        title: "",
        products: 'Все'
    })


    /* фильтры */
    const filterProducts = () => {
        products.value = data
        const filter = products.value.filter(el => {
            if (el.price < filters.value.minPrice && filters.value.minPrice) {
                return false
            }
            if (el.price > filters.value.maxPrice && filters.value.maxPrice) {
                return false
            }
            if (el.productType != filters.value.products && filters.value.products != 'Все') {
                return false
            }
            if (el.title.toLowerCase().indexOf(filters.value.title) == -1 && filters.value.title) {
                return false
            }
            return true
        })     
        products.value = filter
    }    

    const cancelFilters = () => {
        products.value = data
        filters.value.minPrice = ""
        filters.value.maxPrice = ""
        filters.value.title = ""
        filters.value.products = "Все"
    }
</script>