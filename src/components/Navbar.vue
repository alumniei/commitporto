<template>
  <nav :class="{scrolled: scrolled}">
    <router-link to="#about">About</router-link>
    <router-link to="#agenda">Agenda</router-link>
    <router-link to="#sponsors">Sponsors</router-link>
    <!-- <Button
      id="eventbrite-widget-modal-trigger-61719447529"
      text="Get tickets"
      isSecondary={true}
    /> -->
  </nav>
</template>

<script>
import Button from '@/components/common/Button';

export default {
  name: 'Navbar',
  props: ['scrolled'],
  components: {
    Button,
  },
};
</script>

<style>
@import '../variables';

nav {
  position: fixed;
  top: var(--small-space);
  right: 0;
  z-index: 1;
  padding: var(--x-small-space) var(--small-space);

  & a {
    text-transform: uppercase;
    text-decoration: none;
    color: var(--white);
    font-weight: lighter;
    font-size: var(--text-font);

    &:not(:last-child) {
      margin-right: var(--space);
    }

    &:hover {
      position: relative;

      &::before {
        content: '⌜';
        position: absolute;
        top: -10px;
        left: -10px;
      }

      &::after {
        content: '⌟';
        position: absolute;
        bottom: -10px;
        right: -10px;
      }
    }
  }

  &.scrolled {
    background: var(--white);
    box-shadow: 0px 0px 3px 1px rgba(0, 0, 0, 0.25);

    & a {
      color: var(--text-color);
    }
  }

  @media (--bellow-desktop) {
    & a {
      &:not(:last-child) {
        margin-right: var(--x-small-space);
      }
    }
  }
}

</style>
