<template>
  <div
      v-if="machine"
      v-editable="machine"
      class="machine-page"
  >
    <machine-header :story="story"/>
    <div class="machine-teaser">
      <div class="body">
        <div class="image">
          <img
              :src="$resizeImage(machine.image, '700x0')"
              alt=""
          >
        </div>
        <div class="description text">
          <markdown :value="machine.details"/>
        </div>
      </div>
    </div>
    <div class="body">
      <div class="inner-body">
        <!--
        <div class="description">
          <markdown :value="machine.description"></markdown>
        </div>
        -->
        <div
            v-if="hasUser"
            class="machine-list"
        >
          <div
              :key="m.id"
              v-for="m in machine.machine_status_items"
              class="machine-item"
          >
            <machine-status
                v-if="!singleMachine"
                :id="m.fabmanId"
                class="status"
                :name="m.name"
            />
            <machine-calendar :id="m.fabmanId"/>
          </div>
        </div>
        <div
            v-else
            class="machine-list"
        >
          <div class="machine-list-warning">
            {{ $t( "machineViewRestriction" ) }}
          </div>
        </div>
      </div>
    </div>
    <div class="body">
      <image-slideshow :blok="images"/>
    </div>
    <div
        v-if="machine.links && machine.links.length > 0"
        class="body"
    >
      <h3 class="blue">
        Links
      </h3>
      <ul class="link-list">
        <li
            v-for="(i, index) in machine.links"
            :key="index"
            class="link-item"
        >
          <div class="title">
            {{ i.title }}
          </div>
          <a
              class="url"
              :href="i.url"
              target="_blank"
          >{{ i.url }}</a>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import MachineStatus from '@/components/MachineStatus'
import MachineCalendar from '@/components/MachineCalendar'
import MachineHeader from '@/components/MachineHeader'
import { getMetaTagsForMachine } from '../services/MetaDataService'

export default {
  components: {
    MachineHeader,
    MachineStatus,
    MachineCalendar
  },
  props: ['story'],
  computed: {
    machine () {
      return this.story.content
    },
    tags () {
      return this.story.tag_list
    },
    hasUser () {
      return !!this.$store.state.user
    },
    singleMachine () {
      return this.machine && this.machine.machine_status_items && this.machine.machine_status_items.length === 1
    },
    images () {
      return {
        items: this.machine.images
      }
    }
  },
  head () {
    return getMetaTagsForMachine(this.machine)
  }
}
</script>

<style lang="scss">
@import '/assets/scss/styles.scss';

.machine-page {
  h3 {
    &.blue {
      color: $color-blue;
    }
  }

  .machine-teaser {
    display: flex;
    flex-direction: column;
    justify-content: center;

    .title {
      text-transform: uppercase;
    }

    .body {
      display: flex;
      @include media-breakpoint-down(md) {
        flex-direction: column;
      }

      .text {
        flex: 2;
        display: flex;
        padding: 0 3em;
        line-height: 1.5;
        font-size: 1rem;
        @include media-breakpoint-down(sm) {
          padding: 0;
          font-size: 1rem;
          line-height: 1.4;
        }
      }

      .image {
        padding: 0 3em;
        flex: 1;
        @include media-breakpoint-down(md) {
          margin-top: 1em;
          padding-left: 0;
        }
        padding-right: 0;

        img {
          margin: auto;
          display: block;
          max-width: 100%;
          max-height: 100%;
        }
      }
    }
  }

  .body {
    font-family: $font-mono;
    margin: 0 4%;
    margin-bottom: 1em;

    .headline {
      text-transform: uppercase;
      font-family: $font-primary;
      font-weight: 600;
      font-size: 1.8em;
      @include media-breakpoint-up(sm) {
        font-size: 2.8em;
      }
      letter-spacing: .03em;
      white-space: pre-wrap;
      line-height: 1.24;
      margin-bottom: 4vh;
    }

    .description {
      font-size: .9rem;
      line-height: 2.2;
      margin-bottom: 4vh;
    }

    .inner-body {
      display: flex;

      .description {
        flex: 2;
      }

      .machine-list {
        margin-top: 3em;
        flex: 1;
        display: flex;
        flex-direction: row;
        justify-content: space-around;

        .machine-item {
          max-width: 750px;
          flex: 1;
        }

        .machine-list-warning {
          max-width: 400px;
          padding: 10px;
          background-color: $color-yellow;
        }
      }
    }

    .link-list {
      color: $color-blue;
      display: block;
      margin: 0;
      padding: 1em;
      padding-left: 0;
      max-width: 80em;

      .link-item {
        word-break: break-all;
        list-style-type: none;
        margin: 0;
        margin-bottom: 4vh;
        font-size: 1.1rem;
        line-height: 1.4;

        .title {
          font-weight: 700;
          text-transform: uppercase;
        }

        .url {
          color: $color-blue;
          font-size: 0.9rem;
          font-family: $font-mono;

          &:hover {
            text-decoration: underline;
          }
        }
      }
    }
  }
}
</style>
