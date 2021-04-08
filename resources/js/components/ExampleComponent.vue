<template>
    <div class="container">
      <h1>doggo</h1>

      <select class="breeds" name="breeds">
        <option v-for="(race, index) in breeds.message">
          {{index}}
        </option>
      </select>

    </div>
</template>

<script>
    export default {
      data(){
          return {
              breeds:null
          }
      },

      methods:{

      },

      mounted() {
        fetch('https://dog.ceo/api/breeds/list/all')
          .then(response => response.json())
          .then(data => this.breeds = data);
      }
    }
</script>
