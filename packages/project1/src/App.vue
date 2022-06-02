<script setup lang="ts">
import HelloWorld from "./components/HelloWorld.vue";
import componentIndex from "@co2color/components";
import component1 from "@co2color/components/component1/component1.vue";
import component2 from "@co2color/components/component2/component2.vue";
import { clog } from "@co2color/utils";
import { add, sleep } from "@co2color/utils/tools";
sleep(2000).then(() => {
  clog(add(1, 2));
});
</script>

<template>
  <div class="wrapper">
    <HelloWorld msg="project1 started successfully" />
    <componentIndex />
    <component1 />
    <component2 />
  </div>
</template>
