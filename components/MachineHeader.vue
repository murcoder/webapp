<template>
  <div class="machine-header">
    <div
      class="header-image"
      :style="{ 'background-image': 'url(' + $resizeImage(machine.headerImage, '1600x0') + ')' }"
    />
    <div
      v-if="machine.title"
      class="header-title"
    >
      <div class="tags">
        <span :key="tag.id" v-for="(tag, index) in tags">
          {{ tag }}<span v-if="index+1 < tags.length">, </span>
        </span>
      </div>
      <div class="title">
        {{ machine.title }}
      </div>
      <machine-status
        v-if="singleMachine && hasUser && hasBridge"
        :id="machine.machine_status_items[0].fabmanId"
        class="status"
      />
    </div>
  </div>
</template>

<script>
import MachineStatus from '@/components/MachineStatus'

export default {
  components: {
    MachineStatus
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
    hasBridge () {
      return this.machine.machine_status_items[0].hasBridge
    }
  }
}
</script>

<style lang="scss">
@import '@/assets/scss/styles.scss';

.machine-header {
  display: flex;
  flex-direction: column;
  flex-grow: 1;
  align-items: stretch;
  align-content: stretch;
  position: relative;
  @include margin-page-wide();
  background-color: #555;
  margin-bottom: 10vh;
  .header-image {
    min-height: calc(50vh);
    @include media-breakpoint-down(xs) {
      min-height: calc(30vh);
    }
    width: 100%;
    background-size: cover;
    background-position: center;
    opacity: .9;
  }
  .header-title {
    position: relative;
    @include media-breakpoint-up(md) {
      position: absolute;
      right: 0;
      bottom: 0;
    }
    background-color: #FFF;
    padding: 7vh;
    min-width: 60%;
    .tags {
      color: $color-blue;
      text-transform: uppercase;
      margin-bottom: .8rem;
      letter-spacing: 0.05em;
      font-weight: 400;
    }
    .title {
      margin: 0 0 .8rem;
      font-size: 1.5rem;
      @include media-breakpoint-up(md) {
        font-size: 2.5rem;
      }
      font-family: 'Chakra Petch';
      font-weight: bold;
    }
    .subtitle {
      font-size: .9rem;
      letter-spacing: .05em;
    }
    .status {
      position: absolute;
      top: 0;
      right: 0;
    }
  }
}
</style>
