<template>
  <div>
    <v-btn  color="blue"  style="radius: 20%; padding-top: 10px;" class="mr-4">
    Block Button
  </v-btn>
    <HelloWorld message01=" Jaronghi" />
    <v-btn @click="SetData()">click</v-btn>
  </div>
</template>

<script>
import HelloWorld from "../components/HelloWorld";

export default {
  name: "HomeView",

  components: {
    HelloWorld,
  },
  methods: {
    SetData() {
      this.$EventBus.$emit('SetData');
    },
  },
};
</script>
