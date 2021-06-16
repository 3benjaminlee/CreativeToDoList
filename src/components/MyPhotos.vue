<template>
<div class="main">
  <div class="menu">
    <p><a></a></p>
    <h1>{{user.firstName}} {{user.lastName}} <a @click="logout"><i class="fas fa-sign-out-alt"></i></a></h1>
  </div>
</div>
</template>

<script>
import axios from 'axios';
export default {
  name: 'MyPhotos',
  data() {
    return {}
  },
  computed: {
    user() {
      return this.$root.$data.user;
    },
  },
  methods: {
    async logout() {
      try {
        await axios.delete("/api/users");
        this.$root.$data.user = null;
      } catch (error) {
        this.$root.$data.user = null;
      }
    },
  }
}
</script>

<style scoped>
.menu {
  display: flex;
  justify-content:center;
}

.menu h2 {
  font-size: 14px;
}
</style>

