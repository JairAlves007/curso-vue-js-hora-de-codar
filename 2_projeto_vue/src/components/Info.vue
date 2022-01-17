<template>
  <div>
    <Picture />
    <p>
      {{ email }}
    </p>
    <p v-if="is_working">Estou trabalhando no momento.</p>
    <p v-else>
      Não estou trabalhando no momento.
    </p>
    <p v-show="show_email">Meu e-mail: {{ email }}</p>

    <div>
      <button @click="showEmail">
        {{ texto_botao }}
      </button>
    </div>

    <p>
      Para acessar meu portfolio, <a v-bind:href="meu_link" target="_blank">clique aqui</a>
    </p>

    <p>Utilizo as seguintes tecnologias para backend:</p>

    <ul>
      <li v-for="(backend, index) in backend_technologies" :key="index">
        {{ backend }}
      </li>
    </ul>

    <p>
      Utilizo as seguintes tecnologias para frontend
    </p>

    <ul>
      <li v-for="front in frontend_technologies" :key="front.id">
        {{ front.language }}
      </li>
    </ul>
  </div>
</template>

<script>
import Picture from './Picture.vue';

export default {
  name: "Info",
  components: {
    Picture
  },
  props: {
    email: String,
    is_working: Boolean
  },
  data() {
    return {
      show_email: true,
      meu_link: "https://google.com",
      texto_botao: "Mostrar E-mail",
      backend_technologies: [
        'Java',
        'PHP',
        'JavaScript'
      ],
      frontend_technologies: [
        {
          id: 1,
          language: "HTML"
        },
        {
          id: 2,
          language: "CSS"
        },
        {
          id: 3,
          language: "Bootstrap"
        }
      ]
    }
  },
  methods: {
    showEmail() {
      this.show_email = !this.show_email;

      this.show_email ? this.texto_botao = "Esconder E-mail" : this.texto_botao = "Mostrar E-mail";
    }
  }
};
</script>