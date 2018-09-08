<template>
  <div>
    <h1 @click="onClick">
      {{message}}
    </h1>
    <Layout>
      <h1 slot="header">How To Build Vue Apps Like A Pro 😎</h1>
      <h2 slot="body"> by Rajat S</h2>
      <h3 slot="footer">Technical Content Writer</h3>
    </Layout>
    <Settings>
      <Layout slot-scope="{ header }">
        <h1 slot="header">Hola {{header}}</h1>
      </Layout>
    </Settings>
    <h2>Usando desde la instancia de un componente con slots, los valores que maneja ese componente</h2>
    <TodoList :todos="todos">
      <template slot-scope="slotScope">
        <span v-if="slotScope.todo.isComplete">✓</span>
          {{ slotScope.todo.text }}
      </template>
    </TodoList>
    <h2>Otra forma....</h2>
    <TodoList :todos="todos">
      <template slot-scope="{ todo }">
        <span v-if="todo.isComplete">✓</span>
          {{ todo.text }}
      </template>
    </TodoList>
    <h2>Pequeño ejemplo de uso de Functional Components</h2>
    <FunctionalButton :type="'type_1'" @click="log('me clickaste 1')">Clicame</FunctionalButton>
    <FunctionalButton :type="'type_2'" @click="log('me clickaste 2')">Clicame</FunctionalButton>
  </div>
</template>

<script>
import Vue from 'vue';
//import Component from 'vue-class-component';
import {Component, Prop} from 'vue-property-decorator';
import Layout from './components/Layout';
import Settings from './components/Settings.vue';
import TodoList from './components/TodoList';
import FunctionalButton from './components/FunctionalButton'

export default Component ({
  components: {Layout, Settings, TodoList, FunctionalButton},
  methods: {
    log (message) {
      console.log(message)
    }
  }
}) (
  class App extends Vue {
    message = 'Batman';
    todos = [{id:1, text:'primera tarea'}, {id:2, text:'segunda tarea', isComplete: true}];
    onClick() {
      this.message = 'Bruce Wayne'
    }
  }
)
</script>

<style>
* {
  margin: 0;
  padding: 0;
}
</style>
