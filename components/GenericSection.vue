<template>
  <v-container 
    fluid
  >
    <v-layout 
      row
      wrap
    >
      <v-flex 
        md6
        class="hidden-sm-and-down"
      >
        <v-img
          src="/blivandemeeting.jpg"
          contain
          max-height="650px"
          position="75%"
        />
      </v-flex>
      <v-flex 
        xs1 
        class="hidden-sm-and-up" 
      /> 
      <v-flex 
        xs12
        sm10
        md6
      >
        <v-layout row>
          <v-flex 
            xs1
            hidden-md-and-up
          />
          <v-flex xs10>
            <header 
              class="major"
            >
              <h2>Join Beta</h2>
            </header>
            <vue-markdown 
              :source="bodytext" 
            />
          </v-flex>
        </v-layout>
      </v-flex>
      <v-flex 
        xs1 
        class="hidden-sm-and-up"  
      />          
    </v-layout>
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
