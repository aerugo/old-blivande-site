<template>
  <div>
    <v-layout row>
      <page-banner
        :style="{ 'background-image': 'url(/blivandebluebanner.jpg)' }"
        :logo="betaSymbol"
      />
    </v-layout>
    <v-layout row>
      <front-page-section-white 
        :sections="betaSections"
      />
    </v-layout>
    <v-layout row>
      <generic-section 
        :title="joinBetaTitle"
        :subtitle="betaDescriptionText"
        :bodytext="betaPageContent"
      />
    </v-layout>

    <section class="wrapper generic meeting">
      <div class="inner">
        <header 
          class="major special meeting"
        >
          <h1>Book a tour of Studio Beta</h1>
        </header>
        <calendly
          url="https://calendly.com/blivande/blivande-tour" 
        />
      </div>
    </section>

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
import Calendly from '~/components/Calendly.vue'

export default {
  components: {
    PageBanner,
    VueMarkdown,
    FrontPageSectionWhite,
    GenericSection,
    FrontPageFooter,
    Calendly
  },
  head() {
    return {
      title: 'House Blivande – Studio Beta',
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
        }
      ]
    }
  },
  async asyncData({ params }) {
    let blivande_content = await axios.get(
      'https://participio-api.herokuapp.com/discourse/blivande/frontpage'
    )
    let pagebanner = 'taubanner'
    let betaSymbol = 'sbsymbol.png'
    let betaDescriptionText = blivande_content['data']['9180']
    let betaFlexDesk = blivande_content['data']['9397']
    let betaFixedDesk = blivande_content['data']['9398']
    let betaMakers = blivande_content['data']['9401']
    let betaPageContent = blivande_content['data']['9400']
    let tauPageContent = blivande_content['data']['9199']
    let joinBetaTitle = 'Join Beta'
    let betaSections = [
      {
        title: 'Flexible desk membership',
        text: betaFlexDesk,
        image: 'blivandeblue2-square.jpg',
        id: 1
      },
      {
        title: 'Fixed desk membership',
        text: betaFixedDesk,
        image: 'blivandefixed-square.jpg',
        id: 2
      },
      {
        title: 'Artists & Makers',
        text: betaMakers,
        image: 'tau-square.jpg',
        link: '/tau',
        button: 'More about Tau',
        id: 3
      }
    ]

    return {
      pagebanner,
      betaSymbol,
      betaDescriptionText,
      betaFlexDesk,
      betaFixedDesk,
      betaMakers,
      betaPageContent,
      tauPageContent,
      betaSections,
      joinBetaTitle
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
@import url('../static/css/misc.css');
</style>
