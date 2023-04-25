<template>
  <div>
    <button type="button" @click="assign">!</button>
    <ul v-for="(i, j) in arr" :key="j">
      <li>
        <input type="text" v-model="i.name" @input="dbtn" />
      </li>
      <li>
        <input type="text" v-model="i.id" />
      </li>
    </ul>
    <ul>
      <li>
        <button type="button" :disabled="per">?</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      arr: [
        { name: "su", id: 1 },
        { name: "di", id: 2 },
        { name: "", id: 3 },
      ],
      arrdup: [],
      per: true,
    };
  },
  methods: {
    // dbtn() {
    //   let count = 0;
    //   let nCount = 0;
    //   for (let i = 0; i < this.arr.length; i++) {
    //     if (this.arr[i].name !== "") {
    //       if (this.arr[i].name !== this.arrdup[i].name) {
    //         count = count + 1;
    //       }
    //     } else {
    //       nCount++;
    //     }
    //   }
    //   this.per = count !== this.arrdup.length - nCount;
    // },
    dbtn() {
  let count = 0;
  let nCount = 0;
  
  // Using array.reduce() to calculate count and nCount

 
  count = this.arr.reduce((acc, item, index) => {
    if (item.name !== "") {
      if (item.name !== this.arrdup[index].name) {
        return acc + 1;
      }
    }
    return acc;
  }, 0);
  
  nCount = this.arr.reduce((acc, item) => {
    if (item.name === "") {
      return acc + 1;
    }
    return acc;
  }, 0);

  this.per = count !== this.arrdup.length - nCount;
}
  },
  // methods: {
  //   nameChanged(id) {
  //     const item = this.arr.find(item => item.id===id);
  //     const itemdup = this.arrdup.find(item => item.id === id)
  //     if(itemdup.name===item.name){
  //       this.per=true
  //     }
  //     else{this.per=false}
  //   },
  // },
  created() {
const All="All"
  this.arrdup={
    'All':[...this.arr]
  }
    // this.arrdup = JSON.parse(JSON.stringify(this.arr));
    console.log(this.arrdup[All]);
  },
};
</script>
<!-- <script >
export default {
  data(){
    return{
      arr:[{name:"su",id:1},{name:"di",id:2},{name:"p",id:3}],
      arrdup:[],
    }
  },

computed: {
  dbtn() {
    return (c, d) => {
      if (this.arrdup[d] && this.arrdup[d].name) {
        return c.name === this.arrdup[d].name;
      } else {
        return false;
      }
    }
  }
},
 created(){

    
      (this.arr).forEach(element => {
        var obj = {...element};
        this.arrdup.push(obj);
      });
      console.log("Assigned")
   
  }
}
</script> -->

<style scoped>
li {
  text-decoration: none;
  display: inline;
  margin-left: 3px;
}
</style>
