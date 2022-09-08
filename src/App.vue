<script>
import HeaderRow from './components/HeaderRow.vue';
import FooterRow from './components/FooterRow.vue';

export default {
  components: { FooterRow, HeaderRow },
  name: 'App',
  data () {
    return {

    }
  }
}
</script>

<template>




  <div class="header">
    <HeaderRow />
  </div>


  <div class="body">
    <router-view />
  </div>



  <div class="footer">
    <FooterRow />
  </div>



</template>


<style lang="scss" scoped>
.login-cmp {
  width: clamp(50rem, 80%, 80rem);
  height: 100%;
  background-color: rgba(255, 255, 255, 0.65);
  position: absolute;
  z-index: 1;
}

.product-container-cmp {
  margin: 0 auto;
}

.footer {
  margin-top: 9rem;
}
</style>
