<template>
  <div class="nav-container d-flex justify-end align-center">
    <div class="tabs-container">
      <v-btn
        text
        v-for="(anchor, index) in anchors"
        :key="index"
        class="nav-menu"
        :class="{ active: activeSection == index }"
        @click="handleClick(index)"
      >
        <h3>{{ anchor }}</h3>
      </v-btn>
      <v-btn
        class="nav-menu reservation"
        text
        href="https://www.exploretock.com/freya"
        target="_blank"
        ><h3>Reserve a Table</h3></v-btn
      >
    </div>
    <v-btn icon @click="handleNavClick($event)" class="dash-nav-btn"
      ><v-icon class="open-icon" color="secondary">mdi-menu</v-icon></v-btn
    >
  </div>
</template>

<script>
import Drawer from "./Drawer.vue"
export default {
  components: { Drawer },
  props: {
    anchors: {
      type: Array,
      default: () => [],
    },
    activeSection: {
      type: Number,
      default: null,
    },
  },
  data: () => ({}),
  methods: {
    handleClick(value) {
      this.$emit("route-click", value)
    },
    handleNavClick(value) {
      this.$emit("nav-click")
    },
  },
}
</script>

<style lang="scss" scoped>
.nav-container {
  height: 7vh;
  width: 100%;
  transition: 0.5s;
  z-index: 6;
  padding-right: 5%;
  z-index: 999;

  .tabs-container {
    height: 100%;
    width: 50%;
    display: flex;
    justify-content: flex-end;
    align-items: center;
  }
}

.active {
  transition: 0.25s ease-in-out;
  position: relative;
  h3 {
    color: var(--light) !important;
  }
}

.active h3:before {
  content: "";
  background-color: var(--light);
  position: absolute;
  height: 5px;
  width: 100% !important;
  z-index: 5;
  bottom: -10px;
}

.nav-menu {
  font-size: 1.2rem !important;
  letter-spacing: 2px;
  color: var(--primary-light) !important;
  margin: 0 1rem;
  transition: 0.25s ease-in-out;
  position: relative;

  h3 {
    font-family: var(--font-body);
    font-size: 1.8rem !important;
    font-weight: 400;
    letter-spacing: 3px;
  }

  &:hover {
    color: var(--light);
  }
}

.dash-nav-btn {
  display: none;
}

.nav-menu h3:before {
  content: "";
  position: absolute;
  height: 5px;
  width: 0px;
  z-index: 5;
  bottom: -10px;
  transition: 0.5s ease-in-out;
}

.reservation {
  color: var(--secondary) !important;
  border: 1px solid var(--secondary);
}

@media (max-width: 600px) {
  .nav-container {
    height: 10vh;
    top: 0;
    z-index: 999;
  }

  .tabs-container {
    display: none !important;
  }

  .dash-nav-btn {
    display: block;
    position: absolute;
    top: 5vh;
    right: 2rem;
    border: 2px solid var(--light);
    .open-icon {
      color: var(--light) !important;
    }
  }
}

@media screen and (max-height: 400px) and (max-width: 850px) {
  .nav-container {
    height: 10vh;
    top: 0;
    z-index: 999;
  }

  .tabs-container {
    display: none !important;
  }

  .dash-nav-btn {
    display: block;
    position: absolute;
    top: 12vh;
    right: 4rem;
    border: 2px solid var(--light);
    .open-icon {
      color: var(--light) !important;
    }
  }
}
</style>
