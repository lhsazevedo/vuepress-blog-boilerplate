<template>
  <div
    class="container"
    :class="pageClasses"
  >
    <Blog
      :pages="$site.pages" 
      :page-size="$site.themeConfig.pageSize" 
      :start-page="$site.themeConfig.startPage" 
    />
    <!-- <Navbar
      v-if="shouldShowNavbar"
      @toggle-sidebar="toggleSidebar"
    /> -->

    <!-- <Page
      v-else
      :sidebar-items="sidebarItems"
    >
      <template #top>
        <slot name="page-top"/>
      </template>
      <template #bottom>
        <slot name="page-bottom"/>
      </template>
    </Page> -->
  </div>
</template>

<script>
import Blog from '@theme/components/Blog.vue';

export default {
  // components: { Home, Page, Navbar },
  components: { Blog },
  computed: {
    shouldShowNavbar () {
      const { themeConfig } = this.$site
      const { frontmatter } = this.$page
      if (
        frontmatter.navbar === false
        || themeConfig.navbar === false) {
        return false
      }
      return (
        this.$title
        || themeConfig.logo
        || themeConfig.repo
        || themeConfig.nav
        || this.$themeLocaleConfig.nav
      )
    },
    pageClasses () {
      const userPageClass = this.$page.frontmatter.pageClass
      return [
        {
          'no-navbar': !this.shouldShowNavbar,
        },
        userPageClass
      ]
    }
  },
}
</script>

<style lang="scss">
@import "~bulma/sass/utilities/initial-variables";
.navbar .navbar-item .icon.outbound {
  background-color: $white-bis !important;
}
.section {
  margin-top: 1rem;
}
</style>

<style src="bulma/bulma.sass" lang="sass"></style>