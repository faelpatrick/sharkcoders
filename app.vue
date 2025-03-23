<template>
  <v-app class="d-flex flex-column fill-height">
    <NuxtPage class="flex-grow-1" />
    
    <v-footer
      color="black"
      class="text-white d-flex justify-center py-4"
      app
    >
      <v-btn
        icon
        v-for="rede in redes"
        :key="rede.nome"
        :href="rede.link"
        target="_blank"
        variant="plain"
        class="mx-2"
      >
        <v-icon :icon="rede.icone" />
      </v-btn>
    </v-footer>
  </v-app>
</template>
<script setup>
const redes = [
  { nome: 'Instagram', icone: 'mdi-instagram', link: 'https://www.instagram.com/faelpatricks/' },
  { nome: 'LinkedIn', icone: 'mdi-linkedin', link: 'https://www.linkedin.com/in/faelpatrick/' },
  { nome: 'GitHub', icone: 'mdi-github', link: 'https://github.com/faelpatrick' },
  { nome: 'YouTube', icone: 'mdi-youtube', link: 'https://www.youtube.com/@faelpatrick' },
  { nome: 'Linktree', icone: 'mdi-link-variant', link: 'https://linktr.ee/faelpatrick' },
]
</script>

<style>
html, body, #__nuxt {
  height: 100%;
  margin: 0;
}
</style>