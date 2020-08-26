<template>
  <div style="margin-top:10px">
    <b-img
      center
      fluid
      src="https://www.creativefabrica.com/wp-content/uploads/2018/11/Letter-food-logo-by-DEEMKA-STUDIO-580x406.jpg"
    ></b-img>

    <br>
    <br>
    <br>

    <b-row>

       <b-col cols="2">
          <b-button  type="button" class="btn btn-danger" @click="randomMeal">Random meal!</b-button>
      </b-col>

      <b-col cols="8">
        <b-form-input v-model="pretraga" @keyup.enter="dohvatiPodatke" placeholder="Enter the name of the meal..."></b-form-input>
      </b-col>

      <b-col cols="2">
        <b-button type="button" class="btn btn-success" @click="dohvatiPodatke">SEARCH</b-button>
      </b-col>

    </b-row>

    <br>
    <br>

    <b-row>

      <b-col cols="12">
         <div style="margin-top:1px">
      <b-navbar variant="blue" type="light" toggleable="false">
        <b-navbar-brand
          v-for="(slovo, index) in slova"
          v-bind:key="slovo"
          v-on:click="getLetter(index)"
          style="cursor:pointer;"
        >
          <b>{{ slovo }}</b>
        </b-navbar-brand>
      </b-navbar>
    </div>
      </b-col>
    </b-row>

    

    <br>

    <b-row>
      <b-col cols="4" v-for="jelo in jela" v-bind:key="'jelo' + jelo.idMeal">
        <b-card
          :title="jelo.strMeal"
          :img-src="jelo.strMealThumb"
          img-height="340px"
          img-width="340px"
          img-alt="Image"
          img-top
          tag="article"
          style="max-width: 20rem;"
          class="mb-2"
        >
          <b-card-text>
            <br>
            <h5>CATEGORY: </h5>
            {{ jelo.strCategory }}
            <br />
            <h5>ARENA: </h5>
            {{ jelo.strArea }}
            <br>
            <br> 
            <h5>INGREDIENT: </h5>
            {{ jelo.strIngredient1 }}
            <br> 
            {{ jelo.strIngredient2 }}
            <br> 
            {{ jelo.strIngredient3 }} 
            <br> 
            {{ jelo.strIngredient4 }}
            <br> 
            {{ jelo.strIngredient5 }}
            <br> 
            {{ jelo.strIngredient6 }}
            <br> 
            {{ jelo.strIngredient7 }}
            <br> 
            {{ jelo.strIngredient8 }}
            <br> 
            {{ jelo.strIngredient9 }}
            <br> 
            {{ jelo.strIngredient10 }}
            <br> 
          </b-card-text>
        </b-card>
      </b-col>
      
    </b-row>
   
  </div>
</template>

<script>
export default {
  name: "PopsiJela",

  data: function () {
    return {
      pretraga: "",
      jela: [],
      slova: [
        "A",
        "B",
        "C",
        "D",
        "E",
        "F",
        "G",
        "H",
        "I",
        "J",
        "K",
        "L",
        "M",
        "N",
        "O",
        "P",
        "Q",
        "R",
        "S",
        "T",
        "U",
        "V",
        "W",
        "X",
        "Y",
        "Z"
      ]
    };
  },

  methods: {
    dohvatiPodatke: function () {
      this.axios
        .get(
          "https://www.themealdb.com/api/json/v1/1/search.php?s=" +
            this.pretraga
        )
        .then((response) => {
          console.log(response.data.meals);

          this.jela = response.data.meals;
        });
    },randomMeal: function() {
      this.axios
        .get("https://www.themealdb.com/api/json/v1/1/random.php")
        .then(response => {
          console.log(response.data.meals);

          this.jela = response.data.meals;
        });
    }, getLetter: function(i) {
      this.axios
        .get(
          "https://www.themealdb.com/api/json/v1/1/search.php?f=" +
            this.slova[i]
        )
        .then(response => {
          console.log(response.data.meals);

          this.jela = response.data.meals;
        });
    }
  },
};
</script>

<style>
</style>