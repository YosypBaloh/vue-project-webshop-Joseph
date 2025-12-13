<template>
    <div class="header">
      <span class="logo">{{ title }}</span>
      <span class="user">{{ fullName }} ({{ user.rating }})</span>
      <button @click="addRating">+</button>
    </div>
</template>

<script>
export default {
  data() {
      return {
        user: {
          name: 'Timcsi',
          surname: 'Balog',
          age:'20',
          rating: 0,
          email: 'john@doe.com',
          },
        };
      },
computed: {
    fullName(){
      return `Szia, ${this.user.name} ${this.user.surname}`;
    },
},
methods:{
  addRating(){
    this.user.rating++;
  }
},
   props: {
    title: {
      type: String,
      required: true,
   },
  },
};

</script>

<style lang='css' scoped>
  .header {
    background: #FFC5CB;
    color:#502B7B;
    padding: 20px;
    border-bottom: 2px solid #502B7B;
  }

  .header .logo {
    font-size: 20px;
  }

  .header .user {
    float: right;
  }

</style>