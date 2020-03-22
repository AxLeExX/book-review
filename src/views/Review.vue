<template>
<div>
  <h1>Write a Review</h1>
  <form v-if="creating" @submit.prevent="addReview">
    <input v-model="name" placeholder="Name">
    <p></p>
    <textarea v-model="rating"></textarea>
    <textarea v-model="review"></textarea>
    <br />
    <button type="submit">Submit</button>
  </form>
  <div v-else>
    <p>Thank you for submitting a review!</p>
    <p><a @click="toggleForm" href="#">Write another review</a></p>
  </div>
</div>
</template>

<script>
export default {
  name: 'review',
  data() {
    return {
      creating: true,
      name: '',
      rating: '',
      review: '',
    }
  },
  methods: {
    toggleForm() {
      this.creating = !this.creating;
    },
    addReview() {
      this.$root.$data.addReview(this.name, this.rating, this.review);
      this.name = "";
      this.rating = "";
      this.review = "";
      this.creating = false;
    },
  }
}
</script>

<style scoped>
input {
  font-size: 1.2em;
  height: 30px;
  width: 200px;
}

textarea {
  font-size: 1.6em;
  width: 100%;
  max-width: 500px;
  height: 100px;
}

button {
  margin-top: 20px;
  font-size: 1.2em;
}
</style>
