<template>
  <nav class="vuestic-navbar navbar navbar-toggleable-md">
    <div class="vuestic-navbar__logo">
      <router-link class="navbar-brand" to="/dashboard">
        <slot class="logo" name="logo"/>
      </router-link>
    </div>
    <div class="row vuestic-navbar__content">
      <div class="header-elem-wrapper menu-icon-container justify-content-lg-start col">
        <slot name="selector"></slot>
      </div>
      <slot class="col-xs-10"></slot>
      <slot name="profile"/>
    </div>
  </nav>
</template>

<script>
export default {
  name: 'vuestic-navbar',
}
</script>

<style lang="scss">
  .vuestic-navbar {
    .layout-fixed & {
      position: fixed;
      top: 0;
      width: 100%;
      z-index: 1;
    }

    .header-elem-wrapper {
      display: flex;
      align-items: center;
      justify-content: center;
    }

    .vuestic-navbar__content {
      width: 100%;
      height: 100%;
      margin: 0;
    }

    height: $top-nav-height;
    padding-left: $nav-padding-left;
    padding-right: $nav-padding-right;
    background-color: $top-nav-bg;

    .vuestic-navbar__logo {
      font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
      letter-spacing: 3px;
      font-weight: 700;
      display: flex;
      align-items: center;
      justify-content: center;
      position: absolute;
      z-index: 3;
      height: 100%;
      width: 10%;
      left: $navbar-brand-container-left;
      top: 0;

      @include media-breakpoint-down(md) {

        .vuestic-navbar__logo {
          width: $nav-mobile-brand-width;
          top: $nav-mobile-brand-top;
          left: $nav-mobile-brand-left;
          height: auto;
          .navbar-brand {
            height: $font-size-smaller;
            padding: 0;
            font-size: $font-size-smaller;
          }
        }
      }
    }

    .menu-icon-container {
      padding: 0;
      font-size: $font-size-base;
    }

    .nav-item {
      padding: 0;
      height: 100%;
    }

    .dropdown.navbar-dropdown {
      display: flex;
      align-items: center;
      justify-content: center;

      .dropdown-toggle {
        display: flex;
        align-items: center;
        justify-content: center;
        padding: 0;

        &:after {
          display: none;
        }
      }

      &.show {
        @include media-breakpoint-up(lg) {
          .dropdown-menu {
            left: auto;
            right: 0;
          }
        }
        &:after {
          position: absolute;
          bottom: -$dropdown-show-b;
          right: calc(50% - 10px);
          width: 0;
          height: 0;
          display: block;
          content: '';
          border-left: 10px solid transparent;
          border-right: 10px solid transparent;
          border-bottom: 10px solid $darkest-gray;
        }
      }

      .dropdown-menu {
        margin-top: $dropdown-show-b;
        padding-top: 0;
        width: 100%;
      }

      .dropdown-item {
        height: $navbar-dd-item-height;
        cursor: pointer;
        font-size: $font-size-base;

        &:hover, &:active, &:focus, &.active {
          outline: none;
        }

        &.plain-link-item {
          color: $brand-primary;

          &:hover, &:active, &:focus {
            background: $dropdown-background;
          }

          .plain-link {
            text-decoration: none;
          }
        }
      }
    }

    @include media-breakpoint-down(md) {
      height: $top-mobile-nav-height;
      padding: $nav-mobile-pt $nav-mobile-padding-h $nav-mobile-pb $nav-mobile-padding-h;

      .vuestic-navbar__logo {
        width: $nav-mobile-brand-width;
        top: $nav-mobile-brand-top;
        left: $nav-mobile-brand-left;
        height: auto;
        .navbar-brand {
          height: $font-size-smaller;
          padding: 0;
          font-size: $font-size-smaller;
        }
      }

      .dropdown.navbar-dropdown {
        &.show {
          display: flex;
          &:after {
            bottom: -$dropdown-mobile-show-b;
            z-index: 2;
          }
          .dropdown-menu {
            margin-top: $dropdown-mobile-show-b;
            left: auto;
            &.last {
              right: 0;
            }
          }
        }
      }
    }
  }
</style>
