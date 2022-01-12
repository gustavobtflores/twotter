<template>
  <header class="user-profile__header">
    <router-link to="/">
      <h1 class="user-profile__header-title">Twooter</h1>
    </router-link>
  </header>
</template>

<script>
export default {
  name: "Header",
};
</script>

<style lang="scss" scoped>
@use "../styles/scss/variables";

.user-profile__ {
  &header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 16px 5%;
    background-color: variables.$color-primary;

    &-title {
      font-size: 32px;
      color: variables.$color-texts;
    }

    &-username {
      color: variables.$color-texts;
      font-weight: 600;
    }
  }
}
</style>
