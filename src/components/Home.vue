<template>
  <div class="home">
    <h1>Welcome to Vue Restaurant App!</h1>
    <router-link to="/book" class="btn">Book a Table</router-link>
  </div>
</template>

<script>
export default {
  // You can add component-specific logic here
};
</script>

<style>
.home {
  margin-top: 70px;
  text-align: center;
  background-image: url('https://source.unsplash.com/featured/?restaurant');
  background-size: cover;
  background-position: center;
  height: calc(100vh - 70px);
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

h1 {
  color: #fff;
  background-color: rgb(26, 26, 26);
  border-radius: 10px;
  padding: 10px;
  font-size: 2.5rem;
  margin-bottom: 30px;
}

.btn {
  display: inline-block;
  padding: 12px 24px;
  background-color: #007bff;
  color: #fff;
  font-size: 1rem;
  text-decoration: none;
  border-radius: 5px;
  transition: background-color 0.3s ease;
}

.btn:hover {
  background-color: #0056b3;
}
</style>
