<template>
  <div id="app" class="app">
    <header class="navbar">
      <div class="navbar__list">
        <div class="navbar__item">
          <a class="logo">
            <span>
              <svg
                xmlns="http://www.w3.org/2000/svg"
                height="25"
                viewBox="0 0 106 25"
              >
                <title>Revolut</title>
                <path
                  d="M68.664 8.915c-1.784-1.612-3.938-2.4-6.428-2.4-2.456 0-4.61.789-6.395 2.4-1.784 1.577-2.691 3.772-2.691 6.584s.907 5.005 2.691 6.617c1.784 1.577 3.939 2.366 6.395 2.366 2.49 0 4.644-.789 6.428-2.366 1.818-1.612 2.725-3.806 2.725-6.617s-.908-5.007-2.725-6.584zm-9.792 10.183c-.941-.925-1.415-2.126-1.415-3.6s.47-2.674 1.415-3.566a4.6 4.6 0 0 1 3.363-1.371 4.68 4.68 0 0 1 3.398 1.371c.974.892 1.448 2.091 1.448 3.566s-.47 2.674-1.448 3.6c-.941.891-2.086 1.337-3.398 1.337a4.71 4.71 0 0 1-3.363-1.337zm18.881 4.903V.473h-4.24v23.528zM91.438 6.995v9.388c0 2.262-1.2 3.762-3.484 3.762-2.323 0-3.491-1.498-3.491-3.762V6.995h-4.248v10.108c0 3.916 2.423 7.378 7.739 7.378h.033c5.283 0 7.702-3.539 7.702-7.378V6.995zm-42.8 0l-4.24 11.52-4.24-11.52h-4.509l6.766 17.007h3.972l6.765-17.007zm-12.969 8.023c0-2.468-.773-4.491-2.288-6.103s-3.464-2.4-5.854-2.4c-2.456 0-4.544.858-6.26 2.537-1.684 1.681-2.523 3.806-2.523 6.446s.841 4.801 2.49 6.48c1.684 1.681 3.703 2.503 6.092 2.503 3.67 0 6.26-1.646 7.839-4.972l-3.162-1.852c-1.041 2.091-2.558 3.12-4.61 3.12-2.523 0-4.307-1.646-4.577-4.251h12.852v-1.509zM27.39 9.806c2.389 0 3.972 1.371 4.375 3.566h-8.951c.641-2.023 2.389-3.566 4.577-3.566zm-8.647 14.195l-5.689-10.148c3.599-1.337 5.383-3.668 5.383-7.063C18.441 2.641 15.208 0 10.06 0H0v24.001h4.442v-9.737h3.77l5.45 9.738zM10.06 3.977c2.625 0 3.938 1.063 3.938 3.154s-1.314 3.154-3.938 3.154H4.442V3.977zm92.817 20.504c-2.729 0-4.942-2.256-4.942-5.04V2.4h4.24v4.601h3.636v3.497h-3.636v8.665c0 .816.649 1.477 1.451 1.477h2.185v3.841z"
                ></path>
              </svg>
            </span>
          </a>
        </div>
        <slot v-if="screenSize.isMd">
          <ul class="navbar__item">
            <li
              v-for="(menuItem, index) in headerMenu"
              :key="index"
              class="menu"
            >
              <button type="button" class="button-text">
                {{ menuItem }}
              </button>
            </li>
          </ul>
          <div></div>
        </slot>
        <div v-else class="navbar__item">
          <button type="button" class="navbar-button">
            <span class="navbar-button__icon">
              <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24">
                <title>menu</title>
                <path d="M3,6H21V8H3V6M3,11H21V13H3V11M3,16H21V18H3V16Z" />
              </svg>
            </span>
          </button>
        </div>
      </div>
    </header>
    <main class="main">
      <div class="main__content">
        <!-- <div class="call-to-action background-white">
        <div class="call-to-action__subheader text-dark-gray">
          {{ callToAction.landing.subheader }}
        </div>
        <div class="call-to-action__header text-primary">
          {{ callToAction.landing.header }}
        </div>
        <div class="call-to-action__subtitle">
          {{ callToAction.landing.title }}
        </div>
        <div class="call-to-action__button">
          <div class="base-button base-button-text background-dark">
            <span class="text-white">
              {{ callToAction.landing["button-text"] }}</span
            >
          </div>
        </div>
      </div> -->
        <a
          v-for="(content, index) in page['card-content']"
          :key="index"
          class="main__card"
        >
          <img
            loading="lazy"
            class="main__card-background"
            :srcset="
              screenSize.isSm
                ? `${baseUrl}/${content['image-url-desktop']}`
                : `${baseUrl}/${content['image-url-mobile']}`
            "
          />
          <div class="main__card-content">
            <h3 class="main__card-content-title">
              <span>{{ content.title }}</span>
            </h3>
            <p v-if="content.subtitle" class="main__card-content-subtitle">
              {{ content.subtitle }}
            </p>
            <div class="main__card-action">
              <div class="main__card-action-button">
                <span>
                  <span> {{ content["button-text"] }} </span>
                </span>
                <span class="icon main__card-action-button-icon">
                  <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24">
                    <title>arrow-right</title>
                    <path
                      d="M4,11V13H16L10.5,18.5L11.92,19.92L19.84,12L11.92,4.08L10.5,5.5L16,11H4Z"
                    />
                  </svg>
                </span>
              </div>
            </div>
          </div>
        </a>

        <!-- <div class="call-to-action background-white">
        <div class="call-to-action__subtitle text-dark-gray">
          {{ callToAction["end-of-body"].subtitle }}
        </div>
        <div class="call-to-action__title">
          {{ callToAction["end-of-body"].title }}
        </div>
        <div class="call-to-action__button">
          <div class="base-button base-button-text background-dark">
            <span class="text-white">
              {{ callToAction["end-of-body"]["button-text"] }}</span
            >
          </div>
        </div>
      </div> -->
      </div>
    </main>
    <footer class="footer footer_background-color_dark footer_color_white">
      <div class="footer__container">
        <div class="subscription-plan">
          <div class="subscription-plan__empty"></div>
          <h2
            class="subscription-plan__title subscription-plan__title_color-gray"
          >
            {{ subscription.title }}
          </h2>
          <ul class="subscription-plan__card">
            <li
              v-for="(plan, index) in subscription.plans"
              :key="index"
              class="subscription-card subscription-card_background-color_white"
              @click="(event) => wrapNavigateSubscription(event, index)"
              @mouseover="(event) => wrapHoverSubscription(event, index)"
            >
              <a class="subscription-card__link">
                <span class="subscription-card__content">
                  <h3 class="subscription-card__title">{{ plan.title }}</h3>
                  <h4 class="subscription-card__subtitle">
                    {{
                      plan.price === "0.00" ? "Free" : `RM ${plan.price}/month`
                    }}
                  </h4>
                  <p
                    class="subscription-card__description subscription-card__description_color_dark-gray"
                  >
                    {{ plan.description }}
                  </p>
                </span>
                <span class="subscription-card__action">
                  <span
                    :ref="`iconButton${index}`"
                    class="button-icon button-icon--round"
                    @click="navigateSubscription"
                    @mouseover="hoverSubscription"
                  >
                    <span class="icon">
                      <svg
                        xmlns="http://www.w3.org/2000/svg"
                        viewBox="0 0 24 24"
                      >
                        <title>arrow-right</title>
                        <path
                          d="M4,11V13H16L10.5,18.5L11.92,19.92L19.84,12L11.92,4.08L10.5,5.5L16,11H4Z"
                        />
                      </svg>
                    </span>
                  </span>
                </span>
              </a>
            </li>
          </ul>
        </div>
        <!-- <div class="call-to-action">
          <div class="call-to-action__subtitle text-gray">
            {{ callToAction.footer.subtitle }}
          </div>
          <div class="call-to-action__title text-white">
            {{ callToAction.footer.title }}
          </div>
          <div class="call-to-action__button">
            <div class="base-button base-button-text background-white">
              <span class=""> {{ callToAction.footer["button-text"] }}</span>
            </div>
          </div>
        </div> -->
        <div class="menu-list">
          <div
            v-for="(menu, menuIndex) in menuAndSubmenu"
            :key="menuIndex"
            class="menu-list__item"
          >
            <div v-if="screenSize.isSm" class="">
              <h4 class="">
                {{ menu.title }}
              </h4>
              <div
                v-for="(submenu, submenuIndex) in menu['sub-menu']"
                :key="submenuIndex"
              >
                {{ submenu.title }}
              </div>
            </div>

            <div v-else class="menu-list__collapsible">
              <button class="button menu-list__collapsible">
                {{ menu.title }}
              </button>
              <a
                v-for="(submenu, submenuIndex) in menu['sub-menu']"
                :key="submenuIndex"
              >
                {{ submenu.title }}
              </a>
            </div>
          </div>
        </div>
        <div class="social-media">test</div>
        <div class="company-documents">test</div>
        <div class="copyright">test</div>
        <div class="currency">test</div>
      </div>
    </footer>
  </div>
