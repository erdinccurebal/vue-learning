<template>
  <div>
    <div id="parent-area">
      <h3>Parent Component Emit Data: {{ emitData }}</h3>
      <emit-test @emitEvent="emitCatch($event)"></emit-test>
    </div>

    <div id="global-emitter">
      <h3>Parent Component Global Emit Data: {{ globalEmitData }}</h3>
      <global-emit-test></global-emit-test>
    </div>

    <div id="routes-area">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
      <router-view />
    </div>
  </div>
</template>


<script>
import EmitTest from "./components/EmitTest";
import GlobalEmitTest from "./components/GlobalEmitTest";

export default {
  data() {
    return {
      emitData: "NULL",
      globalEmitData: "NULL",
    };
  },
  components: {
    EmitTest,
    GlobalEmitTest,
  },
  methods: {
    emitCatch(eventData) {
      this.emitData = eventData;
    },
  },
  created() {
    this.emitter.on("globalEventEmit", (eventData) => {
      this.globalEmitData = eventData;
    }); // Global emit dinleme.
    // // this.emitter.all.clear() // Bütün emit dinlemelerini durdurur.
    this.emitter.on("*", (type, e) => console.log(type, e)); // Bütün eventleri dinler.
    this.emitter.off("globalEventEmit", (eventData) => {
      console.log("Off Emit", eventData)
    }); // Eventin fonksiyonunu durdurur. Event dinlenir ama fonksiyon gerçekleşmez.
  },
};
</script>

<style scoped>
#parent-area {
  background-color: bisque;
}

#routes-area {
  background-color: darkgray;
}

#global-emitter {
  background-color: cornflowerblue;
}

div {
  margin: 10px;
  padding: 10px;
}
</style>