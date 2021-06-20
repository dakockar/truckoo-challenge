<template>
  <nav>
    <ul>
      <li><a href="#">Dashboard</a></li>
      <li><a href="#">Logout</a></li>
    </ul>
  </nav>
</template>

<style scoped>
nav {
  display: flex;
  position: fixed;
  background-color: #002334;
  width: 300px;
  height: 100vh;
  padding-top: 200px;
}

li {
  background-color: white;
  color: #002334;
  font-weight: 600;
  font-size: 1.2rem;
  text-transform: uppercase;
  box-sizing: border-box;
  width: 100%;
  padding: 10px 0 10px 15px;
  margin: 1rem auto;
  transition: 0.2s ease-in-out;
}

li:hover {
  background-color: #ccd3d6;
}
</style>