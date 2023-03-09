<script setup>
import { onMounted, ref} from 'vue'
import useAPI from '@/composables/useAPI'
import BaseTitle from "@/components/BaseTitle.vue";

const { categories, getCategories } = useAPI()

onMounted(async () => {
   await getCategories()
})
</script>

<template>
 <BaseTitle>
  <template #logo>
    <img src="/logo.svg" alt="logo" />
  </template>
  Triviantastic
 </BaseTitle>
 <div v-if="categories.length > 0" class="categories">
  <RouterLink 
  :to="`/question/category/${category.id}`" v-for="category in categories" 
  :key="category.id" class="category"> {{ category.name }}
  </RouterLink>
 </div>
</template>

<style lang="postcss" scoped>

.categories {
  @apply grid flex-grow grid-cols-4 gap-12;

  & .category {
    @apply text-center flex h-32  items-center justify-center rounded border-4 py-4 font-bold uppercase text-slate-500 transition-colors duration-300;

    &:hover {
      @apply cursor-pointer border-red-500 bg-red-500 text-white;
    }
  }
}
</style>
