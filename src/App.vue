<template>
  <div>
    <nav>
      <router-link
        to="/"
        class="link"
        active-class="link-active"
        exact
      >Home</router-link>
      <router-link 
        to="/users"
        class="link"
        exact
        active-class="link-active"
      >Users</router-link>
    </nav>
    <router-view></router-view>
  </div>
</template>

<style scoped>
  .link{
    margin-right: 10px;
  }
  .link-active{
    font-size: 20px;
  }
</style>