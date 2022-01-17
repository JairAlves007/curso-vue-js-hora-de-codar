<template>
  <Banner />
  <div class="main-container">
    <h1>Monte Seu Burger:</h1>
    <BannerForm />
  </div>
</template>

<script>
import Banner from '../components/Banner.vue';
import BannerForm from '../components/BurgerForm.vue';

export default {
  name: "Home",
  components: {
    Banner,
    BannerForm
  }
}
</script>