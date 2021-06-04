<template>
  <transition name="modal-fade">
    <div class="modal">
      <div class="overlay"></div>
      <div class="modal-content">
        <div @click="close" class="close">x</div>
        <slot name="header"></slot>
        <slot name="body"></slot>
      </div>
    </div>
  </transition>
</template>

<script>
export default {
  name: 'Modal',
  mounted() {
    document.body.addEventListener('keyup', (e) => {
      if (e.keyCode === 27) {
        this.close();
      }
    });
  },
  methods: {
    close() {
      this.$emit('close');
    },
  },
};
</script>

<style>
@import '../../variables';

.modal-fade-enter,
.modal-fade-leave-active {
  opacity: 0;
}

.modal-fade-enter-active,
.modal-fade-leave-active {
  transition: opacity .5s ease
}

.modal {
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  z-index: 2;
}

.overlay {
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  background-color: rgba(255, 255, 255, 0.7);
}

input{
  background-color: var(--text-color);
  color: white;
}

button.secondary{
  color: var(--text-color) !important;
}

.modal-content {
  position: fixed;
  top: 50%;
  left: 0;
  right: 0;
  margin-left: auto;
  margin-right: auto;
  transform: translateY(-50%);
  max-width: 50%;
  min-height: 100px;
  max-height: 80%;
  background: var(--text-color);
  color: var(--white);
  padding: 50px;
  font-weight: var(--font-weight-light);
  border-radius: 5px;
  overflow: auto;
  box-shadow: 0px 0px 5px 1px rgba(0, 0, 0, 0.25);

  @media (--tablet) {
    max-width: 80%;
  }

  @media (--mobile) {
    max-width: 100%;
    max-height: 90%;
    padding: 25px;
  }

  & h1 {
    margin-top: 0;
    text-align: center;
  }

  & small {
    @apply --small-font;
    display: block;
    margin-top: 10px;
  }

  & a {
    color: var(--main-color);
  }
}

.close {
  position: absolute;
  top: 5px;
  right: 10px;
  cursor: pointer;
  font-size: 25px;
}
</style>
