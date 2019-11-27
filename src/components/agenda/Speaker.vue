<template>
  <div class="speaker" :class="{placeholder: !name}" @click="openSpeakerModal">
    <img class="photo" :src="require(`@/assets/speakers/` + fullfileName)"/>
    <div class="time">{{time}}</div>
    <div class="name" @click="openSpeakerModal">{{name}}</div>
    <div class="role">{{role}}</div>
    <div class="social">
      <a v-if="twitter" :href="twitterLink" target="_blank">
        <img src="@/assets/social/twitter.svg" />
      </a>
      <a v-if="github" :href="githubLink" target="_blank">
        <img src="@/assets/social/github.svg" />
      </a>
      <a v-if="linkedin" :href="linkedinLink" target="_blank">
        <img src="@/assets/social/linkedin.svg" />
      </a>
      <a v-if="website" :href="website" target="_blank">
        <img src="@/assets/social/link.svg" />
      </a>
    </div>
    <div class="speaker-hover">
      <div class="hovered-time">{{time}}</div>
      <div class="hovered-talk">{{title}}</div>
    </div>
  </div>
</template>

<script>
import SpeakerModal from './SpeakerModal';

export default {
  name: 'Speaker',
  props: [
    'file',
    'name',
    'role',
    'bio',
    'title',
    'abstract',
    'twitter',
    'github',
    'linkedin',
    'website',
    'openSpeakerDetails',
    'content',
    'type',
    'time',
  ],
  computed: {
    fullfileName() {
      return this.file;
    },
    twitterLink() {
      return `https://twitter.com/${this.twitter}`;
    },
    githubLink() {
      return `https://github.com/${this.github}`;
    },
    linkedinLink() {
      return `https://www.linkedin.com/in/${this.linkedin}`;
    },
  },
  methods: {
    openSpeakerModal() {
      const { fullfileName, role, name, bio, title, abstract } = this;
      this.openSpeakerDetails(SpeakerModal, { fullfileName, role, name, bio, title, abstract });
    },
  },
};
</script>

<style scoped>
@import '../../variables';

.speaker {
  display: inline-block;
  text-align: center;
  margin-bottom: var(--space);
  position: relative;
  width: 200px;

  @media (--desktop) {
    grid-column: span 2;

    &:nth-child(3n+9) {
      grid-column: 2 / 4;
    }
  }

  &.placeholder {
    @media (--bellow-desktop) {
      display: none;
    }
  }

  &:not(.placeholder) {
    cursor: pointer;
  }

  & .time {
    position: absolute;
    right: 0;
    top: 150px;
    background: var(--main-color);
    color: var(--white);
    padding: 0  var(--x-small-space);
  }

  &:hover {
    & .speaker-hover {
      opacity: 1;
    }

    & .photo {
      opacity: 0;
    }

    & .time {
      opacity: 0;
    }
  }
}

.photo {
  width: 200px;
  transform: translate3d(0, 0, 0);
  transition: opacity 0.35s, transform 0.35s;
}

.speaker-hover {
  opacity: 0;
  position: absolute;
  top: 0;
  width: 200px;
  height: 200px;
  left: 50%;
  transform: translateX(-50%);
  transition: opacity 0.35s;
  background-color: var(--main-color);
  color: var(--white);
}

.hovered-time {
  padding: 0 var(--small-space);
  margin-top: var(--space);
  text-align: left;
}

.hovered-talk {
  @apply --small-font;
  font-weight: lighter;
  text-align: left;
  padding: var(--small-space);
}

.name {
  text-transform: uppercase;
  color: var(--text-color);
  font-size: var(--medium-font);
}

.role {
  @apply --small-font;
  color: var(--text-color);
}

.social img {
  width: 15px;
  margin: 5px;
  transition : filter 300ms ease;

  &:hover {
    filter: var(--red-filter);
  }
}
</style>

