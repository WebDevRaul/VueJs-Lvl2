<template>
  <Title title='Hello world!' />
  <Age :age="age" @onUpdateAge="onUpdateAge" />
</template>

<script>
import Title from './components/common/title/Title.vue';
import Age from './components/app/age/Age.vue';

export default {
  name: 'App',
  components: { Title, Age },
  data() {
    return {
      age: 20
    }
  },
  methods: {
    onUpdateAge(num) {
      this.age += num
    }
  }
}
</script>