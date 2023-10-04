<template>
    <div class="margin">
      <h2>Admin Login/Register</h2><br>
      <form @submit.prevent="handleLogin">
        <div>
          <label for="username">Username:</label>
          <input type="text" id="username" v-model="username" required>
        </div>
        <div>
          <label for="password">Password:</label>
          <input type="password" id="password" v-model="password" required>
        </div>
        <div>
          <button type="submit">Login</button>
          <button type="button" @click="handleRegistration">Register</button>
        </div>
      </form>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        username: '',
        password: '',
      };
    },
    methods: {
      handleLogin() {
        const storedUsername = localStorage.getItem('adminUsername');
        const storedPassword = localStorage.getItem('adminPassword');

        if (this.username === storedUsername && this.password === storedPassword) {
          this.$router.push('/adblog');
          this.isAdminLoggedIn = true;
          alert("Login successfull");
        } else {
          alert('Invalid credentials. Please try again or register.');
        }
      },
      handleRegistration() {
        localStorage.setItem('adminUsername', this.username);
        localStorage.setItem('adminPassword', this.password);
      },
    },
  };
  </script>
  
  <style scoped>
  
  h2 {
  text-align: center;
  margin-top: 20px;
  font-size: 24px;
}

form {
  max-width: 300px;
  margin: auto auto;
  padding: 20px;
  padding-right: 20px;
  background-color: #f0f0f0;
  border: 1px solid #ccc;
  border-radius: 5px;
  box-shadow: 0px 0px 5px rgba(0, 0, 0, 0.3);
}

div {
  margin-bottom: 10px;
}

label {
  display: block;
  font-weight: bold;
}

.margin{
    padding-bottom: 3.5rem;
}

input[type="text"],
input[type="password"] {
  width: 90%;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
}

button {
  background-color: #007bff;
  color: #fff;
  border: none;
  border-radius: 5px;
  padding: 10px 20px;
  cursor: pointer;
  font-size: 16px;
}

button[type="button"] {
  background-color: #333;
  margin-left: 10px;
}

button[type="submit"] {
  margin-top: 10px;
}

</style>
  