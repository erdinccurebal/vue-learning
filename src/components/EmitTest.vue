<template>
  <div>
      <h1>Emit Testing</h1>
      <input type="text" v-model="emitData">
      <button @click="emitTrigger">Emit Trigger</button>
  </div>
</template>

<script>
export default {
    data(){
        return {
            emitData: ''
        };
    },
    methods: {
        emitTrigger(){
            this.$emit("emitEvent", this.emitData);
        }
    }
};
</script>

<style>

</style>