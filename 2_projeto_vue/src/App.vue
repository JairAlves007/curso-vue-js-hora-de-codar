<template>
  <div>
    <Header :esta_logado="esta_logado" />
    <PrimeiroComponente />
    <p>
      {{ teste }}
    </p>
    <LifeCycle />
    <Pessoa />
    <Form />
  </div>
</template>

<script>

import Header from './components/Header.vue';
import PrimeiroComponente from "./components/PrimeiroComponente.vue";
import LifeCycle from "./components/LifeCycle.vue";
import Pessoa from './components/Pessoa.vue';
import Form from './components/Form.vue';

export default {
  name: "App",
  components: {
    Header,
    PrimeiroComponente,
    LifeCycle,
    Pessoa,
    Form,
  },
  data() {
    return {
      teste: "Teste",
      esta_logado: false
    }
  }
};
</script>

<style>
body{
  background-color: #333;
  color: #fff;
}
</style>