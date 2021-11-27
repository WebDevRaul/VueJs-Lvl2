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
  <button type="button" @click="flag = !flag">Toggle</button>
  <transition name='fade'>
    <h1 v-show="flag">Hello world!</h1>
  </transition>
  <transition name='fade' mode="out-in">
    <h1 v-if="flag" key="main">Hello world!</h1>
    <h1 v-else key="secondary">Hello world 2!</h1>
  </transition>

  <button type="button" @click="flag = !flag">Animation</button>
  <transition name='zoom' type='animation'>
    <h1 v-if="flag">Hello world!</h1>
  </transition>

  <transition
    @before-enter="beforeEnter"
    @enter="enter"
    @after-enter="afterEnter"
    @before-leave="beforeLeave"
    @leave="leave"
    @after-leave="afterLeave"
    @enter-cancel="enterCancel"
    @leave-cancel="leaveCancel"
    :css="false"
  >
    <h1 v-if="flag">Hello world!</h1>
  </transition>

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
      componentName: 'Home',
      flag: false
    }
  },
  methods: {
    onUpdateAge(num) {
      this.age += num
    },
    onUpdateAgeCB(num) {
      this.age += num
    },
    beforeEnter(el, ) {
      console.log('before-enter-hook', el)
    },
    enter(el, done) {
      console.log('enter-hook', el);
      const animation = el.animate(
        [{transform: "scale3D(0,0,0)"},{}],
        { duration: 1000 }  
      );
      animation.onfinish = () => done();
    },
    afterEnter(el) {
      console.log('after-enter-hook', el)
    },
    beforeLeave(el) {
      console.log('before-leave-hook', el)
    },
    leave(el, done) {
      console.log('leave-hook', el)
      const animation = el.animate(
        [{}, {transform: "scale3D(0,0,0)"}],
        { duration: 1000 }  
      );
      animation.onfinish = () => done();
    },
    afterLeave(el) {
      console.log('after-leave-hook', el)
    },
    enterCancel(el) {
      console.log('enter-cancel-hook', el)
    },
    leaveCancel(el) {
      console.log('leave-cancel-hook', el)
    }
  }
}
</script>

<style scoped>
  .fade-enter-from {
    opacity: 0;
  }
  .fade-enter-active {
    transition: all .25s linear;
  }
  .fade-leave-to {
    transition: all .25s linear;
    opacity: 0;
  }

  .zoom-enter-active {
    animation: zoom-in 1s linear forwards;
    transition: all 2s linear;
  }
  .zoom-leave-active {
    animation: zoom-out 1s linear forwards;
    transition: all 2s linear;
  }
  .zoom-enter-from {
    opacity: 0;
  }
  .zoom-leave-to {
    opacity: 0;
  }
  
  @keyframes zoom-in {
    from {
      transform: scale(0, 0);
    }
    to {
      transform: scale(1, 1);
    }
  }

  @keyframes zoom-out {
    from {
      transform: scale(1, 1);
    }
    to {
      transform: scale(0, 0);
    }
  }

</style>