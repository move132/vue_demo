<template>
    <div class="hello">
        <h1>{{ msg }}</h1>
        <h2>Essential Links</h2>
        <h1>{{msg1}}</h1>
        <input type="text"  v-model="msg1"/>
        <button v-on:click="clickHandler">clickHandler</button>
        <div v-bind:title="message" v-bind:msg="msg" v-bind:xixi="msg1">
            Hover your mouse over me for a few seconds to see my dynamically bound title!
        </div>
        <ul>
            <li v-for="item in items" v-on:click="liItemClick(item)" v-bind:class="{ through: item.isthrough }">
                {{item.title}}
                {{item.lable}}
                <span v-on:click="item_del(item)"></span>
            </li>
        </ul>
    </div>
</template> 

<script>
export default {
  name: 'hello',
  data () {
    return {
      msg: 'Welcome to Your App',
      msg1:'',
      message: 'You loaded this page on ',
      items:[{
        lable:'22222',
        title:'Hello.vue',
        isthrough:false
      },{
        lable:'4444',
        title:'Hello. word vue!!',
        isthrough:true
      }]
    }
  },
  methods:{
    clickHandler: function (e) {
        this.items.push({
            lable:this.msg1,
            title:this.message+  new Date().getTime(),
            isthrough:false
        });
        //this.msg1='';
        console.log(this.msg1);
    },
    liItemClick:function(item){
        item.isthrough= !item.isthrough;
        console.log(item);

    },
    item_del:function(item){
      this.items.splice(this.items.indexOf(item.lable),1);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

  @import '../styles/variable.scss';

</style>