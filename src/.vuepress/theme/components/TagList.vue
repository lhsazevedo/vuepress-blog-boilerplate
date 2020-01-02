<template>
  <ul class="is-flex">
      <li class="" v-for="tag in tags">
        <a href="#" @click="$emit('tag-click', tag)">
          <span class="tag is-light m">{{ tag }}</span>                
        </a>
      </li>
    </ul>
</template>

<script>
export default {
  props: ['tags']
}
</script>

<style lang="scss" scoped>
    .m {
        margin-right: 1em;
    }
</style>
