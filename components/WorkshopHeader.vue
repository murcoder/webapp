<template>
  <div
    v-editable="blok"
    class="header"
  >
    <div
      class="header-image"
      :style="{ 'background-image': 'url(' + $resizeImage(blok.image, '1600x0') + ')' }"
    />
    <div
      v-if="blok.title"
      class="header-title"
    >
      <h4>{{ blok.title }}</h4>
    </div>
  </div>
</template>

<script>
export default {
  props: ['blok']
}
</script>

<style lang="scss" scoped>
@import '/assets/scss/styles.scss';

.header {
  margin: 0 4%;

  height: calc(72vh - 64px);

  position: relative;
  .header-image {
    height: 100%;
    background-size: cover;
    background-position: center;
  }
  .header-title {
    position: absolute;
    right: 0;
    bottom: 0;
    background-color: #FFF;
    padding: 75px;
    min-width: 50%;
    h4 {
      margin: 0;
      font-size: 3rem;
      font-family: 'Chakra Petch';
      font-weight: bold;
    }
  }

  @include media-breakpoint-down(sm) {
    height: auto;
    .header-image {
      height: 33vh;
    }
    .header-title {
      position: relative;
      padding: 5%;
      text-align: right;
      h4 {
        font-size: 2rem;
      }

    }
  }
}
</style>
