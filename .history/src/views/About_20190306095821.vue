<template>
  <div class="about">
    <h1>Colors</h1>
    <table>
      <ul class="list-group">
        <li
          class="list-group-item"
          style ="color:(u.color) "
          v-for="(u,index) in users"
          :key="index"
        >
        {{u.username}} - {{u.mail}} -{{u.color}}
        </li>
      </ul>
    </table>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
return {
users: []
};
},
  mounted() {
    axios
      .get("https://vue-test-ebf88.firebaseio.com/data.json")
      .then(response => {
        console.log(response);
        const data = response.data;
        for (let key in data) {
          const user = data[key];
          user.id = key;
          this.users.push(user);
        }
      })
      .catch(error => {
        console.log(error);
      });
  }
};
</script>


