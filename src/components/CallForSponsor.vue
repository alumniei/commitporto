<template>
  <div>
    <h1>Call for Sponsors</h1>
    <div v-if="!submitted">
      <small>
        Commit Porto is a tech conference that brings together professionals who tackle challenges
        in software development with the latest technologies. Now in its fifth edition the
        conference is only possible due to the generous support of our sponsors.
      </small>
      <small>
        Together we are able to invite a high quality panel of speakers from different backgrounds
        that have in common a love for technology and for sharing their knowledge with our
        participants.
      </small>
      <small>
        If your company wants to be part of Commit Porto ’20, you can reach out to us via the form
        bellow. Find all we have to offer in our prospectus.
      </small>
      <form class="form" @submit.prevent="submitForm">
        <input v-model="name" placeholder="tell us your name" required>
        <input
          v-model="email"
          placeholder="email address where we can reach you"
          type="email"
          required
        >
        <Button text="Send" isSecondary={true} type="submit" />
      </form>
    </div>
    <span v-if="submitted">Thanks for your interest! We will reach you as soon as possible!</span>
    <small>
      We are also happy to answer any questions via our email
      <a href="mailto:partnerships@commitporto.com">partnerships@commitporto.com</a>.<br/>
      Let’s put tech in the center stage of Porto.
    </small>
  </div>
</template>

<script>
import Button from '@/components/common/Button';

export default {
  name: 'CallForSponsor',
  data: () => ({
    name: '',
    email: '',
    submitted: false,
  }),
  methods: {
    submitForm() {
      const url = 'https://hooks.slack.com/services/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';
      const data = JSON.stringify({ text: `Chamo-me ${this.name} e quero patrocinar a commitporto:commitporto:! Enviem-me o prospectus para: ${this.email} (cc <!here>)` });

      this.$http.post(
        url,
        data,
        { headers: { 'Content-Type': 'application/x-www-form-urlencoded' } },
      ).then(() => {
        this.submitted = true;
        this.name = '';
        this.email = '';
      });
    },
  },
  components: {
    Button,
  },
};
</script>

<style scoped>
@import '../variables';

.form {
  display: flex;
  text-align: center;
  margin-top: 20px;
  margin-bottom: 20px;

  & input {
    flex-grow: 1;
    flex-basis: 0;
    margin-right: 20px;
    border: 1px solid var(--text-color);
    padding: 5px;
  }

  @media (--mobile) {
    flex-direction: column;

    & input {
      margin-right: 0;

      &:not(:first-child) {
        margin-top: 10px;
        margin-bottom: 10px;
      }
    }
  }
}
</style>
