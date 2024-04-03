<script setup>
import { ref, onMounted } from 'vue'

const { data: itemsPost } = await useFetch('http://127.0.0.1:8000/json-posts')

const items = [
  '/img/slider/slider.png',
  '/img/slider/slider-2.png',
  '/img/slider/slider-3.png',
]

const carouselRef = ref(null)

onMounted(() => {
  setInterval(() => {
    if (!carouselRef.value) return

    if (carouselRef.value.page === carouselRef.value.pages) {
      return carouselRef.value.select(0)
    }

    carouselRef.value.next()
  }, 5000)
})
</script>

<template>
  <!-- First slider codes -->
  <section class="carousel position-relative">
    <UCarousel
      ref="carouselRef"
      v-slot="{ item }"
      :items="items"
      :ui="{ item: 'basis-full' }"
      class="rounded-lg overflow-hidden"
      indicators
      arrows
    >
      <NuxtImg :src="item" class="w-full" draggable="false" />
    </UCarousel>
  </section>

  <section class="events">
    <h1 class="events__h1 text-center">Upcoming events</h1>
    <div class="events__content d-flex">
      <div class="events__content__box">
        <div class="events__content__box--margin">
          <img class="events__content__box__img" src="" alt="" />
          <div class="events__content__box__text-box">
            <h2 class="events__content__box__h2">cím</h2>
            <p class="events__content__box__p">valami</p>
            <NuxtLink class="events__content__box__link" href="#">
              <NuxtImg src="/img/events.svg" alt="chajcafe" />
            </NuxtLink>
          </div>
        </div>
      </div>
    </div>

    <div class="events__link-box text-center">
      <NuxtLink class="events__link-box__link page-link" href="#"
        >All Events
        <NuxtImg
          class="page-link__img position-relative"
          src="/img/link.svg"
          alt="chajcafe"
        />
      </NuxtLink>
    </div>
  </section>

  <section class="about">
    <div class="about__content about__content--margin-b d-flex">
      <div
        class="about__content__text-box about__content__one-text-box position-relative"
      >
        <div class="about__content__text-box__bg-box position-absolute"></div>
        <div
          class="about__content__one-text-box__img-box d-flex position-relative"
        >
          <NuxtImg
            class="about__content__one-text-box__img-box__img"
            src="/img/about/Layer_1.svg"
            alt="chajcafe"
          />
          <NuxtImg
            class="about__content__one-text-box__img-box__img"
            src="/img/about/Layer_2.svg"
            alt="chajcafe"
          />
        </div>
        <h2 class="about__content__text-box__h2 position-relative">About us</h2>
        <p class="about__content__text-box__p position-relative">
          The Chaj gallery was founded the fall of 2019 by Rabbi Mendy and
          Tzivia Myers. The name Chaj means life, and that's what we're all
          about. We are not your grandfather's gallery - we are building a
          community. From art to literature; from prayers to parties; classes to
          discussions at the Kosher 'Kave El Hasem' (Chaj Cafe), we aim to bring
          just the right dose of Chaj to your life.
        </p>
      </div>

      <div
        class="about__content__img-box about__content__one-img-box position-relative"
      >
        <NuxtImg
          class="about__content__img-box__img"
          src="/img/about/about.webp"
          alt="chajcafe"
        />
      </div>
    </div>

    <div class="about__content d-flex">
      <div
        class="about__content__img-box about__content__two-img-box position-relative"
      >
        <NuxtImg
          class="about__content__img-box__img"
          src="/img/about/about2.webp"
          alt="chajcafe"
        />
      </div>

      <div
        class="about__content__text-box about__content__two-text-box position-relative"
      >
        <div class="about__content__text-box__bg-box position-absolute"></div>
        <div
          class="about__content__two-text-box__img-box d-flex position-relative"
        >
          <NuxtImg
            class="about__content__two-text-box__img"
            src="/img/about/Layer_1.svg"
            alt="chajcafe"
          />
          <NuxtImg
            class="about__content__two-text-box__img"
            src="/img/about/Layer_2.svg"
            alt="chajcafe"
          />
        </div>
        <h2
          class="about__content__text-box__h2 about__content__two-text-box__h2 position-relative"
        >
          Chaj Café
        </h2>
        <p
          class="about__content__text-box__p about__content__two-text-box__p position-relative"
        >
          Kosher cafe offering Kosher food for body, mind and soul, and cultural
          programs. And coffee. Lot's of coffee.
        </p>
      </div>
    </div>
  </section>

  <section class="welcome-shop">
    <h2 class="welcome-shop__h2 text-center">Shop</h2>
    <div class="welcome-shop__content d-flex">
      <div
        v-for="post in itemsPost"
        :key="post.id"
        class="welcome-shop__content__box"
      >
        <div class="welcome-shop__content__box--margin">
          <img
            class="welcome-shop__content__box__img"
            :src="`http://127.0.0.1:8000/storage/${post.image}`"
          />
          <div class="welcome-shop__content__box__text-box">
            <h2 class="welcome-shop__content__box__text-box__h2">
              {{ post.title }}
            </h2>
            <ClientOnly>
              <p class="welcome-shop__content__box__p" v-html="post.body" />
            </ClientOnly>
            <NuxtLink
              class="welcome-shop__content__box__text-box__link"
              :to="`/posts/${post.slug}`"
            >
              Tovább
            </NuxtLink>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
