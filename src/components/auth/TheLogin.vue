<template>
    <div class="the-login">
      <!-- Formularios -->
      <div class="contenedor-formularios">
          <!-- Links de los formularios -->
          <ul class="contenedor-tabs">
              <li
                @click="selectTab(1)"
                :class="{active: currentTab == 1}" 
                class="tab tab-segunda">
                  <a href="#iniciar-sesion">Iniciar Sesión</a>
              </li>

              <li
                @click="selectTab(2)"
                :class="{active: currentTab == 2}" 
                class="tab tab-primera">
                  <a href="#registrarse">Registrarse</a>                    
              </li>
          </ul>


          <!-- Contenido de los Formularios -->
          <!-- <div class="contenido-tab"> -->
          <!-- Iniciar Sesión -->
              <div v-if="currentTab == 1" id="iniciar-sesion">
                  <h1>Iniciar Sesión</h1>
                  <form action="#" method="post">
                      <div class="contenedor-input">
                          <label class="label"><span class="req"></span></label>
                          <input 
                              v-model="login.email"
                              type="email"
                              required
                              placeholder="Email"
                          >
                      </div>

                      <div class="contenedor-input">
                          <label class="label"><span class="req"></span></label>
                          <input
                              v-model="login.password" 
                              type="password"
                              required
                              placeholder="Password"
                          >
                      </div>

                      <p class="forgot"><a href="#">¿Se te olvidó la contraseña?</a></p>

                      <input 
                          @click.prevent="loginUser"
                          type="submit"
                          class="button button-block"
                          value="Iniciar Sesión"
                      >
                  </form>
              </div>

              <!-- Registrarse -->
              <div v-if="currentTab == 2" id="registrarse">
                  <h1>Registrarse</h1>
                  <form action="#" method="post">
                      <div class="fila-arriba">
                          <div class="contenedor-input">
                              <label><span class="req"></span></label>
                              <input 
                                  v-model="register.username"
                                  type="text"
                                  required
                                  placeholder="Nombre"
                              >
                          </div>
                          
                          <div class="contenedor-input">
                              <label><span class="req"></span></label>
                              <input 
                                  v-model="register.userlastname"
                                  type="text"
                                  required
                                  placeholder="Apellidos"
                              >
                          </div>
                      </div>

                      <div class="contenedor-input">
                          <label class="label"><span class="req"></span></label>
                          <input
                              v-model="register.email" 
                              type="email"
                              required
                              placeholder="Email"
                          >
                      </div>

                      <div class="contenedor-input">
                          <label class="label"><span class="req"></span></label>
                          <input
                              v-model="register.password" 
                              type="password"
                              required
                              placeholder="Password"
                          >
                      </div>

                      <div class="contenedor-input">
                          <label class="label"><span class="req"></span></label>
                          <input 
                              v-model="register.passwordcompare"
                              type="password"
                              required
                              placeholder="Verificar Password"
                          >
                      </div>

                      <input 
                          @click.prevent="registerUser"
                          type="submit"
                          class="button button-block"
                          value="Registrarse"
                      >                    
                  </form>
              </div>
          <!-- </div> -->
      </div>

      <pre>
        {{login}}
        {{register}}            
      </pre>
    </div>
</template>

<script>
import swal from "sweetalert";

export default {
  name: 'TheLogin',
  data() {
    return{
      currentTab: 1,
      login: {
        email: "",
        password: "",
      },
      register: {
        username: "",
        userlastname: "",
        email: "",
        password: "",
        passwordcompare: "",
      }  
    }

  },
  methods: {
    selectTab(selectTab){
      this.currentTab = selectTab;
    },
    async loginUser(){
      try {
        let response = await this.$http.post("/api/user/login", this.login);
        console.log(response.data);
        let token = response.data.tokenReturn;
        let user = response.data.user;

        localStorage.setItem("jwt", token);
        localStorage.setItem("user", JSON.stringify(user));

        if(token){
          swal("Éxito!!", "Login correcto", "success");
          this.$router.push("/checked");
          this.$root.$emit('set-is-authenticated', true);
          // this.isAuthenticated = true;
        }
      } catch (e) {
        swal("Oops!", "Algo salió mal!", "error");
      }

    },
    async registerUser(){
      try {
        let response = await this.$http.post('/api/user/register', this.register);

        console.log(response);
        swal("Éxito!!", "Registro correcto", "success");
        this.$router.push("/login");
        this.currentTab = 1;
        
      } catch (e) {
        swal("Oops!", "Algo salió mal con tu registro", "error");
      }
    }
  },
  props: ['isAuthenticated'],

}

