<template>
  <div id="app" class="container">
    <div class="row">
      <div class="col-8">
        <ul class="nav py-3">
          <li class="nav-item">
            <a class="nav-link active" href="#">Active</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#">Link</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#">Link</a>
          </li>
        </ul>
      </div>
    </div>

    <div class="row">
      <div class="col-8">
        <p>{{ user.length }}</p>
        <p v-for="u in user" :key="u.id">
          {{ u }}
        </p>
      </div>
    </div>

    <HelloWorld v-bind:users="user" msg="Javascript" />
    <Menu v-on:termChange="onTermChange"></Menu>
  </div>
</template>

<script>
import axios from "axios";
import HelloWorld from "./components/HelloWorld.vue";
import Menu from "./components/Menu.vue";

export default {
  data: function() {
    return {
      user: [],
    };
  },
  name: "App",
  components: {
    HelloWorld,
    Menu,
  },
  methods: {
    onTermChange: function() {
      axios.get("https://jsonplaceholder.typicode.com/users").then((res) => {
        console.log(res.data);
        res.data.map((r) => this.user.push(r.name));
      });
    },
  },
};
</script>

<style></style>
