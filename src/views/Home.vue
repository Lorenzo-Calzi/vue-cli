<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <!-- <HelloWorld msg="Ei to Your Vue.js App"/> -->
    <post-section>
      
    </post-section>
  </div>
</template>

<script>
// @ is an alias to /src
/* import HelloWorld from '@/components/HelloWorld.vue' */

import PostSection from '@/components/PostSection.vue'

export default {
  name: 'Home',
  components: {
    /* HelloWorld */
    PostSection
  }
}
</script>
