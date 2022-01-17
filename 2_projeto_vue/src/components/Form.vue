<template>
   <form id="form-app" @submit="enviarForm">
      <input type="text" v-model="name"/>
      <input type="text" v-model="email"/>
      <Submit />
   </form>
</template>

<script>

// import InputText from './Form/InputText.vue';
import Submit from './Form/Submit.vue';

export default {
   name: "Form",
   components: {
      // InputText,
      Submit
   },
   data() {
      return {
         name: "",
         email: ""
      }
   },
   methods: {
      enviarForm(e){
         e.preventDefault();
         console.log('Form enviado');
      }
   }
}
</script>