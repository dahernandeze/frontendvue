<template>
  <div class="Services">
    <my-services></my-services>
    <other-services></other-services>
    <the-footer></the-footer>
  </div>
</template>
  
  
  <script>
  // @ is an alias to /src
  import MyServices from '@/components/MyServices.vue'
  import OtherServices from '@/components/OtherServices.vue'
  import TheFooter from '@/components/TheFooter.vue'
  
  export default {
    name: 'ServicesView',
    components: {
      MyServices,
      OtherServices,
      TheFooter,
    }
  }
  </script>
  