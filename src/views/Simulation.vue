<template>
  <div class="simulation">
    <HelloWorld></HelloWorld>
    <ul>
      <li v-for="(todo, index) in todos" :key="index">
        <input @click="toggleTodoDone(index)" type="checkbox" :checked="todo.done">
        <span :class="{ done: todo.done }">{{todo.title}}</span>
      </li>
    </ul>


  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue';
import { mapState, mapMutations, mapActions } from 'vuex';

export default {
  name: 'simulation',
  components: {
    HelloWorld
  },
  computed: {
    newTodo: {
      get() {
        return this.$store.state.job;
      },
      set(value) {
        this.$store.commit('setNewTodo', value);
      }
    },
    ...mapState(['title', 'todos'])
  },
  methods: {
    ...mapMutations(['allDone']),
    ...mapActions(['updateTracker'])
  }
}
</script>
