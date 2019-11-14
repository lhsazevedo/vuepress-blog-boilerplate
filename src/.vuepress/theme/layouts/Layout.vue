<template>
  <div
    class=""
  >
    <!-- <Navbar
      v-if="shouldShowNavbar"
    /> -->

    <Blog
      v-if="$page.frontmatter.blogList"
      :pages="$site.pages" 
      :page-size="$site.themeConfig.pageSize" 
      :start-page="$site.themeConfig.startPage" 
    />

    <Post 
      v-else-if="$page.frontmatter.blog" 
      :sidebar-items="sidebarItems"
    />

    <ArchiveList
      v-else-if="$page.frontmatter.archive"
      :pages="$site.pages"
    />
  </div>
</template>

<script>
// import Navbar from '@parent-theme/components/Navbar.vue'
import Post from '../components/Post.vue'
import Blog from '../components/Blog.vue'
import ArchiveList from '../components/ArchiveList.vue'

export default {
  components: {
    Blog,
    ArchiveList,
    Post
  },
}
</script>
