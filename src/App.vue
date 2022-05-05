<template>
  <TheNavigation />
  <div class="container">
    <!-- <router-view class="view left-sidebar" name="LeftSidebar" :key="$route.path"></router-view> -->
    <router-view v-slot="{Component}" class="view left-sidebar" name="LeftSidebar">
      <transition name="fade" mode="out-in">
        <component :is="Component" :key="$route.path"></component>
      </transition> 
    </router-view>
    <!-- Main View -->
    <router-view v-slot="{Component}" class="view main-content">
      <transition name="fade" mode="out-in">
        <component :is="Component" :key="$route.path"></component>
      </transition>
    </router-view>
  </div>
</template>

<script setup>
import TheNavigation from './components/TheNavigation.vue';

</script>

<style>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

.container {
  display: flex;

}

.left-sidebar {
  width: 20%;
}

.main-content {
  width: 100%;
}
</style>
