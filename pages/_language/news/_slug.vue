<template>
  <div class="body">
    <div v-if="item">
      <div class="header">
        <div class="header-image" :style="{ 'background-image': 'url(' + item.content.image + ')' }"></div>
        <div class="header-title">
          <h4>
            <vue-markdown>{{ item.content.title }}</vue-markdown>
          </h4>
          <voting-button v-if="item.content.voting" is-on-detail="true" :uuid="item.uuid"></voting-button>
        </div>
      </div>
      <div class="blogFeed-detail">
        <div class="left-content">
          <div class="social-media-link">
            <a v-if="item.content.link.url != ''" :href="item.content.link.url" class="info-block"><img
                v-if="item.content.source.length != 0" class="source-img"
                :src="`/icons/${item.content.source}.png`"></a>
            <span class="info-block">{{ item.content.datetime | date }}</span>
          </div>
        </div>
        <div class="right-content">
          <div class="teaser">
            {{ item.content.text }}
          </div>
          <br>
          <div v-if="item.content.materials">
            <div> {{ $t('materialsUsed') }}</div>
            <vue-markdown>{{ item.content.materials }}</vue-markdown>
          </div>
          <div class="spacer"></div>
          <div class="video" v-if="item.content.video">
            <iframe :src="item.content.video" title="YouTube video player" frameborder="0"
                    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
                    allowfullscreen></iframe>
          </div>
        </div>
      </div>
      <div class="image-container" v-if="item.content.images && item.content.images.length != 0">
        <div class="name" v-if="item.content.images && item.content.images.length != 0">{{ $t('steps') }}</div>
        <div class="images">
          <image-slideshow :blok="images"></image-slideshow>
        </div>
      </div>
      <div class="teaser">
        <div :key="i" v-for="i in item.content.contentBloks">
                          <span v-if="item.content.contentBloks">
                            <span v-if="i.text" class="teaser"><vue-markdown>{{ i.text }}</vue-markdown></span>
                          </span>
        </div>
      </div>
      <div class="machine" v-if="machine != null && machine.length != 0">
        <div class="name">  {{ $t('machinesForProject') }}</div>
        <div class="display-machines">
          <machine-preview
              v-for="m in machine"
              :id="m"
              :key="m"
          />
        </div>
      </div>
      <!--              <div class="blogFeed-detail">
                      <div :key="i" v-for="i in item.content.contentBloks" class="right-content">
                          <span v-if="item.content.contentBloks">
                            <span v-if="i.text" class="content-text"><vue-markdown>{{ i.text }}</vue-markdown></span>
                            <span v-if="i.image" class="img"><img :src="$resizeImage(i.image, '600x0')" alt=""/></span>
                          </span>
                      </div>
                    </div>-->
      <div class="maker" v-if="(person != null && person.length !=0) || (member != null && member.length !=0)">
        <div class="name"> {{ $t('personBehindTheProject') }}</div>
        <div class="display-makers">
          <maker-preview
              v-for="p in person"
              :id="p"
              :key="p"
          />
          <maker-preview
              v-for="p in member"
              :id="p"
              :key="p"
          />
        </div>
      </div>
      <!--        <div v-if="item.content.links && item.content.links.length != 0">
                <links-slideshow :blok="links"></links-slideshow>
              </div>-->
    </div><div class="foot-spacer"></div>
    </div>
    <!--      <div v-else>
            <div class="header">
              <div class="header-image" :style="{ 'background-image': 'url(' + item.image + ')' }"></div>
              <div class="header-title">
                <h4>{{ item.title }}</h4>
                <voting-button v-if="item.content.voting" is-on-detail="true" :uuid="item.uuid"></voting-button>

              </div>
            </div>
            <div class="blogFeed-detail">
              <div class="left-content">
                <span class="info-block">{{ item.datetime | date }}</span>
                {{ item }}
                &lt;!&ndash;<a v-if="item.link.url && item.link.url != ''" :href="item.link.url" class="info-block"><img v-if="item.source.length != 0" class="source-img" :src="`/icons/${item.source}.png`"></a>&ndash;&gt;
              </div>
              <div class="right-content">
                <div class="teaser">
                  {{ item.teaser }}
                </div>
                <div>
                  {{ item.text }}
                </div>

              </div>
            </div>
            <div class="images" v-if="item.images && item.images.length != 0">
              <image-slideshow :blok="images"></image-slideshow>
            </div>

            </div>
            <div v-if="item.links && item.links.length != 0">
              <links-slideshow :blok="links"></links-slideshow>
            </div>
      </div>-->
</template>

<script>
import storyblokLivePreview from '@/mixins/storyblokLivePreview'
import VotingButton from '../../../components/VotingButton'
import VueMarkdown from 'vue-markdown'

export default {
  components: { VotingButton, VueMarkdown },
  props: ['blok'],
  mixins: [storyblokLivePreview],
  created () {
    this.$store.app.$storyapi.get(`cdn/stories/${this.id}`, {
      find_by: 'uuid'
    }).then((res) => {
      this.story = res.data.story
    }).catch((e) => {
    })
  },
  data () {
    return {
      // images: [],
      reload: null,
      loading: false,
      sources: [
        { name: 'magazin3', key: 'm3', selected: false },
        { name: 'youtube', key: 'yt', selected: false },
        { name: 'facebook', key: 'fb', selected: false },
        { name: 'twitter', key: 'tw', selected: false },
        { name: 'instagram', key: 'ig', selected: false }
      ],
      item: null
    }
  },
  asyncData (context) {
    return context.store.dispatch('loadNewsItem', context.route.params.slug).then(data => {
      return { item: data.story }
    })
  },
  computed: {
    route () {
      return this.$route.fullPath
    },
    images () {
      return {
        items: this.item.content.images
      }
    },
    links () {
      return {
        items: this.item.content.links
      }
    },
    content () {
      return {
        content: this.item.content.contentBloks.text
      }
    },
    machine () {
      return this.item.content.machine
    },
    person () {
      return this.item.content.person
    },
    member () {
      if (this.item.content.member != null) {
        return this.item.content.member
      }
      return null
    }
  }
}
</script>

