<template>
  <div class="section">
    <div style="margin-top: 2em;"><img width="80px" src="~/assets/img/icons/fireworks.svg" class="decorator"></div>
    <h2 style="margin: 0;">{{ $t('congrats') }}</h2>
    <p class="text">
      {{ $t('youMadeTheFirstStepsTowardsBecomingA-GG-Member') }}<br>{{ $t('toCompleteOnboardingStartSafetyTraining') }}
    </p>
  </div>
</template>
<script>
export default {
  middleware: 'authenticated',
  mounted () {
    this.$store.dispatch('getMemberCourses')
  }
}
</script>
<style lang="scss" scoped>
.section {
  text-align: center;
  margin-top: 1em;
}
</style>
