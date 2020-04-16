<template>
  <div>
    <img src="~assets/logo.svg">
    <nav class="menu">
      <ShokuSection
        :animate="animate"
        :section="section" v-for="section in sections"
        in-viewport-root-margin="-40% 0%"
      ></ShokuSection>
    </nav>
    <img src="~assets/logo.svg">
  </div>
</template>
<script>
export default {
  props: {
    animate: {
      type: Boolean,
      default: false
    },
  },
  components: {
    ShokuSection: () => import('~/components/Section.vue')
  },
  data() {
    return {
      sections: [
        {
          title: 'Contact us',
          description: '<div style="text-align: center"><p>To be added to our waitlist, send us a Dm on instagram</p></div>'
        },
        {
          title: 'Suppliers',
          description: `
              <p>
                One of our core values at Shokupan is transparency, we believe everyone should know how and where their food is being produced. We are very proud to work with our suppliers and their products.
              </p>
              <p>
                We use : St David Dairy for their Milk and Cultured butter, their dairy is made less than 5Km away from where we bake !
              </p>
              <p>
               Wholegrain Milling for their organic flour
              </p>
              <p>
               Mount zero for their Pink lake salt ( did you know that it was harvested in partnership with indigenous workers ? This alone should be the reason to buy Mount Zero Salt !
Terra madre for their organic cane sugar
              </p>
              <p>
We are currently looking at some plant based packaging to preserve the shelf life of your Shokupan.
 </p>
            `
        },
        {
          title: 'Story',
          description: `
          <p>Shokupans means “eating bread” in Japanese. It is characterised as a light and fluffy sandwich bread traditionally made from yeast. Only a handful of homemade bakers have succeeded at making a sourdough Shokupan, making our loaf the first Sourdough Shokupan available on the market. The dough is slowly mixed, long fermented and made without any nasty preservative. We take pride in sourcing the best ingredients available and feeding our community in the most healthy and sustainable way.
          </p>
          <p>Shokupan was born during the 2020 lockdown, after I received a wine delivery from ZigZag wines,  I realised how nice it was to actually meet the winemaker. Not only it was important to me to get to meet my customers, it was also a way to build a community centred around good healthy food.</p>
          `
        }
      ]
    }
  },
}
</script>
<style scoped>
img {
  margin: 25vh auto;
  max-width: 100%;
}
</style>
