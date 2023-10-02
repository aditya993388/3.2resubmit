<template>
  <header>
    <Navbar/>
  </header>

  <body>
    <RouterView/>
  </body>

  <footer>
    <Footer/>
  </footer>
  
</template>

<script>
import Navbar from '../src/components/navbar.vue'
import Footer from '../src/components/footer.vue'
export default { 
  name: 'App',
  components: {Navbar, Footer }
}
</script>

<style scoped>

</style>