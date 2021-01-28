<template>
  <div>
    <h1>Global Emit Testing</h1>
    <input type="text" v-model="emitData" />
    <button @click="emitTrigger">Emit Trigger</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      emitData: "",
    };
  },
  methods: {
      emitTrigger(){
          this.emitter.emit("globalEventEmit", this.emitData);
      }
  }
};
</script>

<style>
</style>