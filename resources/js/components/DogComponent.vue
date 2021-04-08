<template>
    <div class="container">

      <h2>Selezione la razza che preferisci</h2>

      <select class="breeds" name="breeds" v-model="selected">
        <option value="">Seleziona la categoria</option>
        <option v-for="(race, index) in breeds" v-bind:value="index">
          {{index}}
        </option>
      </select>

      <button class="btn-random" type="button" name="button" @click="chooseImg()">Foto</button>

      <button class="btn-random" type="button" name="button" @click="randomImg()">Random</button>

      <div class="doggoImg">
        <img :src=dogImg alt="">
      </div>
    </div>
</template>


<script>
    export default {
      data(){
          return {
              breeds: {},
              selected: "",
              dogImg: null
          }
      },

      methods:{
        chooseImg (){
          fetch('https://dog.ceo/api/breed/' + this.selected + '/images/random')
            .then(response => response.json())
            .then(data => this.dogImg=data.message);
        },

        randomImg(){
          // const rand = Math.floor(Math.random() * Object.keys(this.breeds).length);
          fetch('https://dog.ceo/api/breeds/image/random')
            .then(response => response.json())
            .then(data => this.dogImg=data.message);
        },
      },

      mounted() {
        fetch('https://dog.ceo/api/breeds/list/all')
          .then(response => response.json())
          .then(data => this.breeds = data.message);
          // .then(data => console.log(data));
      }
    }
</script>
