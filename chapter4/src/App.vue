<script setup lang="ts">
import { ref, computed } from "vue";

// 4.1.2
const url = ref("https://vuejs.org/");

// 4.1.3
const isSendButtonDisabled = ref(true);

// 4.1.4
const widthOrHeight = ref("height");
const widthOrHeightValue = ref(100);

// 4.1.5
const imgAttributes = ref({
  src: "/images/logo.svg",
  alt: "Vueのロゴ",
  width: 75,
  height: 75
});

// 4.1.6(抜粋)
const msg = ref("Hello Vue!!");
const msgTextRed = ref("red");
const msgStyles = ref({
  color: "pink",
  fontSize: "24px",
  backgroundColor: "gray"
});
const textSize = computed(
  (): string => {
    const size = Math.round(Math.random() * 25) + 10;
    return `${size}pt`;
  }
);

// 4.2.1
const randValue = ref("まだです");
const onButtonClick = (): void => {
  const rand = Math.round(Math.random() * 10);
  randValue.value = String(rand);
};

// 4.2.3
const mousePointerX = ref(0);
const mousePointerY = ref(0);
const onImageMouseMove = (event: MouseEvent): void => {
  mousePointerX.value = event.offsetX;
  mousePointerY.value = event.offsetY;
};

// 4.2.6
const msg2 = ref("未送信");
const onFormSubmit = (): void => {
  msg2.value = "送信されました。";
};
</script>

<template>
  <!--4.1.2-->
  <p><a v-bind:href="url" target="_blank">Vue.jsのサイト</a></p>
  <p><a :href="url" target="_blank">Vue.jsのサイト(省略形)</a></p>
  <p><a v-bind:href="url + 'guide/introduction.html'" target="_blank">Vue.jsのガイドページ</a></p>

  <!--4.1.3-->
  <p><button type="button" v-bind:disabled="isSendButtonDisabled">送信</button></p>

  <!--4.1.4-->
  <p><img alt="VueLogo" src="./assets/logo.svg" v-bind:[widthOrHeight]="widthOrHeightValue"></p>

  <!--4.1.5-->
  <p><img v-bind="imgAttributes"></p>
  <p><img v-bind="imgAttributes" title="ロゴです!"></p>
  <p><img v-bind="imgAttributes" alt="ロゴです!"></p>

  <!--4.1.6(抜粋)-->
  <p v-bind:style="{color: msgTextRed}">{{ msg }}</p>
  <p v-bind:style="msgStyles">{{ msg }}</p>
  <p v-bind:style="{fontSize: textSize}">{{ msg }}</p>

  <!--4.2.1-->
  <section>
    <button v-on:click="onButtonClick">クリック!</button>
    <p>クリックの結果: {{ randValue }}</p>
  </section>

  <!--4.2.3-->
  <section>
    <img src="./assets/logo.svg" alt="Vueのロゴ" width="200" v-on:mousemove="onImageMouseMove">
    <p>ポインタの位置: x={{ mousePointerX }}; y={{ mousePointerY }}</p>
  </section>

  <!--4.2.6-->
  <form action="#" v-on:submit.prevent="onFormSubmit">
    <input type="text" required>
    <button type="submit">送信</button>
  </form>
  <p>{{ msg2 }}</p>

</template>