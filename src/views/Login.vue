<template>
    <div class="login-form">
      <form @submit.prevent="login">
        <div>
          <label for="email">Correo Electrónico:</label>
          <input type="email" v-model="email" required />
        </div>
        <div>
          <label for="password">Contraseña:</label>
          <input type="password" v-model="password" required minlength="6" />
        </div>
        <button type="submit">Iniciar Sesión</button>
        <p v-if="error">{{ error }}</p>
      </form>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {                                      // inicializando datos
        email: '',
        password: '',
        error: ''
      };
    },
    methods: {
      validateForm() {
        if (!this.email || !this.password) {                             // validando campos vacíos
          this.error = 'Todos los campos son obligatorios';
          return false;
        }
        if (!this.email.includes('@')) {                           // validando formato de correo electrónico
          this.error = 'Correo electrónico no válido';
          return false;
        }
        return true;
      },
      async login() {
        if (!this.validateForm()) return;                               //validando formulario
        try {
          const response = await fetch('https://api.example.com/login', {                     
            method: 'POST',                                                   
            headers: { 'Content-Type': 'application/json' }, 
            body: JSON.stringify({ email: this.email, password: this.password })            // enviando datos de inicio de sesión
          });
          const data = await response.json();
          if (response.ok) {
            localStorage.setItem('token', data.token);             // guardando token en localStorage
            this.$router.push('/dashboard');                
          } else {
            this.error = data.message;            // mostrando mensaje de error
          }
        } catch (err) {
          this.error = 'Error en la conexión';                
        }
      }
    }
  };
  </script>

  
  