<style lang="scss" scoped>
@import '/assets/scss/styles.scss';
.foot-spacer{
  height: 15vh;
  width: 3vw;
}
.teaser {
  font-weight: normal;
  font-family: $font-primary;
  line-height: 1.8;
  font-size: 1.5rem;
  @include media-breakpoint-down(md) {
    line-height: 1.4;
    font-size: 1.2rem;
    margin: 0 0 20px 5%;
    margin-right: 4%;
  }
  @include media-breakpoint-down(xs) {
    margin-left: 6%;

    font-size: 1rem;
  }
}

.body {
  max-width: 1264px;
  width: 100%;
  background: none;
  display: flex;
  justify-content: space-between;
  margin: 0 auto;
  flex-flow: column;
}

.header {
  height: calc(35vh - 64px);
  position: relative;
}

.header-image {
  height: 100%;
  background-size: cover;
  background-position: center;
}

.header-title {
  right: 0;
  bottom: 0;
  background-color: #fff;
  min-width: 50%;
  padding-left: 3vw;
  padding-right: 7vw;
  @include media-breakpoint-up(sm) {
    position: absolute;
  }
  @include media-breakpoint-down(sm) {
    padding: 1px 10px;

  }

  h4 {
    margin: 0;
    font-size: 3rem;
    font-family: Chakra Petch;
    font-weight: 700;
    @include media-breakpoint-down(sm) {
      font-size: 1.6rem;
    }
  }
}

.info-block {
  @include media-breakpoint-down(sm) {
    align-self: baseline;
  }
}

.blogFeed-detail {
  margin-top: 40px;
  color: #000;
  display: flex;
  flex-direction: row;
  flex: 1;
  line-height: normal;
  background: #f2f3ee;;
  font-size: 1.5rem;
  margin-bottom: 7%;
  @include media-breakpoint-down(md) {
    flex-flow: column;
    margin-left: 10%;
  }
  @include media-breakpoint-down(xs) {
    margin-top: 25%;
    font-size: 18px;
  }
  /*  @include margin-page-wide();
    @include media-breakpoint-up(md) {
      margin: 0 100px;
    }
    @include media-breakpoint-down(xs) {
      margin-top: 40px;
    }*/
}

.social-media-link {
  display: flex;
  flex-flow: column;
  justify-content: center;
  width: 15vw;
  @include media-breakpoint-down(md) {
    flex-flow: row;
    width: auto;
    justify-content: flex-start;
  }
}

.left-content {
  margin-left: 2vw;

  & * {
    margin-top: 0.5vh;
    color: $color-secondary-border;
  }

  @include media-breakpoint-up(md) {
    width: 15vw;
  }
  @include media-breakpoint-down(sm) {
    margin-bottom: 20px;
    .source-img {
      width: 70%;
      height: 70%;
    }
  }
}

.name {
  font-size: 2.5rem;
  font-weight: bold;
  padding-top: 3vh;
  padding-left: 4vw;
  font-family: Chakra Petch;
  margin-top: 5vh;
  @include media-breakpoint-down(sm) {
    font-size: 1.9rem;
  }
  @include media-breakpoint-down(xs) {
    font-size: 1.4rem;
  }
}

.image-slideshow {
  padding-left: 5vw;
  padding-right: 5vw;
  margin-top: 3vh;
  @include media-breakpoint-down(xs) {
    padding: 5vw;
  }
}

.right-content {
  flex-direction: column;
  position: relative;
  display: flex;
  width: inherit;
  @include media-breakpoint-down(sm) {
    width: 80vw;
  }

  img {
    @include media-breakpoint-down(sm) {
      width: 100%;
    }
  }

  .spacer {
    height: 4vh;
  }

  .link {
    background-color: $color-orange;
    margin: 2% 0 0 5%;
    text-transform: uppercase;
    @include media-breakpoint-up(md) {
    }
    color: #fff;
    padding: .7em .8em;
    font-weight: 800;
  }

  .content-text {
    padding: 20px 80px;
    @include media-breakpoint-down(sm) {
      padding: 20px 20px;
    }
  }
}

.img {
  display: block;
  width: 20vw;
  @include media-breakpoint-down(sm) {
  }
}

.image-container {
  background: #FFFFFF;
}

.images {
  margin-bottom: 0;
  background: #FFFFFF;
  @include media-breakpoint-down(sm) {
    margin: 4px;
  }
}

.links {
  margin: 40px;
}

.display-machines {
  display: flex;
  flex-flow: row;
  justify-content: center;
  align-items: center;
  margin-top: 2vh;
  margin-bottom: 20vh;
  @include media-breakpoint-down(sm) {
    margin-bottom: 15vh;
  }
  @include media-breakpoint-down(xs) {
    flex-flow: column;
    margin-bottom: 1vh;
  }
}

.display-makers {
  margin-top: 2vh;
  display: flex;
  flex-flow: column;
  @include media-breakpoint-down(sm) {
    display: flex;
    justify-content: center;
  }
}

.video {
  width: inherit;

  & * {
    width: 100%;
    height: 20em;
    @include media-breakpoint-down(sm) {
      height: 35vh;
    }
    @include media-breakpoint-down(xs) {
      height: 25vh;
    }
  }
}
</style>
