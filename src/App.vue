<template>
  <div id="app">
    <Navbar :scrolled="scrolled" />
    <router-view @modalVisible="showModal" />
    <Footer />
    <Modal v-show="isModalVisible" @close="closeModal">
      <component :is="modalComponent" slot="body" v-bind="modalProperties"></component>
    </Modal>
  </div>
</template>

<script>
import Modal from '@/components/common/Modal';
import Footer from '@/components/Footer';
import Navbar from '@/components/Navbar';

export default {
  name: 'App',
  components: {
    Modal,
    Footer,
    Navbar,
  },
  data: () => ({
    isModalVisible: false,
    modalComponent: null,
    modalProperties: null,
    scrolled: false,
  }),
  methods: {
    showModal(modalComponent, modalProperties) {
      this.isModalVisible = true;
      this.modalComponent = modalComponent;
      this.modalProperties = modalProperties;
      document.body.classList.add('modalVisible');
    },
    closeModal() {
      this.isModalVisible = false;
      document.body.classList.remove('modalVisible');
    },
    handleScroll() {
      this.scrolled = window.scrollY > 0;
    },
  },
  created() {
    window.addEventListener('scroll', this.handleScroll);
  },
  destroyed() {
    window.removeEventListener('scroll', this.handleScroll);
  },
};
</script>

<style>
@import './variables';

body {
  margin: 0;
  width: 100%;
  height: 100%;
  position: relative;

  &.modalVisible {
    overflow: hidden;
  }
}

#app {
  font-family: var(--main-font);
  color: var(--text-color);
  margin: 0;
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.border {
  &::before {
    content: '';
    position: absolute;
    background-color: var(--main-color);
  }

  &::after {
    content: '';
    position: absolute;
    background-color: var(--main-color);
  }
}

.section {
  display: flex;
  flex-direction: column;
  margin: 140px auto 0;
  width: 70%;

  @media (--bellow-desktop) {
    margin: 100px auto 0;
    width: 80%;
  }

}

.upper-border {
  &::before {
    top: 0;
    left: 0;
    width: 15px;
    height: 200px;
  }

  &::after {
    top: 0;
    left: 0;
    width: 150px;
    height: 15px;
  }
}

.bottom-border {
  &::before {
    bottom: 0;
    right: 0;
    width: 15px;
    height: 100px;
  }

  &::after {
    bottom: 0;
    right: 0;
    width: 150px;
    height: 15px;
  }
}
</style>