</template>

<script>
import PAGE_JSON from "./json/en/home/page.json";
import SUBSCRIPTION_JSON from "./json/en/subscription.json";
import MENU_JSON from "./json/en/menu.json";

const SCREEN_SIZE = {
  XS: 360,
  SM: 720,
  MD: 1024,
  LG: 1440,
  XL: 1920,
};

const myMixin = {
  data() {
    return {
      screenSize: {
        isXs: false,
        isSm: false,
        isMd: false,
        isLg: false,
        isXl: false,
      },
    };
  },
  mounted() {
    this.handleResize();
    window.addEventListener("resize", this.handleResize);
  },
  destroyed() {
    window.removeEventListener("resize", this.handleResize);
  },
  methods: {
    handleResize() {
      Object.keys(SCREEN_SIZE).forEach((key) => {
        // console.log(SCREEN_SIZE[key]);
        const firstCharacter = key.charAt(0);
        const restOfTheCharacter = key.substring(1).toLowerCase();
        const capitalize = firstCharacter + restOfTheCharacter;

        // console.log(window.innerWidth, SCREEN_SIZE[key]);
        // console.log(
        //   window.matchMedia(`(min-width: ${SCREEN_SIZE[key]}px)`).matches
        // );

        this.$set(
          this.screenSize,
          `is${capitalize}`,
          window.matchMedia(`(min-width: ${SCREEN_SIZE[key]}px)`).matches
        );
      });
    },
  },
};

