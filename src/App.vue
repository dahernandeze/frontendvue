<template>
  <div id="app">
    <header>
      <nav>
        <section class="contenedor nav">
          <div class="logo">
            <router-link to="/">
              <img src="./assets/logoEstigma.png" alt="logo">  
            </router-link>
          </div>
          <div class="enlaces-header">
            <router-link to="/">Home</router-link> 
            <router-link to="/about">About US</router-link> 
            <router-link to="/services">Services</router-link> 
            <router-link to="/store">Store</router-link> 
            <router-link to="/login">Login</router-link>
            <button
                class="logout"
                @click="logout"
                v-if="isAuthenticated"
            >LogOut</button>
          </div>
          <div class="hamburguer">
              <b-icon icon="list" class="b-icon"></b-icon>
          </div>
        </section>
      </nav>
    </header>
    <router-view/>
  </div>
</template>

<script>
export default{
  data() {
    return {
      isAuthenticated: false,
    }
  },
  created() {
    // Escucha el evento personalizado 'set-is-authenticated' para actualizar el prop 'isAuthenticated'
    this.$root.$on('set-is-authenticated', (value=>{
      this.isAuthenticated = value;
    }));
  },
  methods: {
    logout() {
      localStorage.removeItem("jwt");
      localStorage.removeItem("user");
      this.$router.push("/");
      this.isAuthenticated = false;
    },
  },
};
</script>

<style>
:root{
  --dark-blue: #1d273b;
  --middle-blue: #2570ff;
  --light-blue: #5D6678;
  --purple-blue: #667db6;
  --gray:#adb6c7;
  --light-green: #1FDE82;
  --white: #fff;
  --light-gray: #f2f2f2;
  --white-gray: #f2f5fc;
}

*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

#app {
  font-family: 'Roboto', sans-serif;
  text-align: center;
  
}

h1, h2, h3, h4, h5, h6 {
  color: var(--dark-blue);
  font-weight: 300;
}

.contenedor {
    width: 90%;
    max-width: 1000px;
    margin: auto;
    overflow: hidden;
}

.contenedor1 {
  width: 90%;
  max-width: 1000px;
  margin: auto;
  overflow: hidden;
  padding: 60px 0;
}

h1{
    font-size: 50px;
}

header::before {
  content: "";
  display: block;
  margin-bottom: 80px;
  /*Esto es para que cuando el nav que esta fixed no se superponga a elementos, tambien el top y z-index del nav*/
}


nav {
  width: 100%;
  height: 100px;
  background: var(--white);
  border-bottom: 1px solid transparent;
  box-shadow: 1px 1px 10px 0 rgba(0, 0, 0, .2);
  position: fixed;
  top: 0;
  z-index: 100;
  transition: ease-in-out 0.5s;
}

.nav {
  display: flex;
  justify-content: space-between;
  height: 100px;
  width: 100%;
  align-items: center;
  padding: 0 40px;
}

.nav .logo {
  height: 100px;
}

.nav .logo img {
  height: 100%;
  vertical-align: top;
  cursor: pointer;
}

.enlaces-header {
  font-weight: 300px;
  transition: ease-in-out 0.5s;
}

.nav .enlaces-header a,
.nav .enlaces-header .logout {
  font-size: 20px;
  color: var(--light-blue);
  text-decoration: none;
  margin-left: 20px;
  font-weight: 300;

}

.nav a.router-link-exact-active {
  color: var(--light-green);
}

.nav .enlaces-header .logout{
  color: var(--white);
}

.hamburguer {
  width: 80px;
  height: 80px;
  display: none;
  /* background: #236363; */
  text-align: center;
  z-index: 100;
  cursor: pointer;
  transition: color 0.5s ease-in;
}

.hamburguer> .b-icon {
  font-size: 25px;
  line-height: 80px;
  color: var(--dark-blue);
}

.contenido-header {
  width: 100%;
  height: 600px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.contenido-header>img {
  width: 550px;
  animation: ease-in animat 1s;
}

@keyframes animat {
  0%{
      transform: scale(0);
  }
  100%{
      transform: scale(1); /*probar con 2*/
  }
}

.textos-header{
  margin: 0 0 0 30px;
}

.contenido-header p{
  font-weight: 100;
  margin-top: 14px;
  color: var(--light-blue);

}

.contenido-header a{
  margin: 28px 0 0 0;
  width: 130px;
  display: inline-block;
  background: var(--light-green);
  text-align: center;
  color: var(--white);
  padding: 12px 0;
  text-decoration: none;
  font-weight: 400;
  text-transform: uppercase;
  font-size: 14px;
  border-radius: 5px;
  box-shadow: 0 8px 32px rgba(31, 222, 130, 0.46);

}

.enlaces-header .logout {
  margin: 2px 0 0 0;
  width: 100px;
  display: inline-block;
  background: var(--light-green);
  text-align: center;
  color: var(--white);
  padding: 4px;
  text-decoration: none;
  font-weight: 400;
  text-transform: uppercase;
  border-radius: 5px;
  box-shadow: 0 8px 32px rgba(31, 222, 130, 0.46);

}


</style>
