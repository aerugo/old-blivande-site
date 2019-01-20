<template>
  <v-container 
    fluid
  >
    <section class="wrapper generic">
      <div class="inner">
        <header class="major special">
          <h1>{{ title }}</h1>
          <p>{{ subtitle }}</p>
        </header>
        <div class="image main">
          <img 
            src="pic04.jpg" 
            alt=""
          >
        </div>
        <vue-markdown 
          :source="bodytext" 
        />
      </div>
    </section>
  </v-container>
</template>

<script>
import VueMarkdown from 'vue-markdown'
export default {
  components: {
    VueMarkdown
  },
  props: {
    bodytext: {
      type: String,
      required: true
    },
    title: {
      type: String,
      required: true
    },
    subtitle: {
      type: String,
      required: true
    }
  }
}
</script>

<style>
@import url('../static/css/font-awesome.min.css');
@import url('https://fonts.googleapis.com/css?family=IBM+Plex+Sans:200,200i,400,400i');
@import url('../static/css/typography.css');
@import url('../static/css/wrapper.css');
</style>
