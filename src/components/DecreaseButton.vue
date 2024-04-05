<script setup lang="ts">

  import { defineProps } from 'vue';

  const props = defineProps<{ movie: { defaultQuantity: number} }>();

  const handleClick = () => {
    props.movie.defaultQuantity--;
  }

</script>

<template>
  <button
    type="button"
    @click="handleClick"
    :disabled="movie.defaultQuantity <= 0"
  >

  -
  
  </button>
</template>

<!-- Styles with scope only for this component -->
<style lang="scss" scoped>

  @import "../styles/_variables.scss";

  button {
    background: $color;
    border: 2.1px solid $border;
    border-radius: 100%;
    cursor: pointer;
    color: $border;
    transition: border-color 0.15;
  }

  button:hover{
    border-color: $bg;

  }

  button[disabled]{
    opacity: 0.5;
  }
</style>
