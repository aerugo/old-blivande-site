<template>

  <v-container 
    :id="page"
    fluid
  >

    <v-layout
      align-center
      column
      justify-center
    >
      <img 
        :src="logo"
        class="symbol"
        alt="Blivande" 
      >
    </v-layout>

  </v-container>

</template>

<script>
import Vuex from 'vuex'
export default {
  props: {
    logo: {
      type: String,
      required: true
    },
    page: {
      type: String,
      required: true
    }
  }
}
</script>
