<template>
   <div>
      <button @click="primeiro('Primeiro Evento'), segundo('Segundo Evento'), terceiro('')">
         Ativar Múltiplos Eventos
      </button>

      <p>
         {{ multiplos_eventos }}
      </p>
   </div>
</template>

<script>
export default {
   name: "MultiplosEventos",
   data() {
      return {
         multiplos_eventos: ""
      }
   },
   methods: {
      primeiro(txt) {  
         this.multiplos_eventos = txt;
      },
      segundo(txt) {
         setTimeout(
            () => this.multiplos_eventos = txt
         , 1000);
      },
      terceiro(txt) {
         setTimeout(
            () => this.multiplos_eventos = txt
         , 1500);
      }
   }
}
</script>

<style scoped>
   div {
      margin: 100px;
   }
</style>