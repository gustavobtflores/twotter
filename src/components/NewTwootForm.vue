<template>
  <div class="user-profile__create-twoot">
    <form
      class="user-profile__create-twoot-form"
      @submit.prevent="emitNewTwoot(newTwootContent, selectedTwootType)"
      :class="{ '--exceeded': newTwootCharactersCount > 180 }"
    >
      <label for="newTwoot"
        ><strong>New twoot ({{ newTwootCharactersCount }}/180)</strong></label
      >
      <textarea v-model="newTwootContent" id="newTwoot" rows="4"></textarea>
      <label for="newTwootType">Type:</label>
      <select id="newTwootType" v-model="selectedTwootType">
        <option
          :value="option.value"
          v-for="(option, index) in twootTypes"
          :key="index"
        >
          {{ option.name }}
        </option>
      </select>
      <button type="submit">Twoot</button>
    </form>
  </div>
</template>

<script>
export default {
  name: "NewTwootForm",
  data() {
    return {
      newTwootContent: "",
      selectedTwootType: "instant",
      twootTypes: [
        { value: "draft", name: "Draft" },
        { value: "instant", name: "Instant Twoot" },
      ],
    };
  },
  methods: {
    emitNewTwoot(newTwootContent, selectedTwootType) {
      var newTwoot = { newTwootContent, selectedTwootType };
      this.$emit("newTwoot", newTwoot);
    },
  },
  computed: {
    newTwootCharactersCount() {
      return this.newTwootContent.length;
    },
  },
};
</script>

<style scoped>
.user-profile__create-twoot {
  width: 100%;
}

.user-profile__create-twoot-form {
  display: flex;
  flex-direction: column;
  margin-top: 10px;
  padding-top: 10px;
  border-top: 1px solid #eeeeee;
  text-align: left;
}

.user-profile__create-twoot-form.--exceeded textarea {
  border: 2px dotted red;
  outline: red;
  color: red;
}

.user-profile__create-twoot-form textarea {
  margin-bottom: 8px;
}
</style>