</script>





<style scoped>

*{
  --form-bg: #13232f;
  --form-bg-light: #13232fef;
  --blanco: #fff;

  --color-principal: #1ab188;
  --color-principal-light: #1ab18952;
  --color-principal-dark: #1ab189b2;

  --gris-light: #a0b3b038;
  --gris-lightest: #a0b3b093;
  --gris: #ddd;

  --thin: 300;
  --normal: 400;
  --bold: 600;
  --br: 20px;

  --fuente-principal: "Ubuntu", helvetica;
  --fuente-secundaria: "Raleway", arial;
}

* {
  padding: 0;
  margin: 0;
}

*,
*:before,
*:after {
  box-sizing: border-box;
}

.the-login{
  margin-top: 150px;
}

a {
  text-decoration: none;
  color: var(--color-principal);
  transition: 0.5s ease;
}

a:hover {
  color: var(--color-principal-dark);
}

.contenedor-formularios {
  background: var(--form-bg);
  padding: 40px;
  max-width: 600px;
  margin: 40px auto;
  border-radius: var(--br);
  box-shadow: 0 4px 10px 4px var(--form-bg-light);
}

.contenedor-tabs {
  list-style: none;
  padding: 0;
  margin: 0 0 40px 0;
}

.contenedor-tabs:after {
  content: "";
  display: table;
  clear: both;
}

.contenedor-tabs li a {
  display: block;
  text-decoration: none;
  padding: 15px;
  background: var(--gris-light);
  color: var(--gris-lightest);
  font-size: 20px;
  float: left;
  width: 50%;
  text-align: center;
  cursor: pointer;
  transition: 0.5s ease;
}

.contenedor-tabs li a:hover {
  background: var(--color-principal-dark);
  color: var(--blanco);
}

.contenedor-tabs .active a {
  background: var(--color-principal);
  color: var(--blanco);
}

.contenido-tab > div:last-child {
  display: none;
}

h1 {
  text-align: center;
  color: var(--blanco);
  font-weight: var(--thin);
  margin: 0 0 40px;
}

label {
  position: absolute;
  transform: translateY(6px);
  left: 13px;
  color: rgba(var(--blanco), 0.5);
  transition: all 0.25s ease;
  --webkit-backface-visibility: hidden;
  pointer-events: none;
  font-size: 22px;
}

label .req {
  margin: 2px;
  color: var(--color-principal);
}

label .active {
  transform: translateY(50px);
  left: 2px;
  font-size: 14px;
}

label .active .req {
  opacity: 0;
}

label .highlight {
  color: var(--blanco);
}

input {
  font-size: 22px;
  display: block;
  width: 100%;
  height: 100%;
  padding: 5px 10px;
  background: none;
  background-image: none;
  border: 1px solid var(--gris-light);
  border-top: none;
  border-left: none;
  border-right: none;
  color: var(--blanco);
  border-radius: 0;
  transition: all 0.5s ease;
  border-radius: 5px;
}

input:focus {
  outline: none;
  border-color: var(--color-principal);
  background: none;
}

.contenedor-input {
  position: relative;
  margin-bottom: 40px;
}

.fila-arriba:after {
  content: "";
  display: table;
  clear: both;
}

.fila-arriba div {
  float: left;
  width: 48%;
  margin-right: 4%;
}

.fila-arriba div:last-child {
  margin: 0;
}

.button {
  border: 0;
  outline: none;
  border-radius: 5px;
  cursor: pointer;
  padding: 15px 0;
  font-size: 2rem;
  background: var(--color-principal);
  color: var(--blanco);
  transition: all 0.5s ease;
  -webkit-appearance: none;
}

.button:hover {
  background: var(--color-principal-dark);
}

.button:focus {
  background: var(--color-principal-light);
}

.button-block {
  display: block;
  width: 100%;
}

.forgot {
  margin-top: -20px;
  text-align: right;
  margin-bottom: 20px;
}

/* Mediaqueries */
@media screen and (max-width: 500px) {
  .fila-arriba div {
    width: 100%;
  }

  .fila-arriba div :last-child {
    margin-bottom: 40px;
  }
}

@media screen and (max-width: 400px) {
  .contenedor-tabs li a {
    width: 100%;
  }
}

</style>

