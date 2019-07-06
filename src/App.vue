<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/calc">calc</router-link> |
      <router-link to="/UserList">UserList</router-link>
    </div>
    <router-view/>
  </div>
</template>

<style>
#app {
  max-width: 900px;
  margin: 0 auto;
}
</style>
