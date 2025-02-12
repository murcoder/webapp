<template>
  <nuxt-link :to="'/' + blok.full_slug">
    <div
        class="workshop-list-item content-card"
        :class="{ slim: slim }"
    >
      <div class="image">
        <img
            :src="$resizeImage(content.image, '380x280')"
            alt=""
        >
      </div>
      <div class="body">
        <div class="category">
          <div v-if="content.category === 'training'">
            <span>{{ $t('instructions') }}</span>
          </div>
          <div v-if="content.category === 'event'">
            <span>{{ $t('event') }}</span>
          </div>
          <div v-if="content.category === 'meetup'">
            <span>{{ $t('meetup') }}</span>
          </div>
          <div v-if="content.category === 'workshop'">
            <span>{{ $t('workshops') }}</span>
          </div>
        </div>
        <div class="title">
          {{ content.title }}
        </div>
        <div
            v-if="!slim"
            class="teaser"
        >
          {{ content.teaser }}
        </div>
        <div class="trainer">
          {{ content.trainer }}
        </div>
        <div class="workshop-dates">
          <div
              v-for="(d) in dates" :key="d.id"
              class="workshop-date"
              :class="{ soldOut: d.content.sold_out }"
          >
            <div
                v-if="!slim || i === 0"
                class="info-row"
            >
              <div class="info-block">
                <div class="col info">
                  <icon name="calendar" />
                  {{ d.content.starttime | date }}
                  <div v-if="d.content.starttime2">
                    <br>
                    <font-awesome-icon class="grey" icon="plus"/>
                    {{ d.content.starttime2 | date }}
                  </div>
                </div>
                <div class="col info">
                  <icon name="clock" />
                  <span>{{ d.content.starttime | time }}</span>
                  <span v-if="d.content.endtime"> bis {{ d.content.endtime | time }}</span>
                  <span>Uhr</span>
                  <div v-if="d.content.starttime2">
                    <br>
                    <icon name="clock" />
                    <span>{{ d.content.starttime2 | time }}</span>
                    <span v-if="d.content.endtime2"> bis {{ d.content.endtime2 | time }}</span>
                    <span>Uhr</span>
                  </div>
                </div>
              </div>
              <div class="info-block">
                <div
                    v-if="d.content.members_only"
                    class="col"
                >
                  <icon name="user" />
                  <span>{{ $t('membersOnly') }}</span>
                </div>
                <div
                    v-if="d.content.sold_out"
                    class="col soldOut"
                >
                  <span>{{ $t('soldOut') }}</span>
                </div>
              </div>
              <!-- <div class="info-block">
                <div class="col" v-if="content.pax">
                  <icon name="user" />
                  <span>{{content.pax}}</span>
                </div>
              </div>-->
            </div>
          </div>
        </div>
        <div class="icon">
          <icon :name="content.category" />
        </div>
      </div>
    </div>
  </nuxt-link>
</template>

<script>
export default {
  props: ['blok', 'slim'],
  computed: {
    dates () {
      return this.blok.dates
    },
    content () {
      return this.blok.content
    },
    linktext () {
      return 'Mehr Infos'
    }
  },
  mounted () {
    // console.log(this.blok.uuid);
  }
}
</script>

<style lang="scss" scoped>
@import '/assets/scss/styles.scss';
.workshop-list-item {
  color: #000;
  display: flex;
  margin-bottom: 25px;
  justify-content: center;
  &.slim {
    margin-bottom: 0;
    .image {
      max-width: 10%;
    }
    .body {
      padding: 0.9em;
    }
  }
  @include media-breakpoint-down(sm) {
    flex-direction: column;
    margin-right: 4%;
  }
  .image {
    @include media-breakpoint-down(sm) {
      overflow: hidden;
      margin-left: 2%;
    }
    img {
      @include media-breakpoint-down(sm) {
        margin: -2vh 0;
      }
      @include media-breakpoint-down(xs) {
        width: 100%;
      }
      max-height: calc(40vh - 65px);
      max-width: 100%;
      display: block;
    }
  }
  br {
    display: block;
    margin: 4px;
  }

  .body {
    position: relative;
    flex: 2;
    display: flex;
    flex-direction: column;
    background-color: #FFF;
    padding: 1.8rem;
    @include media-breakpoint-down(sm) {
      margin-left: 2%;
    }
    .icon {
      position: absolute;
      top: 0;
      right: 0;
      width: 120px;
      padding: 10px;
      svg {
        fill: #EEE;
      }
    }
    .title {
      position: relative;
      z-index: 1;
      font-family: $font-secondary;
      font-size: 2rem;
      margin-bottom: .4rem;
      @include media-breakpoint-down(sm) {
        font-size: 1.1em;
        font-weight: bold;
        margin-top:4px;
      }
    }
    .category {
      position: relative;
      z-index: 1;
      font-family: $font-mono;
      font-size: 0.9rem;
      letter-spacing: .1em;
      margin-bottom: .3rem;
      text-transform: uppercase;
      color: $color-orange;
      svg {
        fill: $color-orange;
        height: 1em;
        width: 1em;
      }
    }
    .teaser {
      position: relative;
      z-index: 1;
      flex: 1;
      font-family: $font-mono;
      line-height: 1.6;
      font-size: 0.9rem;
      width: 85%;
      @include media-breakpoint-down(sm) {
        width: 100%;
      }
    }
    .trainer {
      line-height: 1.6;
      font-family: $font-mono;
      font-size: 0.9rem;
      font-weight: bold;
      margin: .4em 0;
    }
    .linktext {
      text-transform: uppercase;
      color: $color-blue;
      margin: 1em 0 .5em;
      display: flex;
      align-items: center;
      .link-arrow {
        border-top: $color-blue 1px solid;
        width: 1em;
        position: relative;
        margin-right: .3em;
        &:before {
          position: absolute;
          right: 0;
          content: "";
          border-top: $color-blue 1px solid;
          border-right: $color-blue 1px solid;
          transform: rotateZ(45deg);
          transform-origin: top right;
          height: .3em;
          width: .3em;
          margin-top: -.5px;
        }
      }
    }
  }
}
.workshop-dates {
  margin-top: 20px;
  .workshop-date {
    &:nth-child(even) {
      background-color: rgba(242, 243, 238,0.9);
    }
    margin: 5px;
    @include media-breakpoint-down(xs) {
      border: .11em solid #f2f3ee;
      padding:7px;
    }
    &.soldOut {
      color: #666;
      fill: #666;
      .col {
        &.info {
          text-decoration: line-through;
        }
      }
    }

    .info-row {
      @include media-breakpoint-down(md) {
        flex-direction: column;
      }
      line-height: 1.6;
      font-family: $font-mono;
      font-size: 0.9rem;
      font-weight: bold;
      margin: -8px;
      display: flex;
      .info-block {
        flex: 1;
        flex-direction: row;
        display: flex;
      }
      .col {
        padding: 8px;
        &.soldOut {
          color: $color-orange;
          text-transform: uppercase;
        }
      }

      svg {
        height: 1em;
        width: 1em;
      }
    }
  }
}
</style>
