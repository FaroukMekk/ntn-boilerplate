<template>
  <div class="main text-center flex flex-col items-center justify-center">
    <!-- <logo /> -->
    <h1 class="title">WiSkillz Conseil</h1>
    <h2 class="subtitle"></h2>
    <ul v-for="(blogPost, index) in blogPosts" :key="index" class="articles">
      <nuxt-link :to="`blog/${blogPost.slug}`" class="article article--clickable">
        <div class="flex justify-between align-baseline">
          <h3 class="article-title">{{ blogPost.title }}</h3>
          <h6
            v-if="blogPost.date"
            class="inline-block py-1 px-2 bg-accent text-white font-medium rounded-sm dark:bg-accent whitespace-no-wrap"
          >
            {{ formatDate(blogPost.date) }}
          </h6>
        </div>
        <div class="mt-4 mb-2">
          <p class="inline">{{ blogPost.description }}</p>
        </div>
      </nuxt-link>
    </ul>
  </div>
</template>

<script>
// import Logo from '~/components/Logo.vue'

export default {
  // components: {
  //   Logo
  // },
  computed: {
    blogPosts() {
      return this.$store.state.blogPosts
    },
  },
  methods: {
    formatDate(dateString) {
      const date = new Date(dateString)
      return date.toLocaleDateString(process.env.lang) || ''
    },
  },
  head() {
    return {
      script: [{ src: 'https://identity.netlify.com/v1/netlify-identity-widget.js' }],
    }
  },
}
</script>
