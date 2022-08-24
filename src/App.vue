<template>
  <div id="app">
    <TimeLine :timelineData="timelineData" />
    <div class="form-group">
      <input
        v-model="item"
        class="input"
        type="text"
        placeholder="Add Item"
        @keyup.enter="addItem"
      />
      <button class="btn" @click="addItem">Add</button>
    </div>
  </div>
</template>

<script>
import TimeLine from "./components/TimeLine";

export default {
  name: "App",
  components: {
    TimeLine,
  },
  data() {
    return {
      item: "",
      timelineData: [],
    };
  },
  methods: {
    addItem() {
      const payload = {
        date: new Date(),
        desc: this.item,
      };

      this.timelineData.push(payload);
    },
  },
};
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

#app {
  font-family: sans-serif;
  background-color: #ecf4f4;
  color: #fff;
  min-height: 100vh;
  width: 100%;
  display: flex;
  align-items: center;
  flex-direction: column;
  justify-content: center;
}
.form-group {
  margin-bottom: 20px;
  & .input {
    height: 40px;
    padding: 3px 5px;
    border: none;
    outline: none;
  }
  & .btn {
    height: 40px;
    border: none;
    border-radius: 5px;
    background-color: #fff;
    margin-left: 5px;
    padding: 5px 25px;
    &:hover {
      cursor: pointer;
    }
  }
}
</style>
