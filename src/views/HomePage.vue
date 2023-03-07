<script setup></script>

<template>
 <div class="brand">
  <img class="logo" src="logo.svg" alt="logo" />
  <h1 class="title">Triviantastic</h1>
  <img class="logo" src="logo.svg" alt="logo" />
 </div>
 <div class="categories">
  <RouterLink :to="`/question/category/${n}`" v-for="n in 24" :key="n" class="category">Category - {{ n }}</RouterLink>
 </div>
</template>

<style lang="postcss" scoped>
.brand {
  @apply flex items-center justify-center gap-4;

  & .logo {
   @apply h-16 w-16;
  }

  & .title {
    @apply text-6xl font-bold uppercase tracking-widest text-gray-800;
  }
}

.categories {
  @apply grid flex-grow grid-cols-4 gap-12;

  & .category {
    @apply flex h-32 w-40 items-center justify-center rounded border-4 py-4 font-bold uppercase text-slate-500 transition-colors duration-300;

    &:hover {
      @apply cursor-pointer border-red-500 bg-red-500 text-white;
    }
  }
}
</style>
