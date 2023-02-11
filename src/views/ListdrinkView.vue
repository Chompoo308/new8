<template>
    <div class="Dk">
      <font color="MediumSeaGreen"><h1 class="list">Drink list</h1></font>
      <button @click="loadmenu()">List</button>
      <div class="love">
      <ul>
        <li v-for="drink in drinks" :key="drink.idDrink">
          {{ drink.strDrink }} {{ drink.strGlass }}
          <div><img :src="drink.strDrinkThumb" width="150"></div>
         
        </li>
      </ul>
      </div>
    </div>
  </template>
  
  <script setup>
  import axios from "axios";
  import { ref } from "vue";
  const menudata = ref();
  const drinks = ref();
  const url = ref("https://www.thecocktaildb.com/api/json/v1/1/search.php?f=a");
  
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
    .list{
      margin-top: auto;
  

    }
    .love{
      display: flex;
    }
  </style>