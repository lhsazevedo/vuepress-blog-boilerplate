<template>
	<article class="post-preview">
    <router-link class="link" :to="item.path">
      <header class="header">
        <h2 class="title">{{ item.frontmatter.title }}</h2>
      </header>
      <section v-if="item.frontmatter.excerpt" class="excerpt">
        <p>{{ item.frontmatter.excerpt }}</p>
      </section>
    </router-link>
    <footer class="meta">
      <span class="meta-date">
        <time datetime="item.frontmatter.date">{{ formatPublishDate }}</time>
        <template v-if="item.readingTime"> • {{ item.readingTime.text }}</template>
      </span>
    </footer>
    <ul class="tag-list">
      <li class="tag-list-item" v-for="tag in item.frontmatter.tags">
        <a href="#" @click="addTag(tag)">
          <span class="tag tag-accent">{{ tag }}</span>                
        </a>
      </li>
    </ul>
    
  </article>
</template>

<script>
export default {
  name: 'BlogPostPreview',
  props: {
    item: {
      type: Object,
      required: true
    }
  },
  computed: {
    formatPublishDate() {
      const dateFormat = new Date(this.item.frontmatter.date)
      const options = {
        year: 'numeric',
        month: 'long',
        day: 'numeric'
      } 

      return dateFormat.toLocaleDateString('en-US', options)
    }
  }
}
</script>

<style lang="stylus" scoped>
.post-preview
  padding 20px 0
  margin 20px 0

.link, .link:hover
  text-decoration none !important
  color unset
  
.title
  border-bottom none
  padding-bottom unset

.excerpt
  color: #777

.meta
  color #aaa

.tag-list
  display flex
  list-style none
  margin 0
  padding 0

.tag-list-item
  margin-right 4px

.tag
  display inline-block
  padding .25em .4em
  font-size 75%
  font-weight 700
  line-height 1
  text-align center
  white-space nowrap
  vertical-align baseline
  border-radius .25rem

.tag-accent
  background-color #42b983
  color #ffffff
</style>
