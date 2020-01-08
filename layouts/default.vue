<template>
  <div>
    <Navbar />

    <main>
      <div class="container">
        <nuxt />
      </div>
    </main>
  </div>
</template>

<script>
import Navbar from '@/components/Navbar'

export default {
  components: {
    Navbar
  }
}
</script>

<style>
body {
  margin: 0;
	padding: 0;
	height: 100%;
	--c : rgba(255,255,255,0.7);
  --t : transparent;
	background-image: url('/background.png');
}
</style>
