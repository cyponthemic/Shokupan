<template>
  <div class="screen" id="fold-effect">
    <div class="wrapper-3d">
      <div class="fold fold-top">
        <div class="fold-align">
          <div class="fold-content">
            <ContentFold/>
          </div>
        </div>
      </div>
      <div class="fold fold-center" id="center-fold">
        <div class="fold-align">
          <div class="fold-content" id="center-content">
            <ContentFold/>
          </div>
        </div>
      </div>
      <div class="fold fold-bottom">
        <div class="fold-align">
          <div class="fold-content">
            <ContentFold/>
          </div>
        </div>
      </div>
    </div>
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
  },
  mounted() {
    console.log("top");

    let centerContent = document.getElementById("center-content");
    let centerFold = document.getElementById("center-fold");

    let foldsContent = Array.from(
      document.getElementsByClassName("fold-content")
    );

    let targetScroll = -(
      document.documentElement.scrollTop || document.body.scrollTop
    );
    let currentScroll = targetScroll;
    let tick = () => {
      let overflowHeight = centerContent.clientHeight - centerFold.clientHeight;

      document.body.style.height = overflowHeight + window.innerHeight + "px";

      targetScroll = -(
        document.documentElement.scrollTop || document.body.scrollTop
      );
      currentScroll += (targetScroll - currentScroll) * 0.1;
      foldsContent.forEach(content => {
        content.style.transform = `translateY(${currentScroll}px)`;
      });
      requestAnimationFrame(tick);
    };
    tick();
  }
};
</script>
