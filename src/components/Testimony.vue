<script setup>
  const props = defineProps({
    color: String,
    name: String,
    title: String,
    content: String,
    status: String,
    background: Boolean
  })

  function firstName(name) {
    let res = name.split(" ");
    return res[0].toLowerCase();
  }

  const background = props.background
</script>

<template>
  <div class="card" :class="{'card--quote' : background}">
    <div class="card__author author">
      <img :src="'/img/image-' + firstName(props.name) + '.jpg'" :alt="props.name + '\'s avatar'" class="author__img">
      <p class="author__name">{{ props.name }}</p>
      <p class="author__status">{{ props.status }}</p>
    </div>
    <h1 class="card__title">{{ props.title }}</h1>
    <p class="card__content">{{ props.content }}</p>
  </div>
</template>

<style scoped lang="scss">
  .card {
    padding: 2rem;
    border-radius: 10px;
    background-color: $accent-4;
    &--accent_1 {
      background-color: $accent-1;
      color: $accent-4;
    }
    &--accent_2 {
      background-color: $accent-2;
    }
    &--accent_3 {
      background-color: $accent-3;
      .author .author__img {
        border-color: $accent_1;
      }
    }
    &--accent_1, &--accent_2, &--accent_3 {
      color: $accent-4;
    }
    &--quote {
      background-image: url("./img/bg-pattern-quotation.svg");
      background-repeat: no-repeat;      
      background-position: top right 1.5rem;
    }
    &__author, &__title {
      margin-bottom: 1rem;
    }
    &__title {
      font-size: 1.27rem;
      line-height: 1.6rem;
    }
    &__content {
      opacity: 70%;
      line-height: 1.2rem;
    }
  }

  .author {
    display: grid;
    grid-template-columns: 2rem 1fr;
    align-items: center;
    column-gap: 1rem;
    &__img {
      border-radius: 100%;
      width: 2rem;
      border: 2px solid rgba(255, 255, 255, .5);
      grid-row: 1/3;
    }
    &__name {
      grid-row: 1/2;
    }
    &__status {
      grid-column: 2/3;
      opacity: 50%;
    }
  }

  @include breakpoint {
    .card--quote {
      background-position: top left 83%;
    }
  }
</style>