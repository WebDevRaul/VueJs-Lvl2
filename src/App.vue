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
</template>

<script>
import Title from './components/common/title/Title.vue';
import Age from './components/app/age/Age.vue';
import Slot from './components/common/slot/Slot.vue';

export default {
  name: 'App',
  components: { Title, Age, Slot },
  data() {
    return {
      age: 20,
      one: 'This is slot 1'
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