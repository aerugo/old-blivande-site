<template>
  <v-container 
    fluid
  >
    <section class="wrapper generic">
      <div 
        :data-url="url"
        class="calendly-inline-widget" 
        style="margin: auto; width: 75%; min-width:340px; height:580px;" />
    </section>
  </v-container>
</template>

<script>
export default {
  props: {
    url: {
      type: String,
      required: true
    }
  },
  mounted() {
    let calendlyScript = document.createElement('script')
    calendlyScript.setAttribute(
      'src',
      'https://assets.calendly.com/assets/external/widget.js'
    )
    document.head.appendChild(calendlyScript)
  }
}
</script>

<style>
@import url('../static/css/wrapper.css');
</style>
