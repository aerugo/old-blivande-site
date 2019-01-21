<template>

  <v-container 
    id="pagebanner"
    fluid
  >

    <v-layout
      align-center
      column
      justify-center
    >
      <img 
        v-if="logo"
        :src="logo"
        class="symbol"
        alt="Blivande" 
      >
      <h1
        v-if="title"
      >
        {{ title }}
      </h1>
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
    title: {
      type: String,
      required: true
    }
  }
}
</script>
