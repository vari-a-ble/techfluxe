<template>
  <div>
    <v-layout row class="pt-0 mt-0">
      <v-flex xs12 md9>
        <v-container fluid>
          <!--Start Carousel-->
          <v-card flat>
            <v-carousel hide-controls class="elevation-0" height="400">
              <v-carousel-item
                v-for="(item,i) in items" :key="i">
                <v-img :src="item.src" height="400">
                  <template v-slot:placeholder>
                    <v-layout fill-height align-center justify-center  ma-0 >
                      <v-progress-circular indeterminate color="cyan lighten-4"></v-progress-circular>
                    </v-layout>
                  </template>
                  <v-container fill-height fluid style="background-color: rgba(0, 0, 0, 0.5);">
                    <v-layout align-center justify-center column fill-height>
                      <v-flex xs12>
                        <span> <v-icon right class="gradient-text">language</v-icon> </span> <span class="white--text pl-2 subheading">Global news</span>
                        <div class="border-left"> <div class="px-3"><span class="display-1 font-weight-black" style="color: rgba(255, 255, 255, 0.9);"> {{ item.title }} </span></div> </div>
                      </v-flex>
                    </v-layout>
                  </v-container>
                </v-img>
              </v-carousel-item>
            </v-carousel>
          </v-card>
          <!--End Carousel-->

          <!--Start Latest Feeds-->
          <div class="pt-5 pb-2 border-bottom">
            <Indicator colour="#EE3477" size="15"/>
            <span class="title font-weight-bold ml-1">Latest News</span>
          </div>
          <Feeds/>
          <!--Start Latest Feeds-->
        </v-container>
      </v-flex>

      <v-flex md3 class="hidden-sm-and-down">
        <Events/>
        <v-divider class="my-5" />
        <Newsletter/>
      </v-flex>
    </v-layout>
  </div>
</template>

<script>
import Indicator from '@/components/Indicator'
import Events from '@/components/Events'
import Newsletter from '@/components/Newsletter'
import Feeds from '@/components/Feeds'
import { mapGetters } from 'vuex'

export default {
  head() {
    return {
      title: 'TechFluxe | Technology News',
      meta: [
        { name: 'keywords', content: 'TechFluxe, tech news, technology news, startup news, tech news in africa, tech startup news, best tech news in africa' },
        { hid: 'description', name: 'description', content: 'TechFluxe is a leading technology media in Africa, dedicated to obsessively profiling startups, reviewing new Internet products, and breaking tech news.' },
        { property: 'og:site_name', content: 'TechFluxe' },
        { property: 'og:og:site', content: 'tecfluxe.com' },
        { property: 'og:title', content: '' },
        { property: 'og:description', content: 'TechFluxe is a leading technology media in Africa, dedicated to obsessively profiling startups, reviewing new Internet products, and breaking tech news.' },
        { property: 'og:image', content: '/img/feeds/f1.png' },
        { property: 'og:url', content: 'https://techfluxe.netlify.com/' },
        { property: 'og:type', content: 'website' },
      ]
    }
  },
  components: {
    Indicator,
    Events,
    Newsletter,
    Feeds
  },
  computed: mapGetters({
    items: 'load',
  })
}
</script>
<style scoped>
h5{
  font-size: 4vw;
  line-height: 1.2;
}
.rad{
  border-radius: 100%;
}
.border{
  border-top: 2px #EEFCFF solid;
}

.border-bottom{
  border-bottom: 2px #F0F0F0 solid;
}

.border-thin{
  border-top: 2px #EEFCFF solid;
}
.border-left{
border-left: 5px solid #3cd1c2;
}
</style>

