<template>
  <div class="about">
    <our-history></our-history>
    <our-results></our-results>
    <our-success></our-success>
    <the-footer></the-footer>
  </div>
</template>


<script>
// @ is an alias to /src
import OurHistory from '@/components/OurHistory.vue'
import OurResults from '@/components/OurResults.vue'
import OurSuccess from '@/components/OurSuccess.vue'
import TheFooter from '@/components/TheFooter.vue'

export default {
  name: 'AboutView',
  components: {
    OurHistory,
    OurResults,
    OurSuccess,
    TheFooter,
  }
}
</script>

