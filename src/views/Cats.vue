<template>
    <div>
      <PetTable
        species="cats"
        :pets="cats"
      >
      </PetTable>
      <!--
      <b-table striped hover :items="cats" >
         <template v-slot:cell(name)="data">
        <router-link :to="`/pets/cats/${data.index}`">{{ data.value }}</router-link>
         </template>
      </b-table>
      -->
    </div>
</template>

<script>
import { mapState } from 'vuex'
import PetTable from '@/components/PetTable.vue'

export default {
  components: {
    PetTable
  },
  computed: {
    ...mapState([
      'cats'
    ])
  }
}
</script>
