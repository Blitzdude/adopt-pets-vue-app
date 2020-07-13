<template>
  <div class="home-view-container">
    <img alt="Vue logo" src="../assets/logo.png">
    <div>
      <h1>
        Adopt a New best friend
      </h1>
      <h2>We have {{ animalsCount }} Available</h2>
      <h3>Cats: {{ getAllCats.length }} </h3>
    </div>
    <button class="btn btn-primary" @click="togglePetForm">Add New Pet</button>

    <b-form @submit.prevent="onSubmit" v-if="showPetForm">

      <b-form-group id="input-group-2" label="Pets Name:" label-for="input-2">
        <b-form-input
          id="input-2"
          v-model="formData.name"
          required
          placeholder="Enter name"
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-3" label="Species:" label-for="input-3">
        <b-form-select
          id="input-3"
          v-model="formData.species"
          :options=" ['cats','dogs'] "
          required
        ></b-form-select>
      </b-form-group>

      <b-form-group id="input-group-4" label="Pets Age:" label-for="input-5">
        <b-form-input
          id="input-2"
          v-model="formData.age"
          type="number"
          required
          placeholder="Enter Age"
        ></b-form-input>
      </b-form-group>

      <b-button type="submit" variant="primary">Submit</b-button>
    </b-form>
  </div>
</template>

<script>
import { mapActions, mapGetters } from 'vuex'
export default {
  name: 'Home',
  data () {
    return {
      showPetForm: false,
      formData: {
        name: '',
        age: 0,
        species: null
      }
    }
  },
  computed: {
    ...mapGetters([
      'animalsCount',
      'getAllCats'
    ])
  },
  methods: {
    ...mapActions([
      'addPet'
    ]),
    togglePetForm () {
      this.showPetForm = !this.showPetForm
    },
    onSubmit () {
      const { species, age, name } = this.formData
      const payload = {
        species,
        pet: {
          name,
          age
        }
      }
      this.addPet(payload)

      // Reset form after submit
      this.formData = {
        name: '',
        age: 0,
        species: null
      }
      this.togglePetForm()
    }
  }
}
</script>
