<template>
  <div>
    <v-layout row>
      <banner 
        :users="users" 
      />
    </v-layout>
    <v-layout row>
      <front-page-section-white 
        :sections="betaAndTauSections"
        :title="mainTitle"
        :text="blivandeDescriptionText"
      />
    </v-layout>
    <v-layout row>
      <front-page-section-background
        :features="features"
        :title="featuresTitle"
        :text="featuresText"
        :image="featuresImage"
      />
    </v-layout>
    <v-layout row>
      <front-page-section-white 
        :sections="footerSections"
        :title="footerTitle"
        :text="footerText"
      />
    </v-layout>
    <v-layout row>
      <v-flex xs1 />
      <v-flex xs10>
        <ul class="actions special center">
          <li>
            <a 
              href="/contact" 
              target="_top"
              class="button primary wide"
            >
              Talk to Blivande
            </a>
          </li>
        </ul>
      </v-flex>
      <v-flex xs1 />
    </v-layout>
    <v-layout row>
      <front-page-footer />
    </v-layout>
  </div>
</template>

<script>
import axios from 'axios'
import countTo from 'vue-count-to'
import Vuex from 'vuex'

import Hero from '~/components/Hero.vue'
import Banner from '~/components/Banner.vue'
import FrontPageSectionWhite from '~/components/FrontpageSectionWhite.vue'
import FrontPageSectionBackground from '~/components/FrontpageSectionBackground.vue'
import FrontPageFooter from '~/components/FrontpageFooter.vue'

export default {
  components: {
    Hero,
    Banner,
    FrontPageSectionWhite,
    FrontPageSectionBackground,
    FrontPageFooter,
    countTo
  },
  head() {
    return {
      title: 'House Blivande',
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
          hid: 'image',
          name: 'image',
          content: 'http://www.blivande.com/blivande.jpg'
        }
      ]
    }
  },
  async asyncData({ params }) {
    function randomList(rand) {
      return rand.sort(function() {
        return 0.5 - Math.random()
      })
    }
    let blivande_topics = await axios.get(
      'https://participio-api.herokuapp.com/discourse/blivande'
    )
    let blivande_presentations = await axios.get(
      'https://participio-api.herokuapp.com/discourse/blivande/presentations'
    )
    let users = Object.keys(blivande_presentations.data).map(
      i => blivande_presentations.data[i]
    )
    let blivande_content = await axios.get(
      'https://participio-api.herokuapp.com/discourse/blivande/frontpage'
    )
    let blivandeDescriptionText = blivande_content['data']['9176']
    let betaDescriptionText = blivande_content['data']['9180']
    let tauDescriptionText = blivande_content['data']['9179']
    let nodeDescriptionText = blivande_content['data']['9181']
    let eventDescriptionText = blivande_content['data']['9182']
    let footerText = blivande_content['data']['9393']
    let edgerydersDescriptionText = blivande_content['data']['9392']
    let transformaDescriptionText = blivande_content['data']['9391']
    let whatElseDescriptionText = blivande_content['data']['9394']
    let betaPageContent = blivande_content['data']['9290']
    let tauPageContent = blivande_content['data']['9199']
    let mainTitle = 'House Blivande'
    let betaAndTauSections = [
      {
        title: 'Studio Beta',
        text: betaDescriptionText,
        image: 'blivandebeta-square1.jpg',
        logo: 'studiobeta.png',
        link: '/beta',
        button: 'More about Beta',
        id: 1
      },
      {
        title: 'Studio Tau',
        text: tauDescriptionText,
        image: 'tau-square.jpg',
        logo: 'studiotau.png',
        link: '/tau',
        button: 'More about Tau',
        id: 2
      }
    ]
    let featuresTitle = 'What else is becoming?'
    let featuresText = whatElseDescriptionText
    let featuresImage = 'blivandemeeting-square.jpg'
    let features = {
      tltitle: 'The Node',
      tltext: nodeDescriptionText,
      tllogo: 'node.png',
      tllink: 'https://www.noden.community/',
      trtitle: 'Blivande Events',
      trtext: eventDescriptionText,
      trlogo: 'event.png',
      trlink: '#',
      bltitle: 'Transforma',
      bltext: transformaDescriptionText,
      bllogo: 'transforma.png',
      bllink: '/tau',
      brtitle: 'Edgeryders',
      brtext: edgerydersDescriptionText,
      brlogo: 'edgeryders.png',
      brlink: 'https://edgeryders.eu/'
    }
    let footerTitle = 'Join us'
    let footerSections = []

    return {
      users,
      blivandeDescriptionText,
      tauDescriptionText,
      nodeDescriptionText,
      edgerydersDescriptionText,
      transformaDescriptionText,
      whatElseDescriptionText,
      betaPageContent,
      tauPageContent,
      mainTitle,
      betaAndTauSections,
      featuresTitle,
      featuresText,
      featuresImage,
      features,
      footerTitle,
      footerText,
      footerSections
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
