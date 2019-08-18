<template>
  <div>
    <v-layout row>
      <page-banner
        :style="{ 'background-image': 'url(/frihamnstorget.jpg)' }"
      />
    </v-layout>
    <v-layout row>
      <front-page-section-white 
        :sections="frihamnstorgetSections"
      />
    </v-layout>
    <v-layout row>
      <front-page-footer />
    </v-layout>
  </div>
</template>

<script>
import axios from 'axios'
import VueMarkdown from 'vue-markdown'
import PageBanner from '~/components/PageBanner.vue'
import FrontPageSectionWhite from '~/components/FrontpageSectionWhite.vue'
import GenericSection from '~/components/GenericSection.vue'
import FrontPageFooter from '~/components/FrontpageFooter.vue'

export default {
  components: {
    PageBanner,
    VueMarkdown,
    FrontPageSectionWhite,
    GenericSection,
    FrontPageFooter
  },
  head() {
    return {
      title: 'House Blivande – Frihamnstorget',
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: `
          Blivande is a co-working space, 
          arts workshop, makerspace and 
          community center in Stockholm.`
        },
        {
          hid: 'keywords',
          name: 'keywords',
          content: `
          co-working, co-working space, makerspace, 
          arts workshop, community, burn, burning man, 
          participatory, co-creation, stockholm`
        },
        {
          hid: 'og:image',
          name: 'og:image',
          content: 'http://www.blivande.com/frihamnstorget.jpg'
        }
      ]
    }
  },
  async asyncData({ params }) {
    let blivande_content = await axios.get(
      'https://participio-api.herokuapp.com/discourse/blivande/frontpage'
    )
    let pagebanner = 'taubanner'
    let tauSymbol = 'stsymbol.png'
    let frihamnstorgetAbout = blivande_content['data']['292']
    let frihamnstorgetJoin = blivande_content['data']['293']
    let frihamnstorgetPageContent = blivande_content['data']['36']
    let frihamnstorgetSections = [
      {
        title: 'What is Frihamnstorget?',
        text: frihamnstorgetAbout,
        image: 'containers.png',
        id: 1
      },
      {
        title: 'How do I join?',
        text: frihamnstorgetJoin,
        image: 'frihamnstorget-small.jpg',
        link: 'https://forum.blivande.com/c/tau',
        button: 'Join Frihamnstorget',
        id: 2
      }
    ]

    return {
      pagebanner,
      frihamnstorgetAbout,
      frihamnstorgetJoin,
      frihamnstorgetPageContent,
      frihamnstorgetSections
    }
  }
}
</script>

<style>
@import url('../static/css/font-awesome.min.css');
@import url('https://fonts.googleapis.com/css?family=IBM+Plex+Sans:200,200i,400,400i');
@import url('../static/css/typography.css');
@import url('../static/css/banner.css');
@import url('../static/css/row.css');
@import url('../static/css/box.css');
@import url('../static/css/button.css');
@import url('../static/css/form.css');
@import url('../static/css/icon.css');
@import url('../static/css/image.css');
@import url('../static/css/list.css');
@import url('../static/css/actions.css');
@import url('../static/css/icons.css');
@import url('../static/css/table.css');
@import url('../static/css/wrapper.css');
@import url('../static/css/spotlights.css');
@import url('../static/css/features.css');
@import url('../static/css/header.css');
@import url('../static/css/footer.css');
@import url('../static/css/nav-panel.css');
</style>
