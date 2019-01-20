<template>

  <v-container 
    id="banner"
    fluid
  >
    <hero 
      :users="users" 
    />
  </v-container>

</template>

<script>
import axios from 'axios'
import countTo from 'vue-count-to'
import Vuex from 'vuex'
import Hero from '~/components/Hero.vue'

export default {
  components: {
    Hero
  },
  props: {
    users: {
      type: Array,
      required: true
    }
  }
}
</script>
