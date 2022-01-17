<template>
   <h1>
      Meu Nome É {{ nome }}
   </h1>
</template>

<script>
export default {
   name: "LifeCycle",
   data() {
      return {
         nome: "Não Sei"
      }
   },
   created() {
      setTimeout(() => {
         this.nome = "Jair";
      }, 1000);
   },
   mounted() {
      this.nome = "Alves";
   },
}
</script>