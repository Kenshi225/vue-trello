<template>
  <div class="home">
    <div id="header">
      <img alt="Vue logo" src="../assets/logo.png" width="30" height="30">
      <h2>Vue Trello</h2>
    </div>
    <div id="main">
      <h2>boards</h2>
      <p class="total-tasks">ALL: 0 tasks</p>
      <div class="list-index">
        <list v-for="(item, index) in lists" 
          :key="item.id" 
          :title="item.title" 
          :listIndex="index" />
        <list-add />
      </div>
    </div>
  </div>
</template>

<script>
import ListAdd from './ListAdd'
import List from './List'
import { mapState } from 'vuex'
export default {
  components: {
    ListAdd,
    List,
  },
  computed: {
    ...mapState([
      'lists'
    ]),
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#header {
  background: teal;
  display: flex;
  padding: 10px 0;
}
#header > img {
  margin: auto 10px;
}
#header > p {
  margin: auto 0;
}
#main {
  margin: 10px 30px;
  padding: 0 10px;
  width: calc(100% - 40px);
  height: 100%;
}
h3 {
  padding: 20px 10px;
  border-bottom: 1px solid silver;
}
ul {
  list-style-type: none;
  padding: 0;
}
.task {
  height: 60px;
  margin: 5px 10px;
  background: white;
  border-radius: 2px;
  box-shadow: 2px 2px 2px;
}
a {
  color: #42b983;
}
.board {
  width: 200px;
  display: inline-block;
  vertical-align: top;
  background: rgb(221, 221, 221);
  margin: 5px 2px;
  border-radius: 2px;
  color: dimgray;
}

.list-index {
  display: flex;
}

.addlist {
  margin-top: 15px;;
  display: inline-block;
  flex-direction: column;
  align-items: flex-start;
  min-width: 320px;
  width: 320px;
}

.text-input {
  padding: 20px 15px;
  width: calc(100% - 30px);
  background-color: #ccc;
  border-radius: 8px;
  cursor: pointer;
  border: none;
  font-family: "Noto Sans Japanese", "Noto Sans", 'system-ui', sans-serif;
  font-weight: 700;
  font-size: 24px;
  color: #242424;
  cursor: pointer;
  overflow: overlay;
}

.text-input:focus {
  outline: 0;
  cursor: initial;
}

.add-button {
  margin-top: 15px;
  padding: 15px 18px;
  background-color: #999;
  border: none;
  border-radius: 8px;
  font-family: "Noto Sans Japanese", "Noto Sans", 'system-ui', sans-serif;
  font-weight: 700;
  font-size: 18px;
  color: #fff;
}

.add-button:hover {
  opacity: 0.8;
  cursor: pointer;
}

.active .text-input {
  background-color: #fff;
}
.addable .add-button {
  background-color: lightgreen;
  pointer-events: auto;
  cursor: pointer;
}

.add-button:active {
  background-color: #00d78f;
}
</style>
