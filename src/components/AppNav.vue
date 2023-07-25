<script>
export default {};
</script>

<template>
  <nav class="d-flex align-items-center">
    <ul class="footer-links d-flex gap-4 justify-content-center pt-3">
      <li class="list-unstyled">
        <router-link :to="{ name: 'home' }">
          <button class="button">HOME</button>
        </router-link>
      </li>

      <li class="list-unstyled">
        <router-link :to="{ name: 'about' }">
          <button class="button">CHI SIAMO</button>
        </router-link>
      </li>

      <li class="list-unstyled">
        <router-link :to="{ name: 'drinks' }">
          <button class="button">COCKTAILS</button>
        </router-link>
      </li>

      <li class="list-unstyled">
        <router-link :to="{ name: 'contacts' }">
          <button class="button">CONTACTS</button>
        </router-link>
      </li>
    </ul>
  </nav>
</template>