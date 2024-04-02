<script setup></script>

<template>
  <header>
    <nav class="navbar d-flex position-relative">
      <NuxtImg
        class="navbar__one-img position-absolute"
        src="/img/header/logo2.png"
        alt="chajcafe"
      />
      <div class="hamburger" id="hamburger">
        <div class="bar"></div>
        <div class="bar"></div>
        <div class="bar"></div>
      </div>
      <div class="navbar-logo-box">
        <NuxtImg
          class="navbar-logo-box__img position-relative"
          src="/img/header/logo.png"
          alt="chajcafe"
        />
      </div>
      <ul class="menu d-flex position-relative" id="menu">
        <li><a href="#">Home</a></li>
        <li><a href="#">About us</a></li>
        <li><a href="#">Gallery</a></li>
        <li><a href="#">Chaj Café</a></li>
        <li><a href="#">Events</a></li>
        <li><a href="#">Shop</a></li>
      </ul>
    </nav>
  </header>
</template>
