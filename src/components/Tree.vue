<template>
      <li @hover="showButtons()">
        
                {{generation}}
          <a :href="'#'+id" class="member-box">
              <span class="imgCol"><img class="img-responsive" width="60px" src="/images/default.png"/></span>
              <span class="contentCol">
              <span class="member-name">{{name}}</span>
              <span class="detailBtn"><i @click="getDetails(id,name)" class="fa fa-info-circle fa-2x"></i>
              </span>
        <span><i @click="setSelected(id,name)" class="fa fa-plus fa-2x"></i></span>
            </span>
              
          </a>
          <ul class="clearfix" v-if="isParent && children.length > 0">
            <tree 
              v-for="(item,index) in children" 
              :children="item.children" 
              :name="item.name"
              :id="item.id"
              :generation="item.generation"
              v-bind:key="index"
            />
          </ul>
      </li>
  
  
</template>
<script>
    // import Vuex from 'vuex';

  export default { 
    props: [ 'name', 'children','id','generation' ],
    name: 'tree',
    computed:{
      isParent(){
        return this.children &&
        this.children.length
      }
    },
    methods:{
      getDetails(id,name)
      {
        this.$store.dispatch('setSelected',{id,name});

      },
      setSelected(id,name)
      {
        this.$store.dispatch('setSelected',{id,name});
        $("#addModal").modal("show");
      },
      showButtons()
      {
        console.log("hello");
      }
    }
  }
  
</script>