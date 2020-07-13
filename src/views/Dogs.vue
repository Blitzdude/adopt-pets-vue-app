<template>
    <div>
      <PetTable
        species="dogs"
        :pets="dogs"
      >
      </PetTable>
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
      'dogs'
    ])
  }
}
</script>
