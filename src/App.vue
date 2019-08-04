<template>
  <div id="app">
    <div class="tree">
      <ul class="clearfix">
        <Tree
          v-if="tree[Object.keys(tree)[0]]"
          :children="tree[Object.keys(tree)[0]].children"
          :name="tree[Object.keys(tree)[0]].name"
          :id="tree[Object.keys(tree)[0]].id"
          :generation="tree[Object.keys(tree)[0]].generation"
        />
      </ul>
    </div>
  </div>
</template>

<script>
import Tree from "./components/Tree.vue";

export default {
  name: "app",
  data() {
    return {
      tree: {
        "1": {
          id: 45,
          parent_id: 43,
          name: "Pralhad",
          children: [
            {
              id: 47,
              parent_id: 45,
              name: "Govind",
              generation: 26,
              children: [
                {
                  id: 50,
                  parent_id: 47,
                  name: "Narhar",
                  generation: 27,
                  children: [
                    {
                      id: 54,
                      parent_id: 50,
                      name: "Pramod",
                      generation: 28,
                      children: [
                        {
                          id: 64,
                          parent_id: 54,
                          name: "Varsha",
                          generation: 29,
                          children: [
                            {
                              id: 103,
                              parent_id: 64,
                              name: "Gandhar",
                              generation: 30,
                              children: []
                            }
                          ]
                        },
                        {
                          id: 65,
                          parent_id: 54,
                          name: "Sushma",
                          generation: 29,
                          children: []
                        },
                        {
                          id: 66,
                          parent_id: 54,
                          name: "Sampada",
                          generation: 29,
                          children: []
                        },
                        {
                          id: 67,
                          parent_id: 54,
                          name: "Prachi",
                          generation: 29,
                          children: []
                        },
                        {
                          id: 101,
                          parent_id: 54,
                          name: "sanket",
                          generation: 29,
                          children: []
                        }
                      ]
                    }
                  ]
                },
                {
                  id: 51,
                  parent_id: 47,
                  name: "Ganesh",
                  generation: 27,
                  children: []
                },
                {
                  id: 52,
                  parent_id: 47,
                  name: "Shrinivas",
                  generation: 27,
                  children: [
                    {
                      id: 104,
                      parent_id: 52,
                      name: "Nilesh",
                      generation: 28,
                      children: []
                    },
                    {
                      id: 105,
                      parent_id: 52,
                      name: "Shailesh",
                      generation: 28,
                      children: []
                    }
                  ]
                }
              ]
            }
          ],
          generation: 25
        }
      }
    };
  },
  components: {
    Tree
  }
};
</script>

<style>
body {
  background: #f5eec9;
}
/*Now the CSS*/
* {
  margin: 0;
  padding: 0;
}
.tree {
  width: 4000px;
  overflow-x: scroll;
}
.tree ul {
  padding-top: 20px;
  position: relative;

  transition: all 0.5s;
  -webkit-transition: all 0.5s;
  -moz-transition: all 0.5s;
}

.tree li {
  float: left;
  text-align: center;
  list-style-type: none;
  position: relative;
  padding: 20px 5px 0 5px;

  transition: all 0.5s;
  -webkit-transition: all 0.5s;
  -moz-transition: all 0.5s;
}

/*We will use ::before and ::after to draw the connectors*/

.tree li::before,
.tree li::after {
  content: "";
  position: absolute;
  top: 0;
  right: 50%;
  border-top: 4px solid #fff;
  width: 50%;
  height: 20px;
}
.tree li::after {
  right: auto;
  left: 50%;
  border-left: 4px solid #fff;
}

/*We need to remove left-right connectors from elements without 
any siblings*/
.tree li:only-child::after,
.tree li:only-child::before {
  display: none;
}

/*Remove space from the top of single children*/
.tree li:only-child {
  padding-top: 0;
}

/*Remove left connector from first child and 
right connector from last child*/
.tree li:first-child::before,
.tree li:last-child::after {
  border: 0 none;
}
/*Adding back the vertical connector to the last nodes*/
.tree li:last-child::before {
  border-right: 4px solid #fff;
  border-radius: 0 5px 0 0;
  -webkit-border-radius: 0 5px 0 0;
  -moz-border-radius: 0 5px 0 0;
}
.tree li:first-child::after {
  border-radius: 5px 0 0 0;
  -webkit-border-radius: 5px 0 0 0;
  -moz-border-radius: 5px 0 0 0;
}

/*Time to add downward connectors from parents*/
.tree ul ul::before {
  content: "";
  position: absolute;
  top: 0;
  left: 50%;
  border-left: 4px solid #fff;
  width: 0;
  height: 20px;
}

.member-box {
  border: 4px solid #fff;
  background: #ccc;
  height: 100px;
  padding: 7px;
  text-decoration: none;
  color: #000;
  font-family: arial, verdana, tahoma;
  font-size: 12px;
  display: table;
  width: 250px;
  text-align: center;
  word-wrap: break-word;
  font-weight: bold;
  margin: auto;
  border-radius: 5px;
  -webkit-border-radius: 5px;
  -moz-border-radius: 5px;

  transition: all 0.5s;
  -webkit-transition: all 0.5s;
  -moz-transition: all 0.5s;
}

.member-box img {
  float: left;
}

/*Time for some hover effects*/
/*We will apply the hover effect the the lineage of the element also*/
.tree li a:hover,
.tree li a:hover + ul li a {
  background: #f39c12;
  color: #000;
  border: 1px solid #94a0b4;
}
/*Connector styles on hover*/
.tree li a:hover + ul li::after,
.tree li a:hover + ul li::before,
.tree li a:hover + ul::before,
.tree li a:hover + ul ul::before {
  border-color: #94a0b4;
}

.contentCol {
  display: table-cell;
  vertical-align: middle;
  text-align: left;
}

.contentCol span {
  cursor: pointer;
}

.contentCol .displayBtn {
  margin-right: 4px;
}

.member-name {
  display: table-cell;
  vertical-align: middle;
  text-align: left;
  font-size: 15px;
}

span.imgCol {
  display: table-cell;
  vertical-align: middle;
}

.imgCol img {
  border: 2px solid #fff;
  border-radius: 6px;
}

/*Thats all. I hope you enjoyed it.
Thanks :)*/
</style>
