<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link>
    </div>
    <router-view />
    <footer class="text-muted">
      <div class="container">
        <p>Copyright &copy; Rév Kálmán 2021 </p>
        <router-link to="/about">About</router-link>
      </div>
    </footer>
  </div>
</template>
