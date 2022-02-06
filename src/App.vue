<template>
<div class="container mt-3">
  <div class="jumbotron addList">
    <div class="form-group row addList">
      <h3 class="col-md-3 col-form-label">
        What will be on your next list?
      </h3>
      <div class="col-md-4">
        <input type="text" class="form-control" v-model="item">
      </div>
      <div class="col-md-12 mt-3">
        <button class="btn btn-primary btn-lg" @click="addList">Create List</button>
      </div>
    </div>
  </div>
</div>

<div class="container mt-2">
  <div class="jumbotron text-center start" v-if="Object.keys(this.list).length < 1">
    <h1> Add new list to get started </h1>
  </div>
</div>

<div class="container" v-if="Object.keys(this.list).length > 0">
  <div class="card mt-2 start" v-for="(item, index) in Object.entries(list)" :key="index">
    <div class="card-header text-center">
      <h3>{{ item[0] }}</h3>
    </div>
    <div class="card-body">
      <ul>
        <li v-for="val in list[item[0]]" :key="val"> 
          {{ val }}
        </li>
      </ul>
    </div>
    <div class="card-footer">
      <div class="col-md-10 addListItems offset-md-1">
        <h3> Add {{ item[0] }} </h3>
        <div class="form-group row">
          <h3 class="col-md-2 col-form-label">
            Name
          </h3>
          <div class="col-md-4">
            <input type="text" class="form-control" v-model="temp[index]">
          </div>
          <div class="col-md-12 mt-3">
            <button class="btn btn-primary btn-lg" @click="addSubItem(item[0], index)">Submit</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      item: '',
      subItem: '',
      list: {
      },
      listItem: [],
      temp: [],
    }
  },
  created() {
    // for (const key of Object.entries(this.list)) {
    //   console.log(key[0]);
    // }
  },
  methods: {
    addList() {
      this.list[this.item] = [];
    },
    addSubItem(parent, index){
      this.list[parent][this.list[parent].length] = this.temp[index]
      // this.list[parent] = this.temp[index]
    }
  },

}
</script>

<style scoped>
.addList {
  background: lightblue;
}

.addList input {
  border-radius: 0px;
}

.start {
  background: lightgreen;
}

.start .card-footer .addListItems {
  background: greenyellow;
  border: 1px solid black;
}

.start .card-footer .addListItems h3 {
  font-weight: bold;
}
</style>
