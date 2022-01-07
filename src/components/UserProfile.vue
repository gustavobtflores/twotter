<template>
  <div class="user-profile">
    <div class="user-profile__user-panel">
      <div class="user-profile__user-panel-wrapper">
        <h1 class="user-profile__username">@{{ user.username }}</h1>
        <div class="user-profile__user-infos">
          <div class="user-profile__follower-count">
            Followers: {{ this.followers }}
          </div>
          <span v-if="user.isAdmin" class="user-profile__admin-badge"
            >admin</span
          >
        </div>
      </div>
      <NewTwootForm @newTwoot="pushNewTwoot" />
    </div>
    <div class="user-profile__twoots-wrapper">
      <TwootItem
        v-for="twoot in user.twoots"
        :key="twoot.id"
        :username="user.username"
        :twoot="twoot"
        @favourite="toggleFavourite"
      />
    </div>
  </div>
</template>

<script>
import TwootItem from "./TwootItem";
import NewTwootForm from "./NewTwootForm";

export default {
  name: "UserProfile",
  components: { TwootItem, NewTwootForm },
  data() {
    return {
      followers: 0,
      user: {
        id: 1,
        username: "gustavobtflores",
        firstName: "Gustavo",
        lastName: "Flores",
        email: "example@example.com",
        isAdmin: true,
        twoots: [
          { id: 1, content: "Twoot is amazing, loving it!" },
          {
            id: 2,
            content: "Look how the sky is beatiful today!",
          },
        ],
      },
    };
  },
  mounted() {},
  computed: {
    fullName() {
      return `${this.user.firstName} ${this.user.lastName}`;
    },
  },
  methods: {
    followUser() {
      this.followers++;
    },
    toggleFavourite(id) {
      console.log(`Favourited twoot #${id}`);
    },
    pushNewTwoot({ newTwootContent, selectedTwootType }) {
      var twoots = this.user.twoots;
      if (selectedTwootType === "instant")
        twoots.push({ id: twoots.length + 1, content: newTwootContent });
      return;
    },
  },
};
</script>

<style scoped>
h1 {
  margin: 0;
}

.user-profile {
  display: grid;
  grid-template-columns: 1fr 3fr;
  width: 100%;
  padding: 50px 5%;
}

.user-profile__username {
  font-size: 32px;
  font-weight: 600;
}

.user-profile__user-panel {
  display: flex;
  flex-direction: column;
  margin-right: 20px;
  background-color: #ffffff;
}

.user-profile__user-panel-wrapper {
  border: 1px solid #dddddd;
  padding: 20px;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
}

.user-profile__user-infos {
  display: flex;
  margin-top: 8px;
  flex-direction: column;
  gap: 4px;
}

.user-profile__admin-badge {
  border-radius: 8px;
  padding: 4px 8px;
  background-color: #9f33ff;
  color: #ffffff;
}

.user-profile__twoots-wrapper {
  display: flex;
  flex-direction: column-reverse;
  width: 90%;
  gap: 16px;
  justify-content: flex-end;
}
</style>
