<template>
  <div class="machine-calendar">
    <div v-if="bookings">
      <vue-cal
        class="calendar"
        xsmall
        default-view="day"
        :events="bookings"
        locale="de"
        :hide-weekdays="[1, 7]"
        :time-from="9 * 60"
        :time-to="20 * 60"
        :time-step="30"
        :disable-views="['years', 'year', 'month']"
      />
    </div>
    <div v-else>
      loading
    </div>
  </div>
</template>

<script>
import moment from 'moment'
import VueCal from 'vue-cal'
import 'vue-cal/dist/i18n/de.js'
import 'vue-cal/dist/vuecal.css'

export default {
  components: { VueCal },
  props: ['id'],
  data () {
    return {
      bookings: null
    }
  },
  computed: {
    hasUser () {
      return !!this.$store.state.user
    },
    events () {
      return this.bookings.map((b) => {
        return {
          title: b.title,
          class: b.class,
          start: moment(b.fromDateTime).format('YYYY-MM-DD HH:mm'),
          end: moment(b.untilDateTime).format('YYYY-MM-DD HH:mm')
        }
      })
    }
  },
  created () {
    this.$store.dispatch('getBookings', this.id).then((r) => {
      this.bookings = JSON.parse(JSON.stringify(r))
    })
  }
}
</script>

<style lang="scss">
@import '/assets/scss/styles.scss';

.machine-calendar {
  .calendar {
    background-color: #FFF;
  }
}
</style>
