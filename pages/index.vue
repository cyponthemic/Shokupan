<template>
  <div>
    <ContentFold :animate="true"/>
  </div>
</template>

<script>
export default {
  head() {
    let product = this.product
    return {
      title: `Shokupan | Coming Soon`,
      meta: [
        {
          hid: `description`,
          name: 'description',
          content: 'Naturally Fermented Sandwich Bread'
        },
        {
          hid: `keywords`,
          name: 'keywords',
          keywords: 'Shokupan'
        },
        {
          hid: `og:title`,
          property: 'og:title',
          content: 'Shokupan'

        },
        {
          hid: `og:url`,
          property: 'og:url',
          content: process.env.URL
        },
        {
          hid: `og:image`,
          property: 'og:image',
          content: process.env.URL + '/shokupan.png'
        },
        {
          hid: `og:description`,
          property: 'og:description',
          content: 'Naturally Fermented Sandwich Bread | Coming soon'
        }
      ]
    }
  },
  components: {
    ContentFold: () => import("~/components/Content")
  }
};
</script>
