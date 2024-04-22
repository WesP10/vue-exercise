<template>
  <div id="nav">
    <img alt="Vue logo" src="./assets/logo.png">
    <ul>
      <RouterLink to="/">Home</RouterLink>
      <RouterLink to="/about">About</RouterLink>
    </ul>
  </div>
  <RouterView/>
</template>

<script>
export default {
  name: 'App',
  data () {
    return {
    }
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
}
#nav {
  z-index: 100;
  position: fixed;
  top: 0;
  background-color: #f3f3f3;
  overflow: hidden;
  width: 100%;
  height: 12dvh;
}
#nav img {
  aspect-ratio: 1;
  height: 80%;
  float: left;
  padding: 10px;
}
#nav ul {
  list-style-type: none;
  display: flex;
  justify-content: space-around;
  align-items: center;
  height: 100%;
}
#nav ul > * {
  text-decoration: none;
  color: black;
  font-size: 1.5em;
  font-weight: bold;
}

Body {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: white;
  margin-top: 60px;
  background: #42b883;
}
</style>
