<template>
  <div id="nav">
    <!-- <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link> -->
  </div>
  <router-view/>
</template>

<style lang="scss" >


.text-left{
    text-align: left;
}
.overflow-hidden{
  overflow: hidden;
}
.curso-pointer{
  cursor: pointer;
}
.mt-1{
  margin-top: 1rem;
}
.box-flex{
    display: flex;
    justify-content: center;
    align-items: center;
}
@media only screen and (max-width: 576px){
    .box-flex-mobile{
      flex-direction: column;
    }
    .box-space-mobile{
      justify-content: space-evenly;
    }
}
.w-50{
  width: 50%;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