export default {
  mixins: [myMixin],
  data() {
    return {
      message: "Hello World!",
      headerMenu: ["Personal", "Business", "Revolt <18", "Company"],
      language: "en-MY",
      subscription: SUBSCRIPTION_JSON,
      page: PAGE_JSON,
      menuAndSubmenu: MENU_JSON,
      baseUrl: import.meta.env.VITE_BASE_URL,
    };
  },
  created() {
    console.log(baseUrl);
  },
  methods: {
    wrapNavigateSubscription(event, index) {
      // console.log(event, index);
      // console.log(this.$refs[`iconButton${index}`][0]);
      // this.$refs[`iconButton${index}`][0].click();
    },
    wrapHoverSubscription(event, index) {
      // console.log(event);
      // this.$refs[`iconButton${index}`][0].mouseOver();
    },
    navigateSubscription() {
      console.log("clicked");
    },
    hoverSubscription() {
      console.log("hover");
    },
  },
};
</script>

<style scoped lang="scss">
/*#region font*/
@font-face {
  font-family: "Custom Font";
  // font-style: normal;
  font-weight: 500;
  // font-stretch: 100%;
  src: url("./assets/font/BasierCircle-Regular.otf") format("woff2");
  // unicode-range: U+0460-052F, U+1C80-1C88, U+20B4, U+2DE0-2DFF, U+A640-A69F, U+FE2E-FE2F;
}
/*#endregion*/

/*#region variables*/
$primary-color: rgb(6, 102, 235);
$gray: rgba(255, 255, 255, 0.5);
$light-gray: rgb(243, 244, 245);
$dark-gray: rgb(80, 90, 99);
$white: rgb(255, 255, 255);
$dark: rgb(25, 28, 31);

$nav-gray: rgba(234, 237, 240, 0.8);
$nav-bottom-gray: rgb(223, 227, 231);

$xm: 0px;
$sm: 720px;
$md: 1024px;
$lg: 0px;
$xl: 0px;
/*#endregion*/

/*region override default*/
button {
  padding: 0;
  border: none;
  cursor: pointer;
}
/*endregion*/

