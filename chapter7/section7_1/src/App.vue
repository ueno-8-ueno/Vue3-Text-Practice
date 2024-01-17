<script setup lang="ts">
import { ref, watchEffect, watch } from "vue";

// 7.1.2
const cocktailNo = ref(1);
const priceMsg = ref("");
/*watchEffect(
  (): void => {
    priceMsg.value = getCocktailInfo(cocktailNo.value);
  }
);*/
setInterval(
  (): void => {
    cocktailNo.value = Math.round(Math.random() * 3) + 1;
  },
  1000
);

interface Cocktail{
  id: number;
  name: string;
  price: number;
}

function getCocktailInfo(cocktailNo: number){
  const cocktailDataListInit = new Map<number, Cocktail>();
  cocktailDataListInit.set(1, {id: 1, name: "ホワイトレディ", price: 1200});
  cocktailDataListInit.set(2, {id: 2, name: "ブルーハワイ", price: 1500});
  cocktailDataListInit.set(3, {id: 3, name: "ニューヨーク", price: 1100});
  cocktailDataListInit.set(4, {id: 4, name: "マティーニ", price: 1500});
  const cocktail = cocktailDataListInit.get(cocktailNo);
  let msg = "該当カクテルはありません。";
  if(cocktail != undefined){
    msg = `該当するカクテルは${cocktail.name}で、価格は${cocktail.price}円です。`;
  }
  return msg;
}

// 7.1.3
/*watch(cocktailNo,
  (): void => {
    priceMsg.value = getCocktailInfo(cocktailNo.value);
  }
);*/

// 7.1.4
/*watch(cocktailNo,
  (): void => {
    priceMsg.value = getCocktailInfo(cocktailNo.value);
  },
  {immediate: true}
);*/

// 7.1.5
watch(cocktailNo,
  (newVal: number, oldVal: number): void => {
    let msg = "前のカクテル: ";
    msg += getCocktailInfo(oldVal);
    msg += "現在のカクテル: ";
    msg += getCocktailInfo(newVal);
    priceMsg.value = msg;
  }
);

</script>

<template>
  <!--7.1.2, 3, 4, 5-->
  <p>現在のカクテル番号: {{ cocktailNo }}</p>
  <p>{{ priceMsg }}</p>
</template>