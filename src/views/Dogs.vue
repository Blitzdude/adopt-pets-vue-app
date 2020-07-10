<template>
    <div>
      <h1>
        Dogs For Adoption
      </h1>
      <b-table striped hover :items="dogs" ></b-table>
    </div>
</template>

<script>
import { mapState } from 'vuex'
export default {
  computed: {
    ...mapState([
      'dogs'
    ])
  }
}
</script>
