<template>
   <div>
      <h2>
         Esta é a descrição da pessoa {{ name }}
      </h2>

      <Info :email="email" :is_working="is_working" />
   </div>
</template>

<script>
import Info from "./Info.vue";

export default {
   name: "Pessoa",
   components: {
      Info
   },
   data() {
      return {
         name: "Jair",
         email: "jair@gmail.com",
         is_working: true
      }
   }
}
</script>