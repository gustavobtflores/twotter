<template>
  <div class="user-profile">
    <div class="user-profile__user-panel">
      <h1 class="user-profile__username">{{ user.username }}</h1>
      <div class="user-profile__user-infos">
        <div class="user-profile__follower-count">
          Followers: {{ this.followers }}
        </div>
        <span v-if="user.isAdmin" class="user-profile__admin-badge">admin</span>
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
    pushNewTwoot({newTwootContent, selectedTwootType}) {
      var twoots = this.user.twoots;
      if(selectedTwootType === 'instant') twoots.push({ id: twoots.length + 1, content: newTwootContent });
      return;
    },
  },
};
</script>

<style scoped>
.user-profile {
  display: grid;
  grid-template-columns: 1fr 3fr;
  width: 100%;
  padding: 50px 5%;
}

.user-profile__user-panel {
  display: flex;
  align-items: flex-start;
  flex-direction: column;
  margin-right: 50px;
  padding: 20px;
  background-color: #ffffff;
  border-radius: 4px;
  border: 1px solid #dfe3e8;
}

.user-profile__user-infos {
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 100%;
}

.user-profile__admin-badge {
  border: 2px solid orange;
  border-radius: 8px;
  padding: 0 8px;
  background-color: #fed8b1;
}

.user-profile__twoots-wrapper {
  display: flex;
  flex-direction: column;
  width: 90%;
  gap: 16px;
}

h1 {
  margin: 0;
}
</style>
