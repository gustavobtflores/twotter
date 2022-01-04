<template>
  <div class="user-profile__twoot" @click="favouriteTwoot(twoot.id)">
    <span class="user-profile__twoot-user"> @{{ username }} </span>
    <p class="user-profile__twoot-content">{{ twoot.content }}</p>
  </div>
</template>

<script>
export default {
  name: "TwootItem",
  props: {
    username: {
      type: String,
      required: true,
    },
    twoot: {
      type: Object,
      required: true,
    },
  },
  methods: {
    favouriteTwoot(id) {
      this.$emit("favourite", id);
    },
  },
};
</script>

<style scoped>
.user-profile__twoot {
  display: flex;
  align-items: flex-start;
  flex-direction: column;
  padding: 20px;
  background-color: #ffffff;
  border-radius: 4px;
  border: 1px solid #dfe3e8;
  text-align: left;
  cursor: pointer;
  line-height: 1.5em;
  transition: transform 0.2s ease-in-out;
}

.user-profile__twoot:hover {
  transform: scale(1.05);
}

.user-profile__twoot-user {
  font-weight: 600;
  font-size: 16px;
}

.user-profile__twoot-content {
  font-size: 14px;
  margin: 0;
  margin-top: 4px;
}
</style>
