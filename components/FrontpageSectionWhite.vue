<template>
  <v-container 
    id="first"
    class="wrapper style1"
    fluid
  >
    <div class="inner">
      <header 
        v-if="title"
        class="major special"
      >
        <h2>{{ title }}</h2>
        <vue-markdown
          v-if="text" 
          :source="text" 
        />
      </header>
      <div class="spotlights">
        <section 
          v-for="section in sections"
          :key="section.id"
        >
          <div>
            <v-img 
              :src="section.image"
              class="image"
              alt="" />
          </div>
          <div class="content">
            <header 
              v-if="!section.logo"
              class="major"
            >
              <h3>{{ section.title }}</h3>
            </header>
            <img 
              v-if="section.logo" 
              :src="section.logo"
              alt="section.title"> 
            <header class="major">
              <p><vue-markdown :source="section.text" /></p>
            </header>
            <ul 
              v-if="section.link"
              class="actions special">
              <li>
                <a 
                  :href="section.link" 
                  class="button primary wide"
                >
                  {{ section.button }}
                </a>
              </li>
            </ul>
          </div>
        </section>
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
    sections: {
      type: Array,
      required: true
    },
    title: {
      type: String,
      required: true
    },
    text: {
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
