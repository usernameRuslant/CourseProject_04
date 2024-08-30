<template>
  <main>
    <div v-if="articles.length > 0" id="articles">
      <div class="post" v-for="el in articles" :key="el.id">
        <button @click="deletePost(el.id)">Удалить</button>
        <h2>{{ el.title }}</h2>
        <p>{{ el.text }}</p>
      </div>
    </div>
    <h1 class="empty" v-else>Статей нет</h1>
  </main>
  <aside>
    <AddPost v-on:add-post="createPost" />
  </aside>
</template>
<script>
import AddPost from './AddPost.vue';
export default {
  name: 'Articles',
  components: { AddPost },
  data() {
    return {
      articles: [
        {
          id: 1,
          title: 'Google buy Apple',
          text: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Quos, odit!',
        },
        {
          id: 2,
          title: 'Microsoft kills Minecraft',
          text: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Quos, odit!',
        },
        {
          id: 3,
          title: 'Testing articles',
          text: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Quos, odit!',
        },
        {
          id: 4,
          title: 'Tesla is now phone company',
          text: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Quos, odit!',
        },
      ],
    };
  },
  methods: {
    deletePost(id) {
      this.articles = this.articles.filter((el) => el.id !== id);
    },
    createPost(userTitleInput, userTextInput) {
      this.articles.unshift({
        id: this.articles.length + 1,
        title: userTitleInput,
        text: userTextInput,
      });
    },
  },
};
</script>
<style scoped>
main {
  float: left;
  width: 60%;
}
aside {
  float: left;
  width: 20%;
  margin-left: 10%;
}
#articles {
  margin: 20px;
}
#articles .post {
  background: #c6c391;
  padding: 20px;
  margin-bottom: 20px;
  border: 1px solid #aaa771;
  color: #5e5b21;
  float: left;
  width: 100%;
}
#articles .post button {
  float: right;
  background: #aaa771;
  border: 2px solid #5e5b21;
  border-radius: 5px;
  border-bottom-width: 4px;
  padding: 10px 15px;
  font-size: 13px;
  font-weight: bold;
  color: #5e5b21;
  cursor: pointer;
  /* transition: all 500ms ease; */
}
#articles .post button:hover {
  margin-top: 2px;
  border-bottom-width: 2px;
}
.empty {
  margin: 20px;
  color: #5e5b21;
}
</style>