.app {
  font-family: "Custom Font";
  color: $dark;
}

.navbar {
  background-color: $nav-gray;
  backdrop-filter: blur(16px);
  color: $dark;
  position: sticky;
  top: 0px;
  z-index: 2;
  border-bottom: 1px solid $nav-bottom-gray;

  &__list {
    margin: 0px;
    height: 55px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 12px 20px;
  }

  &__item {
    padding: 0px;
    list-style: none;
  }

  &-button {
    background-color: $white;
    width: 36px;
    height: 32px;
    display: flex;
    border-radius: 10px;

    &__icon {
      display: inline-flex;
      width: 16px;
      height: 16px;
      margin: auto;
    }
  }
}

.menu {
  display: flex;
}

.main {
  background-color: $light-gray;

  &__content {
    // transform: translate3d(0px, 0px, 0px);
    display: grid;
    align-content: flex-start;
    gap: 1.25rem;
    max-width: 1000px;
    margin: auto;
    padding-bottom: 60px;
    padding-left: 1.25rem;
    padding-right: 1.25rem;
  }

  &__card {
    border-radius: 20px;
    color: $dark;
    overflow: hidden;
    position: relative;
    height: 100%;
    width: 100%;

    &:hover {
      .main__card-background {
        transform: scale(1.05);
        // translate: translate3d(0px, 0px, 0px);
      }

      .main__card-action-button {
        background-color: $primary-color;
        color: $white;
      }
    }

    // object-fit: initial;
    //1, 4,7
    &:nth-child(3n + 1) {
      aspect-ratio: 0.6594488188976378;

      .main__card-content {
        color: $white;
      }
    }
    //2,5,8
    &:nth-child(3n - 1) {
      aspect-ratio: 0.7613636363636364;

      .main__card-action {
        color: $primary-color;
      }
    }
    // 3,6
    &:nth-child(3n) {
      aspect-ratio: 0.7613636363636364;

      .main__card-content {
        color: $white;
      }
    }

    &-background {
      transform-origin: right bottom;
      transition: transform 0.6s ease 0s;
      position: absolute;
    }

    &-content {
      display: flex;
      flex-direction: column;
      padding: 2rem;
      height: 100%;
      position: relative;

      &-title {
        font-weight: 600;
        font-size: 24px;
      }

      &-subtitle {
        margin-top: 0.5rem;
        font-size: 16px;
      }
    }

    &-action {
      margin-left: -1rem;
      margin-top: 1rem;
      display: flex;
      box-sizing: border-box;
      position: relative;

      &-button {
        width: fit-content;
        border-radius: 20px;
        display: flex;
        align-items: center;
        padding: 0.25rem 0.5rem 0.25rem 1rem;
        position: absolute;

        &-icon {
          margin-left: 0.5rem;
        }
      }
    }
  }
}

.footer {
  padding: 0px;

  &__container {
    display: flex;
    flex-direction: column;
    align-items: center;
    max-width: 1000px;
    margin: auto;
    padding: 0px 20px;
  }

  &_color_white {
    color: $white;
  }

  &_background-color_dark {
    background-color: $dark;
  }
}

.call-to-action {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin: 80px 0px;

  &__header {
    font-size: 96px;
    font-weight: 600;
    text-align: center;
  }

  &__subheader {
    font-size: 24px;
    font-weight: 600;
  }

  &__title {
    font-size: 60px;
    font-weight: 600;
    text-align: center;
    margin-top: 16px;
  }

  &__subtitle {
    font-size: 20px;
    font-weight: 600;
  }

  &__button {
    margin-top: 24px;
  }
}

