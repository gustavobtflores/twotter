<template>
  <h1>Home</h1>
  <div class="users-list">
    <router-link
      v-for="user in users"
      :to="{ name: 'UserProfile', params: { userId: user.id } }"
      :key="user.userId"
    >
      {{ user.username }}
    </router-link>
  </div>
</template>

<script>
import { users } from "../assets/users.js";

export default {
  name: "Home",
  data() {
    return {
      users,
    };
  },
};
</script>

<style lang="scss" scoped>
@use "../styles/scss/variables";

h1 {
  color: #2c3e50;
  font-size: 2rem;
  font-weight: 600;
  padding: 5% 5%;
}

.users-list {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  flex-direction: column;
}
</style>
