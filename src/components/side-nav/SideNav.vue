<template>
    <nav>
      <header>
        <img src="../../assets/company-logo-white.svg" width="25px">
        <h3 class="pa-3 grey--text text--lighten-4">{{pageTitle}}</h3>       
      </header>

      <!-- create a list of buttons the old way : ul>li>a -->
      <ul v-for="navButton in navButtons" v-bind:key="navButton.id">

        <!-- As here only one button can stay active at any one time we use a global variable to store which button is active and it gets refreshed with click events on each button. Active buttons gets primary color -->
        <li @click="activeBtn = 'btn' + navButton.id" :class="{ 'success darken-1' : activeBtn === 'btn' + navButton.id }">
          <v-icon class="grey--text text--lighten-4" left dark>{{navButton.icon}}</v-icon>
          <a class="grey--text text--lighten-4">{{navButton.title}}</a>
        </li>
      </ul>

    </nav>
    
</template>

<script>
  export default {
    name: "SideNav",
    data: () => ({
      // global variable for storing active button
      activeBtn: 'btn4'
    }),
    props: [ "pageTitle", "navButtons" ]
  }
</script>

<style scoped>

  nav {
    background-color: rgb(75, 75, 75);
    background-image: url('../../assets/background.jpg');
    background-size: cover;
    height: 100vh;
    width: 260px;
    user-select: none;
  }

  header {
    text-align: center;
    padding: 5px 10px;
    border-bottom: 1px solid grey;
    margin-bottom: 40px;
  }

  h3 {
    display: inline-block;
    color: white;
  }

  .btn-block {
    margin: 15px 10px;
    padding: 10px;
  }
  
  ul {
    padding: 0;
    display: flex;
    flex-direction: column;
  }

  li {
    list-style: none;
    width: 100% - 20px;
    margin: 10px 20px;
    padding: 10px 15px;
    border-radius: 5px;
    position: relative;
    cursor: pointer;
  }

  /* buttons are transparent by default, this bg color makes it stands out a bit on dark backgrounds when hovered upon */
  li:hover {
    background-color: rgba(255, 255, 255, .15)
  }


  a {
    position: absolute;
    top: 13px;
    text-decoration: none;
  }

</style>


