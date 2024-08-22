<template>
    <v-app>
      <div>
        <nav :class="{ 'scrolled': isScrolled }" class="navbar">
          <div class="navbar-brand">Your Logo</div>
          <div class="navbar-menu">
            <NuxtLink to="/" class="navbar-item">Home</NuxtLink>
            <NuxtLink to="/about" class="navbar-item">About</NuxtLink>
            <NuxtLink to="/timeline" class="navbar-item">Timeline</NuxtLink>
            <NuxtLink to="/contact" class="navbar-item">Contact</NuxtLink>
            
          </div>
        </nav>
        
        <main>
          <slot/>
        </main>

        <v-footer
          class="bg-grey-lighten-1"
        >
          <v-row
            justify="center"
            no-gutters
          >
            <v-btn
              v-for="link in links"
              :key="link"
              color="white"
              variant="text"
              class="mx-2"
              rounded="xl"
            >
              {{ link }}
            </v-btn>
            <v-col
              class="text-center mt-4"
              cols="12"
            >
              {{ new Date().getFullYear() }} — <strong>Your Company Name</strong>
            </v-col>
          </v-row>
        </v-footer>
      </div>
    </v-app>
</template>

<script setup>
const isScrolled = ref(false)

const handleScroll = () => {
  isScrolled.value = window.scrollY > 50 // Change color after 50px of scrolling
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>

<style scoped>
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1rem 2rem;
  transition: all 0.3s ease;
  z-index: 1000;
}

.navbar-brand {
  font-size: 1.5rem;
  font-weight: bold;
}

.navbar-menu {
  display: flex;
  gap: 1rem;
}

.navbar-item {
  text-decoration: none;
  padding: 0.5rem 1rem;
  border-radius: 4px;
  transition: background-color 0.3s ease;
}

/* Initial state */
.navbar {
  background-color: transparent;
}

.navbar-item {
  color: #333;
}

/* Scrolled state */
.navbar.scrolled {
  background-color: #ffffff;
  box-shadow: 0 2px 4px rgba(0,0,0,.1);
}

.navbar.scrolled .navbar-item {
  color: #333;
}

.navbar-item:hover {
  background-color: rgba(0,0,0,0.1);
}
</style>