<template>
  <div class="homepage">
    <div class="container">
      <div class="background">
        <div class="bckg-img" />
      </div>
      <div class="logo-section">
        <img class="logo" src="@/assets/logobrancohor.png"/>
        <div class="time">6th June 2020</div>
        <!--<a class="location" href="https://goo.gl/maps/Bcr3WfwoUasc1vg2A" target="_blank">
          <img src="@/assets/location.svg" />FEUP
        </a>
        <Button id="eventbrite-widget-modal-trigger-61719447529" text="Get your tickets now" />
        -->
      </div>
      <div class="cta-section">
        <Button text="Call for sponsors" :onClick="openCallForSponsorsModal" />
        <Button text="Call for speakers" :onClick="openCallForSpeakersModal" />
      </div>
    </div>
    <!--<AboutUs />
    <div class="gallery">
      <img src="@/assets/gallery/gallery_1.jpg" />
      <img src="@/assets/gallery/gallery_2.jpg" />
      <img src="@/assets/gallery/gallery_3.jpg" />
      <img src="@/assets/gallery/gallery_6.jpg" />
      <img src="@/assets/gallery/gallery_9.jpg" />
      <img src="@/assets/gallery/gallery_7.jpg" />
      <img src="@/assets/gallery/gallery_11.jpg" />
      <img src="@/assets/gallery/gallery_8.jpg" />
      <img src="@/assets/gallery/gallery_4.jpg" />
      <img src="@/assets/gallery/gallery_10.jpg" />
    </div>-->
    <!-- <Agenda :openSpeakerDetails="openSpeakerDetails" /> -->
    <!-- <Sponsors /> -->
  </div>
</template>

<script>
import Button from '@/components/common/Button';
import AboutUs from '@/components/AboutUs';
import CallForSponsor from '@/components/CallForSponsor';
import CallForSpeaker from '@/components/CallForSpeaker';
import Agenda from '@/components/agenda/';
import Sponsors from '@/components/sponsors/';

export default {
  name: 'Homepage',
  components: {
    Button,
    AboutUs,
    Agenda,
    Sponsors,
  },
  methods: {
    openSpeakerDetails(component, properties) {
      this.$emit('modalVisible', component, properties);
    },
    openCallForSponsorsModal() {
      this.$emit('modalVisible', CallForSponsor, {});
    },
    openCallForSpeakersModal() {
      this.$emit('modalVisible', CallForSpeaker, {});
    },
  },
};
</script>

<style scoped>
@import '../variables';

.container {
  position: relative;
  height: 100vh;
  color: var(--white);
  box-shadow: 0px 0px 3px 2px rgba(0, 0, 0, 0.25);
  overflow: hidden;

  @media (--mobile) {
    height: 85vh;
  }
}

.bckg-img {
  background: var(--text-color) url('../assets/bckg.jpg') no-repeat center center / cover;
  width: 100%;
  height: 100vh;
  filter: var(--red-filter);
  opacity: 1;
  transition: opacity 1s ease;

  &.hide {
    opacity: 0;
    width: 0;
    height: 0;
  }
}

.logo-section {
  position: absolute;
  top: 45%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 100%;
  text-align: center;

  & .logo {
    width: 40%;

    @media (--tablet) {
      width: 70%;
    }

    @media (--mobile) {
      width: 90%;
    }
  }

  & .time {
    font-family: var(--secondary-font);
    font-size: var(--medium-font);
    margin-top: var(--small-space);;
    margin-bottom: var(--x-small-space);

  }

  & .location {
    font-family: var(--main-font);
    font-size: var(--medium-font);
    display: flex;
    align-items: center;
    justify-content: center;
    margin-top: var(--x-small-space);
    margin-bottom: var(--small-space);;
    color: var(--white);
    text-decoration: none;

    &:hover {
      & img {
        animation: spin 2s linear infinite;
      }
    }

    & img {
      width: 20px;
      margin-right: var(--x-small-space);
    }
  }
}

.cta-section {
  position: absolute;
  bottom: 60px;
  width: 100%;
  transform: translateY(-500%);
  text-align: center;
  & > button:not(:last-child) {
    margin-right: 5%;
  }
}

.gallery {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  filter: grayscale(0.4);
  margin: 140px auto 0;

  & img {
    max-width: 100%;
  }

  @media (--bellow-desktop) {
    margin: 100px auto 0;
    grid-template-columns: repeat(2, 1fr);

    & img:nth-child(n + 5) {
      display: none;
    }
  }
}

@keyframes spin {
  100% {
    transform: rotateY(360deg)
  }
}
</style>
