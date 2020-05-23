<template>
  <section>
    <div class="form-container">
      <h2>Add User</h2>
      <form @submit.prevent="addUser">
        <div>
          <label>Name</label>
          <br />
          <input v-model="state.input" type="text" />
        </div>

        <div>
          <button type="submit" class="submit">Add User</button>
        </div>
      </form>
    </div>
    <div class="list-container">
      <ul v-for="(user,index) in state.users" :key="index">
        <li>
          {{user}}
          <span style="float:right;padding-right:10px;">
            <button @click="removeUser(index)">X</button>
          </span>
        </li>
      </ul>
    </div>
  </section>
</template>
<script>
import { reactive } from "@vue/composition-api";
export default {
  setup() {
    const { state, addUser, removeUser } = userList();
    return { state, addUser, removeUser };
  }
};
function userList() {
  let state = reactive({
    input: "",
    users: ["Wisdom"]
  });

  let addUser = () => {
    state.users.push(state.input);
    state.input = "";
  };
  let removeUser = i => {
    state.users.splice(i, 1);
  };
  return { state, addUser, removeUser };
}
</script>

<style scoped>
input {
  width: 20%;
  height: 30px;
  border: 2px solid green;
}
.submit {
  margin: 10px;
  padding: 10px;
  border-radius: 0px;
  border: 0px;
  background: green;
  color: white;
}

ul li {
  list-style: none;
  border: 2px solid green;
  width: 30%;
  margin-top: 10px;
}
</style>