<template>
  <body>
  <div class="box">
    <h2>Login</h2>
    <form @submit.prevent="login">
      <div class="inputBox">
        <input type="text"  v-model="username" required>
        <label>Username</label>
      </div>
      <div class="inputBox">
        <input type="text" v-model="password" required>
        <label>Password</label>
      </div>
      <input type="submit" value="Submit">
    </form>
  </div>
</body>
  </template>
  
  <script>
  export default {
    name:"LoginPage",
    data() {
      return {
        username: '',
        password: ''
      };
    },
    methods: {
      login() {
        // Perform API call to validate user credentials
        // For simplicity, we'll use a hardcoded API endpoint
        const apiUrl = 'http://localhost:3000/users';
        const credentials = {
          username: this.username,
          password: this.password
        };
  
        fetch(apiUrl)
          .then(response => response.json())
          .then(users => {
            const user = users.find(u => u.username === credentials.username && u.password === credentials.password);
            if (user) {
              // User found, store user data and redirect to home page
              this.$store.commit('login', user);
              this.$router.push('/home');
            } else {
              // Invalid credentials, show an error message
              alert('Invalid username or password');
            }
          });
      }
    }
  };
  </script>
  
  <style scoped>
 

body {
  margin: 0;
  padding: 0;
  font-family: sans-serif;
  background: url("https://i.ytimg.com/vi/kU-4z_2m-kg/maxresdefault.jpg")
    no-repeat;
  background-size: cover;
}

.box {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 400px;
  padding: 40px;
  background: rgba(0, 0, 0, 0.8);
  box-sizing: border-box;
  box-shadow: 0 15px 25px rgba(0, 0, 0, 0.5);
  border-radius: 10px;
}

.box h2 {
  margin: 0 0 30px;
  padding: 0;
  color: #fff;
  text-align: center;
}

.box .inputBox {
  position: relative;
}

.box .inputBox input {
  width: 100%;
  padding: 10px 0;
  font-size: 16px;
  color: #fff;
  letter-spacing: 2px;
  margin-bottom: 30px;
  border: none;
  border-bottom: 1px solid #fff;
  outline: none;
  background: transparent;
}

.box .inputBox label {
  position: absolute;
  top: 0;
  left: 0;
  letter-spacing: 2px;
  padding: 10px 0;
  font-size: 16px;
  color: #fff;
  pointer-events: none;
  transition: 0.5s;
}

.box .inputBox input:focus ~ label,
.box .inputBox input:valid ~ label {
  top: -25px;
  left: 0;
  color: #03a9f4;
  font-size: 12px;
}

.box input[type="submit"] {
  background: transparent;
  border: none;
  outline: none;
  color: #fff;
  background: #03a9f4;
  padding: 10px 20px;
  cursor: pointer;
  border-radius: 5px;
}

  </style>
  