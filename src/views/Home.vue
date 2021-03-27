<template>
  <div style="width: 700px;margin: 0 auto;padding-top: 50px;">
    <h3>Home</h3>
    <button @click="toUsers">Usersのページにいく</button>
  </div>
</template>

<script>
export default {
  methods: {
    toUsers(){
      this.$router.push('users');
    }
  },
}
</script>