<script setup lang="ts">
import { ref } from 'vue';
import DecreaseButton from './DecreaseButton.vue';
import IncreaseButton from './IncreaseButton.vue';

const movies = ref([
{
    name: "Revengers",
    maxTickets: 12,
    defaultQuantity: 0,
  },
  {
    name: "Spuder Moon",
    maxTickets: 10,
    defaultQuantity: 0,
  },
  {
    name: "Baturu Man",
    maxTickets: 8,
    defaultQuantity: 0,
  },
  {
    name: "Journey Rabbit",
    maxTickets: 2,
    defaultQuantity: 0,
  },
  {
    name: "Blue Penter",
    maxTickets: 3,
    defaultQuantity: 0,
  },
  {
    name: "River Gens, Mid Game",
    maxTickets: 5,
    defaultQuantity: 0,
  },
]);

const decreaseQuantity = (movie: { defaultQuantity: number}) => {
  if (movie.defaultQuantity > 0) {
    movie.defaultQuantity--;
  }
}

const increaseQuantity = (movie: { defaultQuantity: number, maxTickets: number }) => {
  if (movie.defaultQuantity < movie.maxTickets) {
    movie.defaultQuantity++
  }
}

</script>

<template>
  <form v-for="movie in movies" :key="movie.name">
    <h3> {{ movie.name }} </h3>

    <DecreaseButton
      :movie="movie"
      @click="decreaseQuantity(movie)"
    />

    {{ movie.defaultQuantity }}

    <IncreaseButton
      :movie="movie"
      @click="increaseQuantity(movie)"
    />

  </form>
</template>

<!-- Styles with scope only for this component -->
<style lang="scss" scoped>

  @import "../styles/_variables.scss";

  h3 {
    margin-top: 0vh;
    margin-bottom: 2.1vh;
  }

  form {
    background: $bg;
    border: 3px dotted $border;
    border-radius: 9px;
    margin: 6vh;
    padding-top: 30px;
    padding-bottom: 30px;
    text-align: center;

    transform: scale(1);
    transition: 0.6s transform;
  }

  form:hover {
    transform: scale(1.2);
  }

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

