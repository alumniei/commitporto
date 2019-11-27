<template>
  <div>
    <div class="bio-section">
      <div class="bio-photo">
        <img :src="require(`@/assets/speakers/` + fullfileName)"/>
      </div>
      <div class="bio-details">
        <Title :title="name" :subtitle="role" />
        <div class="bio">{{bio}}</div>
      </div>
    </div>
    <div class="talk-section">
      <div class="talk-title">{{title}}</div>
      <div class="talk" v-html="abstract"></div>
    </div>
  </div>
</template>

<script>
import Title from '@/components/common/Title';

export default {
  name: 'SpeakerModal',
  components: {
    Title,
  },
  props: ['fullfileName', 'role', 'name', 'bio', 'title', 'abstract'],
};
</script>

<style scoped>
@import '../../variables';

.bio-section {
  display: flex;

  @media (--bellow-desktop) {
    flex-direction: column;
  }
}

.bio-photo {
  max-height: 100%;
  max-width: 100%;
  overflow: hidden;
  flex-shrink: 0;
}

.bio-details {
  padding-left: var(--space);
}

.bio {
  font-size: var(--text-font);
  line-height: 1.5;
}

.talk-section {
  margin-top: var(--space);
}

.talk-title {
  font-weight: bold;
  font-size: var(--large-font);
}

.talk {
  font-size: var(--text-font);
  margin-top: var(--small-space);
  line-height: 1.5;
}
</style>
