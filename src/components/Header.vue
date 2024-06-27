<script></script>

<template>
  <header>
    <nav>
      <a href="/" class="nav-link">Home</a> | <a href="#" class="nav-link">Filter</a>
    </nav>
  </header>
</template>

<style scoped>
header {
  padding: 10px 0;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

nav {
  text-align: center;
}

.nav-link {
  font-family: Arial, Helvetica, sans-serif; 
  text-transform: uppercase; 
  color: #fff;
  text-decoration: none;
  padding: 12px 20px;
  margin: 0 10px;
  font-size: 16px;
  transition: background-color 0.3s, color 0.3s;
  border-radius: 4px;
  display: inline-block;
}

.nav-link:hover {
  background-color: #45a049; 
  color: #fff;
}
</style>