<script>
import axios from 'axios';
export default {
  data() {
    return {
      pet: {
        name: '',
        type: '',
        breed: '',
        breedType: 'known', // known | unknown | mix
        mixedBreedDetails: '',
        gender: '',
      },
      breedOptions: {
        cat: ['Tabby', 'Siamese', 'Domestic Long-haired', 'Domestic Short-haired', 'Bengal', 'Russian Blue', 'Can\'t find it?'],
        dog: ['Labrador', 'Bulldog', 'Retriever', 'German Shepherd', 'Poodle', 'Beagle', 'Can\'t find it?']
      },
    }
  },
  methods: {
    submitForm() {
      // send pet data to API, inform user, clear form data
      axios.post("http://localhost:8000/api/pets", this.pet)
        .then(response => alert('Success!'))
        .then(response => this.pet = {
          name: '',
          type: '',
          breed: '',
          breedType: 'known',
          mixedBreedDetails: '',
          gender: '',
        })
        .catch(error => alert('Something went wrong, please try again.'));
    }
  }
}
</script>
<template>
  <div class="form">
    <img src="@/assets/pawprints.png" />
    <h1>Tell us about your pet</h1>

    <p class="form-label">What is your pet's name?</p>
    <input v-model="pet.name" />

    <div class="type-options">
      <p class="form-label">What type of pet are they?</p>
      <input type="radio" class="type-option" id="cat" value="cat" v-model="pet.type" /><label for="cat">Cat</label>
      <input type="radio" class="type-option" id="dog" value="dog" v-model="pet.type" /><label for="dog">Dog</label>
    </div>

    <p class="form-label">What breed are they?</p>
    <select v-model="pet.breed">
      <option v-if="pet.type === 'cat'" v-for="item in breedOptions.cat" :value="item">{{item}}</option>
      <option v-if="pet.type === 'dog'" v-for="item in breedOptions.dog" :value="item">{{item}}</option>
      <option v-if="pet.type === ''" disabled>Please select a pet type first</option>
    </select>

    <div class="breed-options" v-if="pet.breed === 'Can\'t find it?'">
      <p class="form-label">Choose One</p>
      <input type="radio" class="breed-option" id="unknown" value="unknown" v-model="pet.breedType" /><label for="unknown">I don't know</label><br/>
      <input type="radio" class="breed-option" id="mix" value="mix" v-model="pet.breedType" /><label for="mix">It's a mix</label><br />
      <input class="mixed-breed-input" v-model="pet.mixedBreedDetails" placeholder="Which breeds are in the mix?" v-if="pet.breedType === 'mix'" />
    </div>

    <p class="form-label">What gender are they?</p>
    <div class="gender-options">
      <button :class="{ 'selected-gender': pet.gender === 'female' }" class="button-style gender-button female" @click="pet.gender = 'female'">Female</button>
      <button :class="{ 'selected-gender': pet.gender === 'male' }" class="button-style gender-button male" @click="pet.gender = 'male'">Male</button>
    </div>

    <div class="continue">
      <button class="button-style submit-button" @click=submitForm()>Save Pet</button>
    </div>
  </div>
</template>

<style scoped>
@import '@/assets/base.css';

.form {
  background-color: white;
  width: 70vw;
  max-width: 350px;
  min-height: 500px;
  margin: 25px auto;
  padding: 15px;
  display: flex;
  flex-direction: column;
}

// TODO: update select dropdown icon to be a magnifying glass
input, select {
  padding: 5px 12px;
  background-color: white;
  border: 1px solid darkgray;
  border-radius: 3px;
}

.form-label {
  font-size: 15px;
  margin: 15px 0 2px 0;
}

.breed-options {
  margin-left: 20px;
}

.breed-option, .type-option {
  margin: 8px;
}

.breed-option label::after {
  color: #fff;
}

.breed-option label::before {
  color: #fff;
}

.mixed-breed-input {
  margin-left: 8px;
  max-width: 200px;
}

h1 {
  color: #2f628f;
  font-size: 18px;
  font-weight: 500;
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

.gender-button:hover {
  background-color: #00aeef;
  color: white;
}

.female {
  border-radius: 5px 0 0 5px;
}

.male {
  border-radius: 0 5px 5px 0;
}

.selected-gender {
  background-color: #00aeef;
  color: white;
}

.submit-button {
  background-color: #00aeef;
  color: white;
  padding: 8px 50px;
}

.submit-button:hover {
  background-color: white;
  color: #00aeef;
}

.continue {
  margin: 35px auto 0 auto;
}

@media (min-width: 1024px) {
  .form {
    max-width: 500px;
    margin: 50px auto;
    padding: 35px 55px;
  }
}
</style>
