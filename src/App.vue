<template>
  <div id="nav">
    <router-link :class="{active: $route.name === 'Home'}" to="/">Home</router-link> |
    <router-link :class="{active: $route.name === 'Cart'}" to="/">Home</router-link> |
    <router-link to="/about">About</router-link>
  </div>
  <router-view/>
</template>

<style lang="scss">
*,
  *::after,
  *::before
  {
  margin : 0;
  padding: 0;
  }
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #26a842;
}

// #nav {
//   padding: 30px;

//   a {
//     font-weight: bold;
//     color: #2c3e50;

//     &.router-link-exact-active {
//       color: #42b983;
//     }
//   }
// }
html, body {
  
  overflow-x: hidden;
}
body {
  background-color: rgb(245,245,245);
}
#nav {
  padding: 0.8rem;
  width: 100vw;
  height: 2.5rem;
  background-color: #fff;
  line-height: 2.5rem;
  a {
    font-weight:bold;
    color: #a9a9a9 ;
    text-decoration: none;
    margin: 0 0.15rem 0 0.15rem;
    font-size: 1.25rem;
    &.active {
      color: #2c3e50;
    }
  }
}
.text-center {
  text-align: center;
}
</style>
