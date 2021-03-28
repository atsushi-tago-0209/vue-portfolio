<template>
  <div style="width: 700px;margin: 0 auto;padding-top: 50px;">
    <h3>Users</h3>
    <router-link to="/users/1">ユーザー１</router-link>
    <router-link to="/users/2">ユーザー２</router-link>
    <hr>
    <router-link :to="'/users/'+(Number(id)+1)+'/profile'">次のユーザー</router-link>
    <router-link :to="{ name: 'users-id-profile',params: { id: Number(id)+ 1 },query:{ lang:'ja',page: 2 } }">次のユーザー</router-link>
    <h1>User.No {{ id }}</h1>
  </div>
</template>

<script>
export default {
  props: ['id'],
};
</script>