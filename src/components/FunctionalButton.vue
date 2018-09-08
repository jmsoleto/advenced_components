<template functional>
  <button :class="props.type" @click="listeners.click"><slot></slot></button>
</template>

<script>
  export default {
    name: 'FunctionalButton',
    props: {
      type: {
        required: true,
        type: String
      }
    }
  } 
</script>

<style scoped>
  button{
    padding: .5rem;
    margin: 0;
    color: white;
    border: none;
    outline: none;
  }
  .type_1{
    background: red;
  }

  .type_2{
    background: green;
  }
</style>
