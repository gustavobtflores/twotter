<template>
  <div class="user-profile__create-twoot">
    <form
      class="user-profile__create-twoot-form"
      @submit.prevent="emitNewTwoot(newTwootContent, selectedTwootType)"
      @keydown.enter.exact.prevent="
        emitNewTwoot(newTwootContent, selectedTwootType)
      "
      :class="{ '--exceeded': newTwootCharactersCount > 180 }"
    >
      <label for="newTwoot"
        ><strong>New twoot ({{ newTwootCharactersCount }}/180)</strong></label
      >
      <textarea v-model="newTwootContent" id="newTwoot" rows="4"></textarea>
      <div class="user-profile__twoot-submit">
        <div class="user-profile__twoot-type">
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
        </div>
        <button type="submit">Twoot it!</button>
      </div>
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
      this.newTwootContent = "";
      return;
    },
  },
  computed: {
    newTwootCharactersCount() {
      return this.newTwootContent.length;
    },
  },
};
</script>

<style lang="scss" scoped>
@use "../styles/scss/variables";

.user-profile__create-twoot {
  width: 100%;
}

.user-profile__create-twoot-form {
  display: flex;
  flex-direction: column;
  margin-top: 20px;
  text-align: left;
}

.user-profile__create-twoot-form.--exceeded textarea {
  border: 2px solid red;
  outline: red;
  color: red;
}

.user-profile__create-twoot-form textarea {
  margin: 8px 0 16px;
  border: 1px solid #cecece;
  resize: none;
  box-shadow: rgba(0, 0, 0, 0.16) 0px 1px 4px;
  padding: 8px;
}

.user-profile__create-twoot-form button {
  background-color: variables.$color-primary;
  border: none;
  padding: 4px 16px;
  border-radius: 4px;
  color: #ffffff;
  cursor: pointer;
}

.user-profile__twoot-submit {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.user-profile__twoot-type {
  display: flex;
  align-items: center;
  gap: 4px;
}
</style>
