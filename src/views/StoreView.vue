<template>
    <div>
        <store-carousel></store-carousel>
        <the-footer></the-footer>
    </div>
</template>

<script>
import StoreCarousel from '@/components/StoreCarousel'
import TheFooter from '@/components/TheFooter'

export default{
    name: 'StoreView',
    components: {
        StoreCarousel,  
        TheFooter,  
    },
}

</script>