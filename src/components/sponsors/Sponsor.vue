<template>
  <a
    :href="link"
    target="_blank"
  >
    <img :src="require(`@/assets/sponsors/` + imagePath)" />
  </a>
</template>

<script>
export default {
  name: 'Sponsor',
  props: ['link', 'imagePath'],
  methods: {
    imgLink(fileName) {
      return `@/assets/sponsors/${fileName}`;
    },
  },
};
</script>
