<script setup lang="ts">
import { ref } from 'vue';

// 6.2.2
const cocktailListInit: {[key: number]: string;} = {
  2345: "ホワイトレディ",
  4412: "ブルーハワイ",
  6792: "ニューヨーク"
};
const cocktailList = ref(cocktailListInit);

// 6.2.3
const cocktailListInit623 = new Map<number, string>();
cocktailListInit623.set(2345, "ホワイトレディ");
cocktailListInit623.set(4412, "ブルーハワイ");
cocktailListInit623.set(6792, "ニューヨーク");
const cocktailList623 = ref(cocktailListInit623);

// 6.2.4
const whiteLadyInit: {
  id: number;
  name: string;
  price: number;
  recipe: string;
} = {
  id: 2345,
  name: "ホワイトレディ",
  price: 1200,
  recipe: "ジン30mlなどなど"
};
const whiteLady = ref(whiteLadyInit);

// 6.2.5
const cocktailDateListInit: Cocktail[] = [
  {id: 2345, name: "ホワイトレディ", price: 1200},
  {id: 4412, name: "ブルーハワイ", price: 1500}
];
const cocktailDateList = ref(cocktailDateListInit);

interface Cocktail{
  id: number;
  name: string;
  price: number;
}
</script>

<template>
  <!--6.2.2-->
  <ul>
    <li
      v-for="(cocktailName, id) in cocktailList"
      v-bind:key="'cocktailList' + id">
      IDが{{ id }}のカクテルは{{ cocktailName }}
    </li>
  </ul>
  <ul>
    <li
      v-for="(cocktailName, id, index) in cocktailList"
      v-bind:key="'cocktailListWithIdx' + id">
      {{ index + 1 }}: IDが{{ id }}のカクテルは{{ cocktailName }}
    </li>
  </ul>

  <!--6.2.3-->
  <ul>
    <li
      v-for="[id, cocktailName] in cocktailList623"
      v-bind:key="'6.2.3_' + id">
      IDが{{ id }}のカクテルは{{ cocktailName }}
    </li>
  </ul>

  <!--6.2.4-->
  <dl>
    <template
      v-for="(value, key) in whiteLady"
      v-bind:key="key">
      <td>{{ key }}</td>
      <dd>{{ value }}</dd>
    </template>
  </dl>

  <!--6.2.5-->
  <ul>
    <li
      v-for="cocktailItem in cocktailDateList"
      v-bind:key="cocktailItem.id">
      {{ cocktailItem.name }}の値段は{{ cocktailItem.price }}円
    </li>
  </ul>
</template>