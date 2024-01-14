<script setup lang="ts">
import { computed, ref } from 'vue';

// 6.1.1
const number = ref(80);
const showOrNot = computed(
  (): boolean => {
    let showOrNot = false;
    const rand = Math.round(Math.random() * 100);
    if(rand >= 50){
      showOrNot = true;
    }
    return showOrNot;
  }
);

// 6.1.2
const randomNumber = computed(
  (): number => {
    return Math.round(Math.random() * 100);
  }
);
</script>

<template>
  <!--6.1.1-->
  <p v-if="number >= 50">
    表示①
  </p>
  <p v-if="Math.round(Math.random() * 100) >= 50">
    表示②
  </p>
  <p v-if="showOrNot">
    表示③
  </p>

  <!--6.1.2-->
  <p>
    点数は{{ randomNumber }}点で
    <span v-if="randomNumber >= 80">優です。</span>
    <span v-else-if="randomNumber >= 70">良です。</span>
    <span v-else-if="randomNumber >= 60">可です。</span>
    <span v-else>不可です。</span>
  </p>

  <!--6.1.3-->
  <p>
    点数は{{ randomNumber }}点
    <template v-if="randomNumber >= 80">
      で優です。
      <span style="color: red;">素晴らしい！</span>
    </template>
  </p>

  <!--6.1.4-->
  <section>
    v-ifを利用
    <p v-if="showOrNot">
      条件に合致したので表示_6.1.4
    </p>
  </section>
  <section>
    v-showを利用
    <p v-show="showOrNot">
      条件に合致したので表示_6.1.4
    </p>
  </section>
</template>