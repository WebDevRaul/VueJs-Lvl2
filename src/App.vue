<template>
  <Title title='Hello world!' />
  <Age :age="age" @onUpdateAge="onUpdateAge" :updateAgeFn='onUpdateAgeCB' />
  <Slot>
    <template v-slot:1>
      <li>{{ one }}</li>
    </template>
    <template v-slot:2>
      <li>This is slot 2</li>
    </template>
    <template v-slot:3>
      <li>This is slot 3</li>
    </template>
  </Slot>
  <select v-model="componentName">
    <option value="Home">Home</option>
    <option value="About">About</option>
  </select>
  <keep-alive>
    <component :is="componentName"></component>
  </keep-alive>
</template>

<script>
import Title from './components/common/title/Title.vue';
import Age from './components/app/age/Age.vue';
import Slot from './components/common/slot/Slot.vue';
import Home from './components/app/home/Home.vue';
import About from './components/app/about/About.vue';

export default {
  name: 'App',
  components: { Title, Age, Slot, Home, About },
  data() {
    return {
      age: 20,
      one: 'This is slot 1',
      componentName: 'Home'
    }
  },
  methods: {
    onUpdateAge(num) {
      this.age += num
    },
    onUpdateAgeCB(num) {
      this.age += num
    }
  }
}
</script>