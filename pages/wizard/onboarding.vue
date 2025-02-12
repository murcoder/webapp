<template>
  <div
      v-if="user !== null"
      class="wizard"
  >
    <div class="header">
      <font-awesome-icon
          class="icon"
          icon="user-friends"
      />
      <h2>{{ $t('joinNow') }}</h2>
      <p>{{ $t('becomeAMemberIn4simpleSteps') }}</p>
    </div>
    <div class="wizard-section">
      <div class="wizard-section-menu">
        <div class="steps">
          <div
              :key="i"
              v-for="s,i in steps"
              class="step"
              :class="{ 'icon': index > i, 'color': index >= i}"
          >
            <!--            <NuxtLink class="dot" v-if="i == 0" to="/wizard/onboarding/">-->
            <span
                v-if="!i"
                class="dot"
            >
              <svg
                  xmlns="http://www.w3.org/2000/svg"
                  viewBox="0 0 230 200"
              ><path
                  d="M20 130l40 40L200 30"
                  stroke-width="25"
                  fill="none"
                  stroke="#FFF"
              /></svg>
            </span>
            <!--            </NuxtLink>-->
            <!--            <NuxtLink class="dot" v-else :to="'/wizard/onboarding/' + s">-->
            <span
                v-else
                class="dot"
            >
              <svg
                  xmlns="http://www.w3.org/2000/svg"
                  viewBox="0 0 230 200"
              ><path
                  d="M20 130l40 40L200 30"
                  stroke-width="25"
                  fill="none"
                  stroke="#FFF"
              /></svg>
            </span>
            <!--            </NuxtLink>-->
          </div>
        </div>
      </div>
      <div class="wizard-section-content">
        <NuxtChild
            :key="$route.params.slug"
            :onboarding-data="onboardingData"
        />
      </div>
      <div class="wizard-section-nav">
        <div class="form">
          <div class="button-row">
            <button
                v-if="activeStep === 'confirmation'"
                class="input-button-primary"
                @click="$router.push('/me/trainings')"
            >
              <font-awesome-icon icon="arrow-circle-right"/> {{ $t('startSafetyTraining') }}
            </button>
            <button
                v-else-if="index > 0"
                class="input-button-primary"
                @click="back()"
            >
              {{ $t('back') }}
            </button>
            <button
                v-if="activeStep !== 'confirmation'"
                :class="['input-button-primary', { disabled: !nextStepEnabled }]"
                :disabled="nextStepEnabled"
                @click="next()"
            >
              {{ activeStep === 'done' ? 'Anmeldung abschließen' : 'Weiter' }}
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  middleware: 'authenticated',
  data () {
    return {
      loading: false,
      steps: ['index', 'contact', 'payment', 'done', 'confirmation'],
      onboardingData: {
        paymentType: null,
        paymentFrequency: null,
        rulesAccepted: false,
        profile: {
          address: null,
          address2: null,
          city: null,
          zip: null,
          phone: null,
          birthdate: null,
          company: null
        },
        sepaAccepted: false,
        payment: {
          iban: null
        },
        ibanIsValid: false,
        referrer: ''
      }
    }
  },
  computed: {
    activeStep () {
      return this.$route.path.split('/')[3] || 'index'
    },
    nextStepEnabled () {
      const data = this.onboardingData
      switch (this.activeStep) {
        case 'index':
          return !(data.paymentType && data.rulesAccepted)
        case 'contact': {
          const requiredKeys = ['address', 'city', 'zip', 'phone', 'birthdate']
          return !!requiredKeys.filter(k => !data.profile[k]).length
        }
        case 'payment':
          return !(data.ibanIsValid && data.sepaAccepted && data.paymentFrequency)
        default:
          return false
      }
    },
    index () {
      return this.steps.indexOf(this.activeStep)
    },
    user () {
      return this.$store.state.user
    }
  },
  created () {
    this.getData()
  },
  methods: {
    getData () {
      if (sessionStorage.getItem('onboardingData')) {
        this.onboardingData = JSON.parse(sessionStorage.getItem('onboardingData'))
      }
      const user = this.$store.state.user
      for (const key of Object.keys(this.onboardingData.profile)) {
        if (Object.prototype.hasOwnProperty.call(user, key)) {
          this.onboardingData.profile[key] = user.profile[key]
        }
      }
    },
    saveUserData () {
      this.$store.dispatch('updateUser', Object.assign({}, this.onboardingData.profile))
    },
    saveOnboardingData () {
      sessionStorage.setItem('onboardingData', JSON.stringify(this.onboardingData))
    },
    back () {
      const ni = this.index - 1 < 0 ? 0 : this.index - 1
      let path = this.steps[ni]
      if (ni === 0) {
        path = ''
      }
      this.$router.push('/wizard/onboarding/' + path)
    },
    next () {
      if (this.activeStep === 'done') {
        this.send()
        // sessionStorage.removeItem('onboarding')
      } else {
        this.saveOnboardingData()
      }
      const ni = this.index + 1 < 0 ? 0 : this.index + 1
      const path = this.steps[ni]
      if (path === 'payment') {
        this.saveUserData()
      }
      this.$router.push('/wizard/onboarding/' + path)
    },
    async send () {
      this.loading = true
      await this.$store.dispatch('startOnboarding', this.onboardingData)
      this.loading = false
    }
  }
}
</script>

<style lang="scss">
@import '/assets/scss/styles.scss';

.wizard {
  margin: 0 4%;

  & .header {
    margin-top: 1em;

    & .icon {
      font-size: 3em;
    }
  }

  .wizard-section {
    h2 {
      width: 100%;
      margin-top: 1.5em;
      text-align: center;
    }

    & .form {
      margin-top: 1em;
    }

    display: flex;
    align-items: center;
    flex-direction: column;

    .wizard-section-menu {
      .steps {
        .step {
          display: inline-block;
          position: relative;

          &:before {
            z-index: -1;
            content: '';
            position: absolute;
            margin-top: -3px;
            top: 50%;
            right: -10px;
            border-bottom: 6px solid #999;
            width: 50px;
          }

          &.color {
            .dot {
              background-color: $color-orange;
            }
          }

          &.icon {
            .dot {
              svg {
                display: block;
              }
            }

            &:before {
              border-bottom: 6px solid $color-orange;
            }
          }

          .dot {
            height: $step-size;
            width: $step-size;
            display: inline-block;
            border-radius: 50%;
            margin-right: $step-size;
            background-color: #999;

            svg {
              display: none;
              padding: 8px;
              height: 30px;
            }
          }

          &:last-child {
            .dot {
              margin-right: 0;
            }

            &:before {
              display: none;
            }
          }
        }
      }
    }

    .wizard-section-content {
      width: 100%;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
    }

    .wizard-section-nav {
      min-width: 50vh;

      .button-row {
        display: flex;
        flex-flow: row nowrap;
        justify-content: space-evenly;

        .spacer {
          flex: 1;
        }
      }
    }
  }

  .input-button-primary:disabled {
    cursor: default;
    background-color: grey;
    border: 1px solid darkgrey;
  }
}
</style>
