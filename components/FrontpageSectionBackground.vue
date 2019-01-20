<template>
  <v-container 
    id="first"
    class="wrapper style2 alt"
    fluid
  >
    <div class="inner">
      <header class="major special">
        <h2>{{ title }}</h2>
        <vue-markdown :source="text" />
      </header>
      <div class="features">
        <ul>
          <li>
            <img 
              :src="features.tllogo" 
              class="icons"
            >
            <h3>{{ features.tltitle }}</h3>
            <vue-markdown :source="features.tltext" />
          </li>
          <li>
            <img 
              :src="features.bllogo" 
              class="icons"
            >
            <h3>{{ features.bltitle }}</h3>
            <vue-markdown :source="features.bltext" />
          </li>
        </ul>
        <span class="image">
          <img 
            :src="image" 
            alt=""
          >
        </span>
        <ul>
          <li>
            <img 
              :src="features.trlogo" 
              class="icons"
            >
            <h3>{{ features.trtitle }}</h3>
            <vue-markdown :source="features.trtext" />
          </li>
          <li>
            <img 
              :src="features.brlogo" 
              class="icons"
            >
            <h3>{{ features.brtitle }}</h3>
            <vue-markdown :source="features.brtext" />
          </li>
        </ul>
      </div>
    </div>
  </v-container>
</template>

<script>
import VueMarkdown from 'vue-markdown'
export default {
  components: {
    VueMarkdown
  },
  props: {
    features: {
      type: Object,
      required: true
    },
    title: {
      type: String,
      required: true
    },
    text: {
      type: String,
      required: true
    },
    image: {
      type: String,
      required: true
    }
  }
}
</script>
