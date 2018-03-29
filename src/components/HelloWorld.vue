<template>
  <div class="hello">
    <input placeholder="Enter nerdy thing" v-model="currentThing" v-on:keydown.enter="updateCurrentThing" />
    <br/>
    {{ currentThing }}
    <br/>
    <div>
      <h2>To Experience</h2>
      <div v-for="thing in toExperience" :key="thing.name"
        @click="markCompleted(thing)"
        :class="{
          completed: thing.completed
        }"
      >
        {{ thing.name }}
      </div>
      <h2>Experienced</h2>
      <div v-for="thing in experienced" :key="thing.name"
        @click="markCompleted(thing)"
        :class="{
          completed: thing.completed
        }"
      >
        {{ thing.name }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String
  },
  data() {
    return {
      exclamation: "!!!",
      nerdStuff: [],
      currentThing: ""
    };
  },
  computed: {
    toExperience: function() {
      return this.nerdStuff.filter(item => !item.completed);
    },
    experienced: function() {
      return this.nerdStuff.filter(item => item.completed);
    }
  },
  methods: {
    updateCurrentThing: function() {
      this.nerdStuff.push({
        name: this.currentThing,
        completed: false
      });
      this.currentThing = '';
    },
    markCompleted(thing) {
      thing.completed = !thing.completed;
      console.log(thing);
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.completed {
  color: lightgrey;
  text-decoration: line-through;
}
</style>
