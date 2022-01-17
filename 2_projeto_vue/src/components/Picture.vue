<template>
  <div>
    <img :src="avatar" :alt="description" />

    <MudarImagem @mudarImagem="mudarImagem"/>
  </div>
</template>

<script>
import MudarImagem from "./MudarImagem.vue";

export default {
  name: "Picture",
  components: {
    MudarImagem,
  },
  data() {
    return {
      avatar: "/img/avatar.png",
      description: "Jair Alves",
    };
  },
  methods: {
    mudarImagem() {
      
      this.avatar === "/img/avatar.png" ? 
      this.avatar = "/img/avatar2.png" : 
      this.avatar = "/img/avatar.png";

    }
  }
};
</script>