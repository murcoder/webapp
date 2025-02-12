<template>
  <div
    class="header-wrapper"
    :class="{ 'scrolled': scrolled }"
  >
    <div
      v-if="hasAuth"
      class="login-header"
    >
      <div class="login-header-content">
        <template v-if="hasUser">
          <nuxt-link
            class="me"
            to="/me"
          >
            <font-awesome-icon
              icon="user"
              style="margin-right: 0.2em; font-size: 0.9em"
            />
            <span>{{ username }}</span>
          </nuxt-link>
          <div
            class="logout"
            @click="logout"
          >
            <font-awesome-icon icon="sign-out-alt" />
          </div>
        </template>
        <span v-else>
          <loading-spinner color="white" />
        </span>
      </div>
    </div>
    <header class="top-header">
      <div class="top-header-inner">
        <div class="logo">
          <nuxt-link
            class="top-header__link"
            to="/"
          >
            <img src="~/assets/img/icons/gg-logo-icon.svg">
            <span v-if="devWarning">{{ devWarning }}</span>
          </nuxt-link>
          <div
            v-if="home && home.length > 0"
            class="dropdown"
          >
            <div
              v-for="child in home"
              :key="child.id"
              class="child"
            >
              <sb-link
                :link="child.link"
                class="child-nav-item"
                target="_blank"
              >
                {{ child.name }}
              </sb-link>
            </div>
          </div>
        </div>
        <div class="spacer" />
        <main-nav-item
          v-for="item in main"
          :key="item.id"
          class="desktop"
          :item="item"
        />
        <div class="right-corner">
<!--          <LanguageInput> </LanguageInput>-->
          <div
              v-if="!hasAuth"
              class="login-button"
          >
            <button @click="login">
              LOGIN
            </button>
          </div>
          <div
            class="menu-icon"
            @click="toggleMenu()"
        >
          <img src="~/assets/img/icons/menu-icon.svg">
        </div>
        </div>
      </div>
    </header>
    <transition name="fadefromright">
      <div
        v-show="showMenu"
        class="mobile-nav"
      >
        <div class="mobile-nav-header">
          <div
            class="home"
            @click="toggleMenu()"
          >
            <nuxt-link to="/">
              <img
                class="logo"
                src="~/assets/img/icons/gg-logo-icon.svg"
              >
            </nuxt-link>
          </div>
          <div
            class="close-nav"
            @click="toggleMenu"
          >
            <svg
              class="close-nav-icon"
              viewBox="0 0 32 32"
              height="32"
              width="32"
            >
              <g>
                <path d="M 5.5488281 3.8535156 A 2.0002 2.0002 0 0 0 4.15625 7.2890625 L 13.388672 16.519531 L 4.15625 25.751953 A 2.0002 2.0002 0 1 0 6.984375 28.580078 L 16.216797 19.347656 L 25.449219 28.580078 A 2.0002 2.0002 0 1 0 28.277344 25.751953 L 19.044922 16.519531 L 28.277344 7.2890625 A 2.0002 2.0002 0 0 0 26.824219 3.8554688 A 2.0002 2.0002 0 0 0 25.449219 4.4589844 L 16.216797 13.691406 L 6.984375 4.4589844 A 2.0002 2.0002 0 0 0 5.5488281 3.8535156 z " />
              </g>
            </svg>
          </div>
        </div>
        <div class="main-nav-items">
          <main-nav-mobile-item
            v-for="item in main"
            :key="item.id"
            class="mobile"
            :item="item"
            @close="closeMenu"
          />
        </div>
        <div
          v-if="home && home.length > 0"
          class="house-nav-items"
        >
          <div
            v-for="child in home"
            :key="child.id"
            class="item"
          >
            <sb-link
              :link="child.link"
              class="item-link"
              target="_blank"
            >
              {{ child.name }}
            </sb-link>
          </div>
        </div>
      </div>
    </transition>
  </div>
</template>

<script charset="utf-8">
/* import LanguageInput from './LanguageInput' */

export default {
/*  components: {
    LanguageInput
  }, */
  props: ['blok'],
  data () {
    return {
      scrolled: false,
      showMenu: false
    }
  },
  computed: {
    loginLink () {
      return '/' + this.$store.state.language + '/login'
    },
    main () {
      return this.$store.state.settings.main_navi
    },
    home () {
      return this.$store.state.settings.home_navi
    },
    username () {
      return this.$store.state.user.profile.firstName + ' ' + this.$store.state.user.profile.lastName
    },
    hasAuth () {
      return !!this.$store.state.auth
    },
    hasUser () {
      return !!this.$store.state.user
    },
    devWarning () {
      return process.env.NODE_ENV === 'development' ? 'DEV' : null
    }
  },
  watch: {
    '$store.state.route.fullPath': function () {
      this.closeMenu()
    }
  },
  created () {
    if (process.client) {
      window.addEventListener('scroll', this.handleScroll)
    }
  },
  unmounted () {
    if (process.client) {
      window.removeEventListener('scroll', this.handleScroll)
    }
  },
  methods: {
    closeMenu () {
      this.showMenu = false
    },
    toggleMenu () {
      this.showMenu = !this.showMenu
    },
    login () {
      this.$store.dispatch('setSidebar', 'login')
    },
    logout () {
      this.$store.dispatch('logout').then(() => {
        this.$router.push('/')
      })
    },
    // add css-shadow when page is scrolled down
    handleScroll () {
      this.scrolled = window.scrollY > 0
    }
  }
}
</script>

