<script>
export default {
  name: 'HeaderComponent',
};
</script>

<template>
  <nav class="navbar navbar-expand-sm bg-dark navbar-dark mynav">
  <div class="container">
    <ul class="navbar-nav">
      <li class="nav-item">
        <a class="nav-link active" href="#">Home</a>
      </li>
     <li class="nav-item">
        <a class="nav-link" href="#">About</a>
      </li>
      <li class="nav-item">
        <a class="nav-link" href="#">Mail</a>
      </li>
      <li class="nav-item">
        <a class="nav-link disabled" href="#"></a>
      </li>
    </ul>
  </div>
</nav>
</template>

<style scoped>
.mynav{

width: 1600px;



}
</style>
