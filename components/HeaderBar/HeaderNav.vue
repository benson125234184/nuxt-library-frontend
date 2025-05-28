<template>
      <nav class="nav-bar">
      <ul>
        <li><a href="#">活動公告</a></li>
        <li><a href="#">數位資源</a></li>
        <li><a href="#">讀者服務</a></li>
        <li><a href="#">來館資訊</a></li>
        <li><a href="#">關於我們</a></li>
      </ul>
    </nav>
</template>

<script setup>

</script>

<style scoped>
    .nav-bar {
  background: white;
  padding: 0.5rem 1rem;
}
.nav-bar ul {
  display: flex;
  justify-content: center;
  list-style: none;
  gap: 2rem;
  padding: 0;
  margin: 0;
}
.nav-bar a {
  text-decoration: none;
  font-weight: bold;
  color: #000;
}

</style>