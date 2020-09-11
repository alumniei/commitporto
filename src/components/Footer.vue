<template>
  <footer>
    <div class="editions">
      <a href="http://previous.commitporto.com/2019" target="_blank">2019</a>.
      <a href="http://2018.commitporto.com" target="_blank">2018</a>.
      <a href="http://2017.commitporto.com" target="_blank">2017</a>.
      <a href="http://2016.commitporto.com" target="_blank">2016</a>.
      <a href="http://2015.commitporto.com" target="_blank">2015</a>
    </div>
    <div class="organizer">Powered by
      <a href="http://alumniei.pt/" target="_blank">AlumniEI-FEUP</a>
    </div>
    <div class="socials">
      <a href="https://www.facebook.com/commitportoconf" target="_blank">
        <img src="@/assets/social/facebook.svg" />
      </a>
      <a href="https://www.instagram.com/commitportoconf" target="_blank">
        <img src="@/assets/social/instagram.svg" />
      </a>
      <a href="https://twitter.com/commitportoconf" target="_blank">
        <img src="@/assets/social/twitter.svg" />
      </a>
      <a href="https://www.youtube.com/channel/UCuYn5xuAmChRDcSdQrbp-Fw/videos" target="_blank">
        <img src="@/assets/social/youtube.svg" />
      </a>
    </div>
  </footer>
</template>

<script>
export default {
  name: 'Footer',
};
</script>

<style>
@import '../variables';

footer {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: var(--small-space);
  padding-left: 100px;
  padding-right: 100px;
  background: var(--main-color);
  position: relative;

  @media (--bellow-desktop) {
    margin: 0;
    text-align: center;
    flex-direction: column-reverse;
    background: var(--main-color);
  }
}

.socials {
  @media (--bellow-desktop) {
    margin-bottom: var(--small-space);
  }

  & a:not(:last-child) {
    margin-right: 20px;
  }

  & img {
    filter: brightness(0) invert(1);
  }
}

.editions {
  @apply --small-font;
  margin-top: 5px;
  color: var(--white);

  & a {
    text-decoration: none;
    color: var(--white);

    &:not(:first-child) {
      padding-left: 5px;
    }

    &:not(:last-child){
      padding-right: 5px;
    }
  }
}

.organizer {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);

  &, & a {
    color: var(--white);
    font-size: var(--text-font);
    text-decoration: none;
  }
}

</style>
