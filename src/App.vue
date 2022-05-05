<script>
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  props: {
    petName: String,
    petBreed: String,
    breedType: String
  },
  emits: ['update:petName', 'update:petBreed', 'update:breedType']
}
</script>

<template>
  <header>
    <img alt="logo" class="logo" src="@/assets/logo.png" width="80" height="80" />

    <div class="menu-items">
      <a href="#" class="menu-item">Help</a>
      <a href="#" class="menu-item logo-blue">Save and Finish Later</a>
    </div>
  </header>

  <body>
    <div class="form">
      <h1>Tell us about your dog</h1>

      <p class="form-label">What is your dog's name?</p>
      <input v-model="petName" />
      <p class="form-label">What breed are they?</p>
      <select v-model="petBreed">
        <option disabled value="">Please select one</option>
        <option>Breed 1</option>
        <option>Breed 2</option>
        <option>Breed 3</option>
        <option>Can't find it?</option>
      </select>

      <div class="breed-options">
        <p class="form-label">Choose One</p>
        <input type="radio" class="breed-option" id="unknown-breed" value="I don't know" v-model="breedType" /><label>I don't know</label><br/>
        <input type="radio" class="breed-option" id="mix-breed" value="It's a mix" v-model="breedType" /><label>It's a mix</label>
      </div>

      <p class="form-label">What gender are they?</p>
      <div class="pillbox-group">
        <button class="button-style gender-button selected-gender">Female</button>
        <button class="button-style gender-button">Male</button>
      </div>

      <div class="continue">
        <button type="submit" class="button-style submit-button">Continue</button>
      </div>
    </div>
  </body>

</template>

<style>
@import '@/assets/base.css';

#app {
  max-width: 1280px;
  margin: 0 auto;

  font-weight: normal;
}

header {
  display: flex;
  justify-content: space-between;
  background-color: white;
  padding: 10px;
}

.logo {
  align-items: flex-end;
  justify-content: flex-end;
}

.menu-items {
  display: flex;
  align-items: flex-end;
  margin-bottom: 10px;
}

.menu-item {
  margin: 5px;
}

.menu-item:hover {
  color: #00aeef;
}

.logo-blue {
  color: #00aeef;
}

.logo-blue:hover {
  color: black;
}

a {
  text-decoration: none;
  transition: 0.4s;
  color: black;
}

body {
  background-color: #f6f6f6;
}

.form {
  background-color: white;
  width: 70vw;
  max-width: 500px;
  min-height: 500px;
  margin: 50px auto;
  padding: 35px 55px;
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
}

.form-label {
  font-size: 14px;
}

.breed-options {
  margin-left: 20px;
}

.breed-option {
  margin: 8px;
}

h1 {
  color: #2f628f;
  font-size: 18px;
}

.button-style {
  border: 1px solid #00aeef;
  border-radius: 5px;
}

.gender-button {
  background-color: white;
  color: #00aeef;
  padding: 5px 25px;
}

.selected-gender {
  background-color: #00aeef;
  color: white;
}

.submit-button {
  background-color: #00aeef;
  color: white;
  padding: 8px 55px;
}

@media (min-width: 1024px) {
  body {
    display: flex;
    place-items: center;
  }

  #app {
    display: grid;
    grid-template-columns: 1fr 1fr;
    padding: 0 2rem;
  }

  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }


}
</style>
