<template>
  <div class="topnav">
    <span class="toggleAside" @click="toggleMenu"></span>
    <div class="logo">LOGO</div>
    <ul class="menu">
      <li>菜单1</li>
      <li>菜单2</li>
    </ul>
  </div>
</template>
<script lang="ts">
import { inject, Ref } from "vue";
export default {
  setup() {
    const menuVisible = inject<Ref<boolean>>("menuVisible"); //get
    const toggleMenu = () => {
      menuVisible.value = !menuVisible.value;
    };
    return { toggleMenu };
  },
};
</script>
<style lang="scss" scoped>
.topnav {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  background-color: pink;
  display: flex;
  padding: 16px;
  z-index: 10;
  justify-content: center;
  align-items: center;
  > .logo {
    max-width: 6em;
    margin-right: auto;
  }
  > .menu {
    display: flex;
    flex-direction: row;
    white-space: nowrap;
    flex-wrap: nowrap;
    > li {
      margin: 10px 1em;
    }
  }
  > .toggleAside {
    display: none;
    width: 24px;
    height: 24px;
    background-color: red;
    position: absolute;
    left: 16px;
    top: 50%;
    transform: translateY(-50%);
  }
  @media (max-width: 500px) {
    > .menu {
      display: none;
    }
    > .logo {
      margin: 0 auto;
    }
    > .toggleAside {
      display: inline-block;
    }
  }
}
</style>
