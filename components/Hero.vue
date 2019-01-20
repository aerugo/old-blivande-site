<template>

  <v-container
    fluid
    grid-list-xs
  >

    <v-layout 
      row 
      wrap
    >

      <v-flex 
        md1
      />

      <v-flex 
        xs12 
        sm12
        md5
        class="logo"
      >
        <v-img 
          src="blivande.png" 
          contain
          position="50%"
          max-height="280"
        />
      </v-flex>

      <v-flex 
        xs12
        md4
      >
        <v-layout 
          row 
          wrap
        >
          <v-flex 
            xs1 
            sm2
            md1
          />
          <v-flex 
            xs10
            sm8
            md12
            class="members"
          > 
            <h2 class="hero">ALWAYS BECOMING</h2>  
            <a 
              v-for="user in users"
              :key="user.id"
              :href="'https://edgeryders.eu/u/' + user.username"
            >
              <img
                :src="user.avatar_template.replace('{size}', '50')"
                class="members"
              > 
            </a>
          </v-flex>
          <v-flex 
            xs1
            sm2
            md2
          />
        </v-layout>
      </v-flex>
    </v-layout>

  </v-container>

</template>

<script>
export default {
  props: {
    users: {
      type: Array,
      required: true
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Open+Sans');

.members {
  margin-bottom: 15px;
}

.members img {
  border-radius: 20px;
  width: 30px !important;
  height: 30px !important;
  margin: 9px 9px 0px 0px !important;
  outline: 0;
}
</style>