.subscription {
  &-plan {
    &__empty {
      height: 2.5rem;
    }
    &__title {
      font-weight: 600;
      font-size: 24px;
      padding: 1.25rem 0px;
      display: flex;
      justify-content: center;

      &_color-gray {
        color: $gray;
      }
    }

    &__card {
      display: grid;
      grid-template-columns: repeat(1, 1fr);
      gap: 1.25rem;
    }
  }

  &-card {
    border-radius: 20px;
    padding: 1.5rem 1rem;

    &:hover {
      cursor: pointer;

      .button-icon {
        background-color: $primary-color;
        color: $white;
      }
    }

    &_background-color_white {
      background-color: $white;
    }

    &__link {
      display: grid;
      height: 100%;
      text-decoration: none;
      color: $dark;
    }

    &__content {
      display: flex;
      flex-direction: column;
    }

    &__title {
      font-weight: 600;
      font-size: 24px;
      line-height: 28px;
      margin-block-end: 0.25rem;
    }

    &__subtitle {
      font-weight: 600;
      font-size: 16px;
      line-height: 22px;
      margin-block-end: 0.25rem;
    }

    &__description {
      font-size: 12px;
      line-height: 16px;

      &_color_dark-gray {
        color: $dark-gray;
      }
    }

    &__action {
      display: flex;
      justify-content: end;
      align-items: flex-end;
    }
  }
}

.menu-list {
  margin-top: 2rem;
  margin-bottom: 1.5rem;
  &__item {
  }
}

.button {
  &:hover {
    cursor: pointer;
  }

  &-text {
    margin: 0px 4px;
    padding: 8px 12px;
    background-color: inherit;
    // &__text {
    //   font-size: 16px;
    //   font-weight: 500;
    // }

    &--border {
      height: 32px;
      display: block;
      margin: 8px;
      padding: 0px 16px;
      border-radius: 10px;
      display: flex;
      align-items: center;
    }
  }

  &-icon {
    width: 32px;
    height: 32px;
    display: flex;
    justify-content: center;
    align-items: center;
    color: $primary-color;

    &--round {
      border-radius: 50%;
    }
  }
}

.icon {
  color: inherit;
  width: 24px;
  height: 24px;
}

.card {
  border-radius: 20px;
  color: inherit;

  &__image {
    position: absolute;
    height: 100%;
    width: 100%;
  }

  &__main-content {
    position: relative;
  }

  &:hover {
    .base-button-icon--round {
      background-color: $primary-color;
      color: white;
    }
  }
}

@media (min-width: $sm) {
  .navbar {
    &__list {
      padding: 8px 12px;
    }
  }

  .main {
    &__content {
      grid-template-columns: 1fr 1fr;
    }

    &__card {
      &:hover {
        .main__card-background {
        }
      }

      &:nth-child(3n + 1) {
        grid-column: 1/-1;
        aspect-ratio: 1.9083969465648856;

        .main__card-content {
          width: 51.6%;

          &-title {
            margin-top: auto;
            display: block;
          }
        }
      }
      &:nth-child(3n - 1) {
        aspect-ratio: 0.8461538461538461;
      }
      &:nth-child(3n) {
        aspect-ratio: 0.8461538461538461;
      }

      &-action {
        margin-top: auto;
        align-items: flex-end;
      }
    }
  }

  .subscription {
    &-plan {
      &__card {
        grid-template-columns: repeat(4, 1fr);
      }
    }
  }

  //   &-card {
  //     max-width: 226px;
  //     display: grid;
  //     // max-height: 308px;
}

@media (min-width: $md) {
  .navbar {
    &__list {
      height: 69px;
      width: 1000px;
      padding: 16px 0px;
      margin: 0px auto;
      justify-content: flex-start;
    }

    &__item {
      display: flex;
    }
  }

  .menu {
    //
    // padding: 0px;
    flex-direction: row;
    &__item {
    }
  }

  .main {
    &__content {
      padding-bottom: 128px;
      padding-left: 0px;
      padding-right: 0px;
    }

    &__card {
      &-background {
        transform-origin: center center;
      }

      &-content {
        &-title {
          font-size: 34px;
          line-height: 40px;
        }
        &-subtitle {
          font-size: 20px;
          line-height: 28px;
          margin-top: 1rem;
        }
      }

      &-action {
        font-size: 20px;
      }
    }
  }

  .subscription {
    &-plan {
      &__title {
        padding: 2.5rem 0px;
      }

      &__card {
        gap: 2rem;
      }
    }

    &-card {
      &__title {
        font-size: 34px;
        line-height: 40px;
        margin-block-end: 0.5rem;
      }
      &__subtitle {
        font-size: 20px;
        line-height: 24px;
        margin-block-end: 0.5rem;
      }
      &__description {
        font-size: 14px;
        line-height: 20px;
      }
    }
  }

  .footer {
    &__container {
      padding: 0px;
    }
  }
}
</style>
