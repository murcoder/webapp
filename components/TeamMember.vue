<template>
  <div
    v-editable="blok"
    class="member-page"
    @touchstart="touch"
  >
    <a
      ref="hidden"
      href="#"
      display="none"
    />
    <div class="header">
      <div class="image">
        <img
          v-if="blok.image"
          class="picture"
          :src="$resizeImage(blok.image, '700x700')"
          :alt="blok.name + ', ' + blok.title"
        >
        <img
          v-if="blok.image_alt"
          class="picture image-alt"
          :src="$resizeImage(blok.image_alt, '700x700')"
          :alt="blok.name + ', ' + blok.title"
        >
      </div>
      <div class="info">
        <div class="short-info">
          <div class="name-contact">
            <div class="name">
              {{ blok.name }}
            </div>
            <div class="contact-options">
              <a
                v-if="blok.email"
                class="option email"
                :href="'mailto:'+blok.email"
              >
                <img
                  class="icon"
                  src="~/assets/img/icons/envelope.svg"
                  alt=""
                >
                <div class="text">{{ blok.email }}</div>
              </a>
            </div>
          </div>
          <div class="title">
            {{ blok.title }}
          </div>
        </div>
        <div class="short-description">
          {{ blok.short_description }}
        </div>
      </div>
    </div>
    <div class="short-description-mobile">
      {{ blok.short_description }}
    </div>
    <div class="body">
      <div class="future-slogan">
        <div class="first">
          {{ $t('theFuture') }}
        </div>
        <div class="second">
          {{ $t('belongs') }}{{ blok.future }}<span v-if="!blok.future"> {{ $t('toUsAll') }}</span>
        </div>
      </div>
      <div class="description">
        <markdown :value="blok.description" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ['blok'],
  methods: {
    touch (e) {
      if (e.target.localName !== 'img') {
        this.$refs.hidden.focus()
      }
    }
  }
}
</script>

<style lang="scss">
@import '/assets/scss/styles.scss';

.member-page {
  @include margin-page-wide();
  min-height: 150px;
  .header {
    display: flex;
    .image {
      position: relative;
      flex-grow: 1;
      width: 46%;
      margin-right: 2%;
      text-align: right;
      &:hover {
        .image-alt {
          display: inline;
        }
      }
      .image-alt {
        display: none;
        position: absolute;
        top: 0;
        right: 0;
        z-index: 99;
      }
      .picture {
        width: 100%;
        max-width: 70%;
      }
    }
    .info {
      display: flex;
      flex-direction: column;
      flex-grow: 1;
      width: 50%;
      margin-left: 2%;
      .short-info {
        display: flex;
        flex-grow: 1;
        flex-direction: column;
        justify-content: flex-end;
        .name-contact {
          padding-bottom: 1rem;
          border-bottom: .4rem solid black;
          margin-top: 1rem;
          margin-bottom: 1rem;
          display: flex;
          flex-direction: column-reverse;
          align-items: flex-end;
          justify-content: space-between;
          .name {
            font-family: $font-secondary;
            font-size: 4rem;
            text-transform: uppercase;
            line-height: 1.2;
          }
          .contact-options {
            font-size: .9rem;
            margin-bottom: .8rem;
            display: flex;
            flex-direction: column;
            .option {
              display: flex;
              flex-direction: row-reverse;
              align-items: center;
              padding: .4em 0;
              color: inherit;
              text-decoration: none;
              .icon {
                width: 18px;
                margin-left: .5em;
              }
              .text {
              }
            }
          }
        }
        .title {
          font-family: $font-mono;
          font-size: 1rem;
          margin-bottom: 2em;
        }
      }
      .short-description {
        line-height: 1.5;
        @include media-breakpoint-up(xl) {
          width: 80%;
        }
        font-size: 1rem;
      }
    }
  }
  .short-description-mobile {
    display: none;
  }
  .body {
    padding: 100px 0;
    .future-slogan {
      transform: rotate(-5deg);
      font-size: 2rem;
      @include media-breakpoint-down(sm) {
        font-size: 1.4rem;
      }
      width: 40%;
      min-width: 15em;
      margin-left: 12%;
      margin-bottom: 9%;
      .first {
        font-weight: bold;
        text-transform: uppercase;
        margin-bottom: .2em;
      }
      .second {
        font-family: $font-secondary;
      }
    }
    .description {
      margin: 0 20% 0 30%;
    }
  }

  @include media-breakpoint-down(lg) {
    .header {
      .info {
        .short-info {
          justify-content: flex-start;
          .name-contact {
            flex-direction: column-reverse;
            .name {
              align-self: flex-start;
              font-size: 2.5em;
            }
          }
        }
        .short-description {
          display: none;
        }
      }
    }
    .short-description-mobile {
      display: flex;
      margin: 1em 0;
      line-height: 1.4;
      font-size: 1rem;
    }
  }

  @include media-breakpoint-down(sm) {
    .header {
      flex-direction: column;
      .info {
        width: 100%;
        margin: 0;
        .short-info {
          .name-contact {
            .name {
            }
          }
        }
        .short-description {
        }
      }
      .image {
        width: 400px;
        max-width: 100%;
      }
    }
    .short-description-mobile {
    }
    .body {
      .future-slogan {
        margin-left: 2%;
        margin-bottom: 20%;
      }
      .description {
        margin: 0;
      }
    }
  }

  @include media-breakpoint-down(xs) {
    .header {
      .info {
        .short-info {
          .name-contact {
            .name {
              font-size: 2em;
            }
          }
        }
      }
    }
  }
}
</style>
