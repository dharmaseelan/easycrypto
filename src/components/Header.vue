<template>
  <header id="header">
    <div class="container">
      <b-navbar>
        <template #brand>
          <b-navbar-item tag="router-link" :to="{ path: '/' }">
            <img alt="logo" src=".././assets/logo.png" class="logo" />
          </b-navbar-item>
        </template>

        <template #end>
          <b-navbar-dropdown label="Buy & Sell">
            <b-navbar-item href="#">Instant buy & sell</b-navbar-item>
            <b-navbar-item href="#">Multi-coin order</b-navbar-item>
            <b-navbar-item href="#">Auto-Buy</b-navbar-item>
            <b-navbar-item href="#">Swap</b-navbar-item>
          </b-navbar-dropdown>
          <b-navbar-item href="#">Rates</b-navbar-item>
          <b-navbar-item href="#">Tracker</b-navbar-item>
          <b-navbar-item href="#">About Us</b-navbar-item>
          <b-navbar-item tag="div">
            <div class="buttons">
              <a class="button is-light">Sign in</a>
              <a class="button is-primary"><strong>Sign up</strong></a>
            </div>
          </b-navbar-item>
        </template>
      </b-navbar>
    </div>
  </header>
</template>

<script>
export default {
  name: "Header",
};
</script>

<style lang="scss">
#header {
  position: absolute;
  width: 100%;
  height: auto;
  top: 0;
  left: 0;
  padding: 20px 0;
  .navbar {
    background-color: transparent;
  }
  .logo {
    max-height: 50px;
  }
  .navbar-link,
  .navbar-item {
    color: $bg-color;
    font-weight: 500;
    &:after {
      color: $bg-color;
    }
  }
  .navbar-menu {
    a {
      &.navbar-item {
        &:before {
          position: absolute;
          width: 0;
          height: 2px;
          content: "";
          bottom: 12px;
          left: 0;
          background-color: $bg-color;
          border-radius: 5px;
          opacity: 0;
          @include trans(0.6s);
        }
        &:hover,
        &:active,
        &:focus {
          background-color: transparent;
          &:before {
            width: 100%;
            opacity: 1;
          }
        }
      }
    }
    .navbar-dropdown {
      background-color: $primary-color;
    }
    .navbar-item {
      &.has-dropdown,
      &.is-active {
        .navbar-link {
          background-color: transparent;
          &:after {
            border-color: $bg-color;
          }
          &:hover,
          &:active {
            background-color: transparent;
          }
        }
        .navbar-dropdown {
          a.navbar-item {
            @include trans;
            &:before {
              display: none;
            }
            &:hover {
              background-color: $bg-color;
              color: $primary-color;
            }
          }
        }
      }
    }
  }
  .navbar-burger {
    color: $bg-color;
    span {
      height: 2px;
    }
  }
  @media (max-width: 1023px) {
    .navbar-menu {
      background-color: $primary-color;
    }
  }
  @media (max-width: 767px) {
    .logo {
      max-height: 35px;
    }
  }
}
</style>
