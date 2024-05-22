<template>
  <div class="iphone-cell">
    <header>
      <nav>
        <ul>
          <li>
            <a href="#" @click.prevent="activeFeature = 'todos'">Todos</a>
          </li>
          <li>
            <a href="#" @click.prevent="activeFeature = 'posts'">Posts</a>
          </li>
        </ul>
      </nav>
    </header>
    <Todos v-if="activeFeature === 'todos'" :iphone-types="iphoneTypes" :new-iphone-type="newIphoneType" :show-only-incomplete="showOnlyIncomplete" @add-iphone-type="addIphoneType" @delete-iphone-type="deleteIphoneType"/>
    <Posts v-if="activeFeature === 'posts'" :users="users" :selected-user="selectedUser" :posts="posts" @user-changed="fetchPosts"/>
  </div>
</template>

<script>
import Todos from './components/Todos.vue';
import Posts from './components/Posts.vue';

export default {
  name: 'App',
  components: {
    Todos,
    Posts
  },
  data() {
    return {
      activeFeature: 'todos', // Default active feature
      iphoneTypes: [],
      newIphoneType: '',
      showOnlyIncomplete: false,
      users: [],
      selectedUser: null,
      posts: []
    };
  },
  methods: {
    addIphoneType() {
      // Logika untuk menambahkan tipe iphone
    },
    deleteIphoneType(index) {
      // Logika untuk menghapus tipe iphone
    },
    fetchPosts(userId) {
      // Logika untuk mengambil posts berdasarkan user
    }
  },
  created() {
    // Panggil API atau inisialisasi data di sini
  }
};
</script>

<style scoped>
.iphone-cell {
  max-width: 800px;
  margin: 40px auto;
  padding: 20px;
  background-color: #f9f9f9;
  border: 1px solid #ddd;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

.feature-todos, .feature-posts {
  padding: 20px;
}

.input-group {
  margin-bottom: 20px;
}

.input-group input[type="text"] {
  width: 50%;
  padding: 10px;
  font-size: 16px;
  border: 1px solid #ccc;
}

.input-group button {
  padding: 10px 20px;
  font-size: 16px;
  background-color: #4CAF50;
  color: #fff;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

.iphone-types-list {
  margin-bottom: 20px;
}

.iphone-types-list div {
  display: flex;
  align-items: center;
  margin-bottom: 10px;
}

.iphone-types-list div span {
  flex: 1;
  margin-left: 10px;
}

.filter-group {
  display: flex;
  align-items: center;
}

.filter-group label {
  margin-right: 10px;
}
</style>