<style lang="scss" scoped>
@import '/assets/scss/styles.scss';

.header-wrapper {
  background-color: $color-bright-bg;
  position: fixed;
  top: 0;
  z-index: 1000;
  width: 100%;
  max-width: 100%;
  transition: box-shadow 1s linear;
  &.scrolled {
    box-shadow: 0 2px 5px rgba(0,0,0,.2);
  }
  .login-header {
    display: flex;
    flex-flow: row nowrap;
    justify-content: flex-end;
    align-items: center;
    background-color: $color-blue;
    padding: 5px;
    color: #FFF;
    font-size: 0.85em;
    height: 2em;
    .login-header-content {
      display: flex;
      flex-flow: row nowrap;
      fons-size: 1.1em;
      @include margin-page-wide();
      .logout {
        margin-left: 2em;
        cursor: pointer;
        font-size: 1.1em;
      }
      .me {
        font-size: 1.1em;
      }
    }
    a {
      color: #FFF;
    }
  }
}

.top-header {
  @include margin-page-wide();
  font-size: 1.1em;
  @media screen and (min-width: 1149px) {
    letter-spacing: .1em;
  }
  .top-header-inner {
    display: flex;
    justify-content: space-between;
    margin: 0 -15px 0 -20px; // compensate paddings from logo and nav items
    .right-corner{
      display:flex;
      align-items: center;
      padding: 12px 15px;
      .login-button {
        padding: 12px 15px;
        button {
          font-weight: bold;
          line-height: 1em;
          padding: 10px;
          outline: none;
          width: 100%;
          color: #FFF;
          border: none;
          background-color: $color-orange;
          margin: 0;
          cursor: pointer;
        }
    }

    }
  }

  .logo {
    position: relative;
    // only for desktop navigation
    @include media-breakpoint-up(md) {
      &:hover {
        .dropdown {
          display: block;
        }
      }
    }
    a {
      padding: 20px;
      display: block;
      img {
        height: 1.1em;
      }
    }
    .dropdown {
      display: none;
      position: absolute;
      padding: 20px;
      background-color: #FFF;
      min-width: 150px;
      left: 18px;
      text-align: left;
      .child {
        .child-nav-item {
          white-space: nowrap;
          display: block;
          text-transform: uppercase;
          color: #000;
          text-decoration: none;
          font-weight: bold;
          font-size: 0.9rem;
          padding: 8px;
        }
      }
    }
  }

  .menu-icon {
    display: none;
  }

  .spacer {
    flex: 1;
  }
}

.mobile-nav {
  display: none;
  .mobile-nav-header {
    display: flex;
    justify-content: space-between;
    .close-nav {
      padding: 4%;
      cursor: pointer;
      .close-nav-icon {
        width: 1.1em;
      }
    }
    .home {
      padding: 20px;
      .logo {
        height: 1em;
      }
    }
  }
  .main-nav-items {
    flex-grow: 1;
  }
  .house-nav-items {
    background-image: url("data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' width='270' height='100'><path fill='white' d='M101.424.285L0 47.777v51.938h270V46.47L101.424.285'></path></svg>");
    background-size: cover;
    width: 100%;
    height: 30vw;
    display: flex;
    align-items: flex-end;
    justify-content: space-around;
    padding: 0 3vw;
    .item {
      flex-grow: 1;
      flex-basis: 100%;
      font-weight: bold;
      font-size: .85em;
      letter-spacing: .05em;
      .item-link {
        display: block;
        text-align: center;
        padding:  3vh .5em;
      }
    }
  }
}

/* Mobile */
@media screen and (max-width: 1334px) {
  .top-header {
    .top-header-inner {
      display: flex;
      justify-content: flex-end;
      margin: 0 -20px 0 -20px; // compensate paddings from logo and burger button
    }
    .nav-item.desktop {
      display: none;
    }

    .logo {
      img {
        height: 1.1em;
      }
    }
    .menu-icon {
      padding: 20px;
      img {
        height: 1.1em;
      }
    }
    .spacer {
      flex: 1;
    }

    .menu-icon {
      display: block;
    }

  }

  .mobile-nav {
    background-color: $color-bright-bg;
    display: flex;
    flex-direction: column;
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    overflow-y: auto;
    height: 100vh;
    background: $color-bright-bg;
  }

  .fadefromright-enter-active, .fadefromright-leave-active {
    transition: all .3s;
  }
  .fadefromright-enter, .fadefromright-leave-to {
    opacity: 0;
    transform: translateX(50vw);
  }
}

</style>
