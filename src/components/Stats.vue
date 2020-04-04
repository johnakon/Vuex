<template>
  <div class="stats">
    <h3 class="header-text">Here are your numbers, {{ username }} 😬</h3>
    <p class="header-text">You need to perform {{ taskCount }} tasks!</p>
    <button class="" @click="removeAllTasks">Nope, can't even ...</button>
    <p class="header-text">{{ message }}</p>
  </div>
</template>

<script>
import { mapGetters, mapActions, mapMutations, mapState } from "vuex";

export default {
  name: "Stats",
  computed: {
    ...mapGetters(["taskCount"]),
    ...mapState(["username"])
  },
  data() {
    return {
      message: ""
    };
  },
  methods: {
    ...mapMutations(["Remove_all"]),
    ...mapActions(["removeAll"]),

    //removing all tasks
    removeAllTasks() {
      this.removeAll().then(() => {
        this.message = "self care, tasks are gone";
      });
    }
  }
};
</script>

<style scoped>
button {
  padding: 5px;
  margin-top: 5px;
  border-radius: 3px;
  background-color: #0cf50cbb;
  cursor: pointer;
}

.header-text {
  color: #e9e9e9;
}
</style>
