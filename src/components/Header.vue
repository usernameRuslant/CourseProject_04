<template>
  <div class="header">
    <span class="logo">{{ title }}</span>
    <button @click="addRating">+</button>
    <span class="user">{{ fullName }} ({{ user.rating }})</span>
  </div>
</template>
<script>
export default {
  name:'Header',
  data() {
    return {
      user: {
        name: 'John',
        surname: 'Doe',
        age: 20,
        rating: 0,
        email: 'j@d.com',
      },
      allRating: 0,
    };
  },
  computed: {
    fullName() {
      return ` Привет, ${this.user.name} ${this.user.surname}`;
    },
  },
  methods: {
    addRating() {
      this.user.rating++;
      this.allRating++;
    },
  },
  mounted() {
    this.addRating();
  },
  watch: {
    allRating(newValue, oldValue) {
      if (newValue > 5) console.log(`${newValue} - ${oldValue}`);
    },
  },
  props: {
    title: {
      type: String,
      required: true,
    },
  },
};
</script>
<style lang="css" scoped>
.header {
  background: #333;
  color: #fff;
  padding: 20px;
  border-bottom: 2px solid black;
}
.header .logo {
  font-size: 20px;
}
.header .user {
  float: right;
}
.header button {
  float: right;
  border: 0;
  background: #b94b4b;
  border-radius: 5px;
  padding: 5px 10px;
  font-size: 12px;
  color: #fff;
  font-weight: bold;
  cursor: pointer;
  position: relative;
  top: -3px;
  left: 10px;
}
.header button:hover {
  background: #7c2c2c;
}
</style>
