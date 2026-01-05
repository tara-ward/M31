<template>
  <nav class="navigation-bar">
    <div class="nav-container">
      <router-link to="/" class="nav-logo">M31</router-link>
      <ul class="nav-menu">
        <li v-for="item in navItems" :key="item.name">
          <router-link :to="item.path" class="nav-link">{{ item.name }}</router-link>
        </li>
      </ul>
    </div>
  </nav>
</template>

<script setup>
const navItems = [
  { name: 'Home', path: '/' },
  { name: 'About', path: '/about' },
  { name: 'Projects', path: '/projects' },
  { name: 'News & Events', path: '/news-events' },
  { name: 'Contact', path: '/contact' },
  { name: 'Social Media', path: '/social-media' },
  { name: 'Portfolio', path: '/portfolio' },
  { name: 'CV', path: '/cv' }
]
</script>

<style scoped lang="scss">
.navigation-bar {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  z-index: 2000;
  background-color: rgba(10, 15, 30, 0.9);
  backdrop-filter: blur(10px);
  border-bottom: 1px solid rgba(255, 255, 255, 0.1);
}

.nav-container {
  max-width: 1400px;
  margin: 0 auto;
  padding: 1rem 2rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.nav-logo {
  font-family: 'Playfair Display', serif;
  font-size: 1.8rem;
  font-weight: 700;
  color: #fff;
  text-decoration: none;
  letter-spacing: 0.1rem;
  transition: opacity 0.3s ease;

  &:hover {
    opacity: 0.8;
  }
}

.nav-menu {
  display: flex;
  list-style: none;
  margin: 0;
  padding: 0;
  gap: 2rem;
  flex-wrap: wrap;
  justify-content: flex-end;

  @media (max-width: 768px) {
    gap: 1rem;
    font-size: 0.9rem;
  }
}

.nav-link {
  font-family: 'Montserrat', sans-serif;
  text-transform: uppercase;
  color: #fff;
  text-decoration: none;
  font-size: 0.85rem;
  letter-spacing: 0.1rem;
  padding: 0.5rem 0;
  position: relative;
  transition: opacity 0.3s ease;

  &:hover {
    opacity: 0.7;
  }

  &.router-link-active {
    font-weight: 700;
    
    &::after {
      content: '';
      position: absolute;
      bottom: 0;
      left: 0;
      width: 100%;
      height: 2px;
      background-color: #fff;
    }
  }
}
</style>

