<template>
  <div>
    <!-- Header section -->
    <header
      :class="{
        'h-14 lg:h-20 fixed w-full top-0 inset-0 z-20 bg-gradient-to-r from-green-900 to-blue-900 transition-transform duration-100': true,
        '-translate-y-full': !isHeaderVisible,
      }"
    >
      <div
        class="flex items-center justify-between mx-auto max-w-7xl h-full px-4 lg:px-0"
      >
        <!-- Logo and menu toggle button -->
        <div class="flex items-center gap-6">
          <button
            class="text-2xl p-1 text-black hover:text-blue-900 lg:hidden"
            @click="toggleMenu2"
          >
            {{ close2 ? "☰" : "✘" }}
          </button>
          <router-link
            to="/"
            class="flex items-center"
            @click.native="closeMenu"
          >
            <img
              src="../assets/logos.png"
              alt="Logo"
              class="h-10 lg:h-12 object-contain"
            />
          </router-link>
        </div>

        <!-- Navigation menu -->
        <nav
          :class="{ hidden: close2, flex: !close2 }"
          class="bg-black xl:bg-transparent lg:static lg:flex lg:items-center flex-1 justify-center absolute top-14 lg:top-0 left-0 w-full lg:w-auto z-30"
        >
          <!-- Navigation items -->
          <ul
            class="flex flex-col lg:flex-row gap-6 lg:gap-8 text-white lg:text-black mt-4 lg:mt-0 lg:items-center px-4 lg:px-0 font-semibold"
          >
            <li>
              <router-link
                to="/"
                class="hover:text-blue-900"
                active-class="hover:text-blue-900"
                @click.native="closeMenu"
                >Home</router-link
              >
            </li>
            <li class="relative group">
              <router-link
                to="/shop"
                class="hover:text-blue-900 flex items-center"
                active-class="hover:text-blue-900"
                @click.native="closeMenu"
              >
                <span>Shop</span>
                <span class="ml-1"></span>
              </router-link>
            </li>

            <li>
              <router-link
                to="/aboutus"
                class="hover:text-blue-900"
                active-class="hover:text-blue-900"
                @click.native="closeMenu"
                >About Us</router-link
              >
            </li>
            <li>
              <router-link
                to="/contact"
                class="hover:text-blue-900"
                active-class="hover:text-blue-900"
                @click.native="closeMenu"
                >Contact Us</router-link
              >
            </li>         
          </ul>
          <!-- Icons container -->
          <div class="flex items-end justify-end gap-12 ml-20">
            <!-- Cart icon -->
            <router-link to="/cart" class="text-white lg:text-black">
              <svg
                xmlns="http://www.w3.org/2000/svg"
                fill="none"
                viewBox="0 0 24 24"
                stroke-width="1.5"
                stroke="currentColor"
                class="size-6"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  d="M2.25 3h1.386c.51 0 .955.343 1.087.835l.383 1.437M7.5 14.25a3 3 0 0 0-3 3h15.75m-12.75-3h11.218c1.121-2.3 2.1-4.684 2.924-7.138a60.114 60.114 0 0 0-16.536-1.84M7.5 14.25 5.106 5.272M6 20.25a.75.75 0 1 1-1.5 0 .75.75 0 0 1 1.5 0Zm12.75 0a.75.75 0 1 1-1.5 0 .75.75 0 0 1 1.5 0Z"
                />
              </svg>
            </router-link>

            <!-- User icon -->
            <router-link to="/profile" class="text-white lg:text-black">
              <svg
                xmlns="http://www.w3.org/2000/svg"
                fill="none"
                viewBox="0 0 24 24"
                stroke-width="1.5"
                stroke="currentColor"
                class="size-6"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  d="M15.75 6a3.75 3.75 0 1 1-7.5 0 3.75 3.75 0 0 1 7.5 0ZM4.501 20.118a7.5 7.5 0 0 1 14.998 0A17.933 17.933 0 0 1 12 21.75c-2.676 0-5.216-.584-7.499-1.632Z"
                />
              </svg>
            </router-link>
          </div>
        </nav>
      </div>
    </header>
  </div>
</template>

<script>
export default {
  data() {
    return {
      close2: true,
      isHeaderVisible: true,
      lastScrollY: 0,
    };
  },
  computed: {
    isHomePage() {
      return this.$route.path === "/";
    },
  },
  watch: {
    $route(to, from) {
      if (to.path === "/") {
        this.close2 = true;
      }
    },
  },
  methods: {
    toggleMenu2() {
      this.close2 = !this.close2;
    },
    closeMenu() {
      this.close2 = true;
    },
    handleScroll() {
      const currentScrollY = window.scrollY;
      this.isHeaderVisible =
        currentScrollY < this.lastScrollY || currentScrollY <= 0;
      this.lastScrollY = currentScrollY;
    },
  },
  mounted() {
    window.addEventListener("scroll", this.handleScroll);
    if (this.isHomePage) {
      this.close2 = true;
    }
  },
  beforeDestroy() {
    window.removeEventListener("scroll", this.handleScroll);
  },
};
</script>

<style scoped>
button {
  font-size: 1rem;
}

/* Ensure nav covers hero section when opened on mobile */
nav {
  transition: all 0.3s ease-in-out;
}

/* Adjust visibility for icons on small screens */
@media (max-width: 1024px) {
  .icons-container {
    display: flex;
    gap: 1rem;
    margin-left: auto;
  }
}
</style>
