<template>
  <div class="feature-posts">
    <h1>Posts</h1>
    <select v-model="selectedUser" @change="fetchPosts">
      <option v-for="user in users" :key="user.id" :value="user.id">{{ user.name }}</option>
    </select>
    <ul>
      <li v-for="post in posts" :key="post.id">
        <h2>{{ post.title }}</h2>
        <p>{{ post.body }}</p>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'Posts',
  data() {
    return {
      users: [],
      selectedUser: null,
      posts: []
    };
  },
  methods: {
    fetchUsers() {
      fetch('https://jsonplaceholder.typicode.com/users')
        .then(response => response.json())
        .then(data => {
          this.users = data;
          this.selectedUser = data[0]?.id; // Set default selected user to the first one
          this.fetchPosts();
        })
        .catch(error => console.error('Error fetching users:', error));
    },
    fetchPosts() {
      if (!this.selectedUser) return;
      fetch(`https://jsonplaceholder.typicode.com/posts?userId=${this.selectedUser}`)
        .then(response => response.json())
        .then(data => {
          this.posts = data;
        })
        .catch(error => console.error('Error fetching posts:', error));
    }
  },
  created() {
    this.fetchUsers();
  }
};
</script>

<style scoped>
/* Style yang relevan dari App.vue */
</style>

