<template>
    <div class="home">
      <my-intro></my-intro>
      <my-services></my-services>
      <our-success></our-success>
      <our-results></our-results>
      <other-services></other-services>
      <the-footer></the-footer>
    </div>
  </template>
  
  <script>
  // @ is an alias to /src
  import MyIntro from '@/components/MyIntro.vue'
  import MyServices from '@/components/MyServices.vue'
  import OurSuccess from '@/components/OurSuccess.vue'
  import OurResults from '@/components/OurResults.vue'
  import OtherServices from '@/components/OtherServices.vue'
  import TheFooter from '@/components/TheFooter.vue'
  
  export default {
    name: 'HomeView',
    components: {
      MyIntro,
      MyServices,
      OurSuccess,
      OurResults,
      OtherServices,
      TheFooter,
    },
  }
  </script>
  
  


