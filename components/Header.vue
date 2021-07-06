<template>
  <div>
    <b-navbar id="navbar" toggleable="lg" type="dark" fixed="top">
        <b-navbar-brand to="/">
            <img width="36px" height="36px" src="~/assets/images/logo.png" alt="logo" />
            <span class="brand-name space-blue">CODE </span>
            <span class="brand-name">SPACE</span>
        </b-navbar-brand>

        <b-navbar-toggle target="header-nav-collapse"></b-navbar-toggle>

        <b-collapse id="header-nav-collapse" class="justify-content-end text-right" is-nav>
            <b-navbar-nav>
                <b-nav-item to="/" active exact exact-active-class="space-blue">HOME</b-nav-item>
                <!-- <b-nav-item href="/#services" exact-active-class="space-blue">SERVICES</b-nav-item> -->
                <b-nav-item to="/portfolio" exact exact-active-class="space-blue">PORTFOLIO</b-nav-item>
                <b-nav-item to="/blog" exact exact-active-class="space-blue">BLOG</b-nav-item>
                <b-nav-item v-if="$route.path === '/'" href="#contact" exact-active-class="space-blue">CONTACT</b-nav-item>
            </b-navbar-nav>
        </b-collapse>
    </b-navbar>
  </div>
</template>

<style scoped>

    /* #navbar {
        background-color: #040004;
    } */

    .navbar-dark .navbar-nav .nav-link {
        color: white;
    }

    .navbar-dark .navbar-nav .nav-link:hover {
        color: var(--space-blue) !important;
    }
</style>