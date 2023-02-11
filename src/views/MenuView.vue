<template>
  <div class="well">
    <b><font color="Green"><h1 class="list">Cocktail Recipes</h1></font></b>
    <button @click="loadmenu()">Cocktail</button>
    <!-- {{ menudata.drinks }} -->
    <ul class="text">
      <h4 v-for="drink in drinks" :key="drink.idDrink">
        {{ drink.strDrink }} {{ drink.strGlass }} {{ drink.strCategory }}
        <div><img :src="drink.strDrinkThumb" alt="" srcset="" width="200"></div>
         <u>Instructions</u>
        <h3>{{ drink.strInstructions }}</h3>
      </h4>
    </ul>
  </div>
</template>

<script setup>
import axios from "axios";
import { ref } from "vue";
const menudata = ref();
const drinks = ref();
const url = ref("https://www.thecocktaildb.com/api/json/v1/1/search.php?s=margarita");

function loadmenu() {
  axios
    .get(url.value)
    .then((response) => {
      menudata.value = response.data;
      drinks.value = menudata.value.drinks;
    })
    .catch((err) => {
      console.log(err);
    });
}
</script>
<style>
  .well{
    width: 100%;
    font-size: 14px;
    text-transform: lowercase;

  }
  .list{
    margin-top: auto;
    font-size: 30px;
  }
  .text{
  margin: auto;
 
  margin: 0.8em ,0.6em;
  }
</style>
