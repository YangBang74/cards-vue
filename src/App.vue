<script setup>
import { ref } from 'vue'

const left = [
  {
    id: 1,
    name: 'Shoes 1',
    image: '/shoes-1.avif',
  },
  {
    id: 2,
    name: 'Shoes 2',
    image: '/shoes-2.avif',
  },
  {
    id: 3,
    name: 'Shoes 3',
    image: '/shoes-3.avif',
  },
  {
    id: 4,
    name: 'Shoes 4',
    image: '/shoes-4.avif',
  },
  {
    id: 5,
    name: 'T-shirt 1',
    image: '/t-shirt-1.webp',
  },
  {
    id: 6,
    name: 'T-shirt 2',
    image: '/t-shirt-2.webp',
  },
  {
    id: 7,
    name: 'T-shirt 3',
    image: '/t-shirt-3.webp',
  },
  {
    id: 8,
    name: 'T-shirt 4',
    image: '/t-shirt-4.webp',
  },
]

const right = [
  {
    id: 9,
    name: 'Jacket 1',
    image: '/jacket-1.jpg',
  },
  {
    id: 10,
    name: 'Jacket 2',
    image: '/jacket-2.jpg',
  },
  {
    id: 11,
    name: 'Jacket 3',
    image: '/jacket-3.jpg',
  },
  {
    id: 12,
    name: 'Jacket 4',
    image: '/jacket-4.jpg',
  },
  {
    id: 13,
    name: 'Hoodie 1',
    image: '/hoodie-1.avif',
  },
  {
    id: 14,
    name: 'Hoodie 2',
    image: '/hoodie-2.avif',
  },
  {
    id: 15,
    name: 'Hoodie 3',
    image: '/hoodie-3.avif',
  },
  {
    id: 16,
    name: 'Hoodie 4',
    image: '/hoodie-4.avif',
  },
]

const selectedLeft = ref([])
const selectedRight = ref(null)

function onUserSelect(item) {
  const idx = selectedLeft.value.findIndex((i) => i.id === item.id)
  if (idx > -1) {
    selectedLeft.value.splice(idx, 1)
  } else if (selectedLeft.value.length < 6) {
    selectedLeft.value.push(item)
  }
}

function onChoiceSelect(item) {
  selectedRight.value = item
}
</script>

<template>
  <div class="wrap">
    <div class="container">
      <div class="selected">
        <div class="selected__left">
          <div class="card__block" v-for="item in selectedLeft" :key="item.key">
            <img :src="item.image" alt="" class="card__block-img" />
          </div>
        </div>
        <div class="selected__right">
          <img :src="selectedRight.image" :alt="selectedRight.name" v-if="selectedRight" />
        </div>
      </div>
      <div class="cards">
        <div class="cards__wrap">
          <div v-for="(card, i) in left" :key="i" class="card__block">
            <img
              class="card__block-img"
              :src="card.image"
              :alt="card.name"
              @click="onUserSelect(card)"
            />
          </div>
        </div>
        <div class="cards__wrap">
          <div
            v-for="(card, i) in right"
            :key="i"
            class="card__block"
            @click="onChoiceSelect(card)"
          >
            <img class="card__block-img" :src="card.image" :alt="card.name" />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style>
.wrap {
  font-family: 'Arial', sans-serif;
  font-weight: 500;
  font-size: 1rem;
}
.container {
  padding: 0 100px;
}
.cards {
  margin: 30px 0;
  display: flex;
  justify-content: space-between;
  align-items: start;
  gap: 20px;
}

.cards__wrap {
  border-radius: 10px;
  border: 1px solid #000;
  padding: 20px;
  height: 100%;
  width: 100%;
  gap: 20px;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-evenly;
  align-items: start;
}

.card__block {
  width: 200px;
  height: 200px;
  border: 1px solid #000;
  border-radius: 10px;
}

.card__block-img {
  width: 100%;
  height: 200px;
  object-fit: cover;
  align-self: top;
  border-radius: 10px;
}

.selected {
  display: flex;
  justify-content: space-between;
  align-items: start;
}

.selected__left {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-evenly;
  padding: 10px;
  gap: 10px;
  border: 1px solid #000;
  width: 49%;
  min-height: 500px;
  border-radius: 10px;
}

.selected__right {
  width: 500px;
  height: 500px;
  border: 1px solid #000;
}

.selected__right img {
  object-fit: cover;
  width: 100%;
  height: 100%;
}
</style>
