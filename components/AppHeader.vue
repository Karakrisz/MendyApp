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
        <li><NuxtLink to="/">Home</NuxtLink></li>
        <li><NuxtLink href="#">About us</NuxtLink></li>
        <li><NuxtLink href="#">Gallery</NuxtLink></li>
        <li><NuxtLink href="#">Chaj Café</NuxtLink></li>
        <li><NuxtLink href="#">Events</NuxtLink></li>
        <li><NuxtLink href="#">Shop</NuxtLink></li>
      </ul>
    </nav>
  </header>
</template>
