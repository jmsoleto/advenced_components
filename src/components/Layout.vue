<template>
  <div>
    <div class="header">
      <slot  name="header"></slot>
    </div>
    <slot name="body"></slot>
    <slot name="footer"></slot>
  </div>
</template>

<script>
export default {

}
</script>

<style>
.header{
  background: #fafafa;
  padding: 1.5rem;
  margin-bottom: 1rem;
}

</style>
