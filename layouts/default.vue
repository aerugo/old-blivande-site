<template>
  <v-app>
    <section 
      id="header" 
      class="alt"
    >

      <nav id="nav">
        <ul>
          <li 
            :class="{ current: $nuxt.$route.path == '/' }"
          >
            <a href="/">Home</a>
          </li>
          <li
            :class="{ current: $nuxt.$route.path == '/beta' }"
          >
            <a href="beta">Beta</a>
          </li>
          <li
            :class="{ current: $nuxt.$route.path == '/tau' }"
          >
            <a href="tau">Tau</a>
          </li>
          <li
            :class="{ current: $nuxt.$route.path == '/members' }"
          >
            <a href="members">Members</a>
          </li>
          <li
            :class="{ current: $nuxt.$route.path == '/contact' }"
          >
            <a href="contact">Contact</a>
          </li>
        </ul>
      </nav>
    </section>

    <nuxt />

  </v-app>
</template>

<script>
export default {}
</script>
