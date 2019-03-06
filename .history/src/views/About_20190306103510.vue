<template>
  <div class="about">
    <h1>Colors</h1>
    <table>
      <ul class="list-group">
        <li
          class="list-group-item"
          style="color: [u.color]"
          v-for="(c,index) in colors"
          :key="index"
          
        >
        {{u.username}} - {{c.color}}
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
          const color = data[key];
          color.id = key;
          this.colors.push(color);
        }
      })
      .catch(error => {
        console.log(error);
      });
  }
};
</script>


