<template>
  <div class="box">
    <ul v-for="(item, index) in tagTree" :key="index" class="about">
      <li v-for="(itm1, idx1) in item.child" :key="idx1">
        {{itm1.id}}{{JSON.stringify(getOwnTag(item))}}
        <ul>
          <li v-for="(itm2, idx2) in itm1.child" :key="idx2">
            {{itm2.id}}
            <ul>
              <li v-for="(itm3,idx3) in itm2.child" :key="idx3">
                {{itm3.id}}
                <ul>
                  <li v-for="(itm4,idx4) in itm3.child" :key="idx4">
                    {{itm4.id}}
                  </li>
                </ul>
              </li>
            </ul>
          </li>
        </ul>
      </li>
    </ul>
    <ul class="selected">
      <li v-for="(item, index) in checkedKeys" :keys="index">{{item}}</li>
    </ul>
  </div>
</template>

<script>
 function getNodesFromTree(tree, key, accu) {
  console.log('参数', tree, key, accu)
  let list = [];
  if(accu && accu.length > 0) {
    list = accu;
  }
  if(tree.id === key) {
    list.push(tree)
    console.log(list)
    return list
  } else {
    if(tree.child && tree.child.length > 0) {
      tree.child.some((childTag)=>{
        let flag = getNodesFromTree(childTag, key, list)
        if(flag && flag.length > 0) {
          return true
        }
      })
    }
  }
}
export default {
  data() {
    return {
      tagTree: [
        {
          name: 'A',
          id: 'A',
          child: [
            {
              name: 'a',
              id: 'A-a',
              child: [
                {
                  name: '1',
                  id: 'A-a-1',
                  child: [
                    {
                      id: 'A-a-1-1'
                    }
                  ]
                },
                {
                  name: '2',
                  id: 'A-a-2',
                },
                {
                  name: '3',
                  id: 'A-a-3',
                },
                {
                  name: '4',
                  id: 'A-a-4',
                },
                {
                  name: '5',
                  id: 'A-a-5',
                },
              ]
            },
            {
              name: 'b',
              id: 'A-b',
              child: [
                {
                  name: '1',
                  id: 'A-b-1',
                },
                {
                  name: '2',
                  id: 'A-b-2',
                },
                {
                  name: '3',
                  id: 'A-b-3',
                },
                {
                  name: '4',
                  id: 'A-b-4',
                },
                {
                  name: '5',
                  id: 'A-b-5',
                },
              ]
            },
            {
              name: 'c',
              id: 'A-c',
              child: [
                {
                  name: '1',
                  id: 'A-c-1',
                },
                {
                  name: '2',
                  id: 'A-c-2',
                },
                {
                  name: '3',
                  id: 'A-c-3',
                  child: [
                    {
                      name: '3-1',
                      id: 'A-c-3-1',
                    }
                  ]
                },
                {
                  name: '4',
                  id: 'A-c-4',
                },
                {
                  name: '5',
                  id: 'A-c-5',
                },
              ]
            },
          ]
        },
        {
          name: 'B',
          id: 'B',
          child: [
            {
              name: 'a',
              id: 'B-a',
              child: [
                {
                  name: '1',
                  id: 'B-a-1',
                },
                {
                  name: '2',
                  id: 'B-a-2',
                },
                {
                  name: '3',
                  id: 'B-a-3',
                },
                {
                  name: '4',
                  id: 'B-a-4',
                },
                {
                  name: '5',
                  id: 'B-a-5',
                },
              ]
            },
            {
              name: 'b',
              id: 'B-b',
              child: [
                {
                  name: '1',
                  id: 'B-b-1',
                },
                {
                  name: '2',
                  id: 'B-b-2',
                },
                {
                  name: '3',
                  id: 'B-b-3',
                },
                {
                  name: '4',
                  id: 'B-b-4',
                },
                {
                  name: '5',
                  id: 'B-b-5',
                },
              ]
            },
            {
              name: 'c',
              id: 'B-c',
              child: [
                {
                  name: '1',
                  id: 'B-c-1',
                },
                {
                  name: '2',
                  id: 'B-c-2',
                },
                {
                  name: '3',
                  id: 'B-c-3',
                },
                {
                  name: '4',
                  id: 'B-c-4',
                },
                {
                  name: '5',
                  id: 'B-c-5',
                },
              ]
            },
          ]
        },
        {
          name: 'C',
          id: 'C',
          child: [
            {
              name: 'a',
              id: 'C-a',
              child: [
                {
                  name: '1',
                  id: 'C-a-1',
                },
                {
                  name: '2',
                  id: 'C-a-2',
                },
                {
                  name: '3',
                  id: 'C-a-3',
                },
                {
                  name: '4',
                  id: 'C-a-4',
                },
                {
                  name: '5',
                  id: 'C-a-5',
                },
              ]
            },
            {
              name: 'b',
              id: 'C-b',
              child: [
                {
                  name: '1',
                  id: 'C-b-1',
                },
                {
                  name: '2',
                  id: 'C-b-2',
                },
                {
                  name: '3',
                  id: 'C-b-3',
                },
                {
                  name: '4',
                  id: 'C-b-4',
                },
                {
                  name: '5',
                  id: 'C-b-5',
                },
              ]
            },
            {
              name: 'c',
              id: 'C-c',
              child: [
                {
                  name: '1',
                  id: 'C-c-1',
                },
                {
                  name: '2',
                  id: 'C-c-2',
                },
                {
                  name: '3',
                  id: 'C-c-3',
                },
                {
                  name: '4',
                  id: 'C-c-4',
                },
                {
                  name: '5',
                  id: 'C-c-5',
                },
              ]
            },
          ]
        },
        {
          name: 'D',
          id: 'D',
          child: [
            {
              name: 'a',
              id: 'D-a',
              child: [
                {
                  name: '1',
                  id: 'D-a-1',
                },
                {
                  name: '2',
                  id: 'D-a-2',
                },
                {
                  name: '3',
                  id: 'D-a-3',
                },
                {
                  name: '4',
                  id: 'D-a-4',
                },
                {
                  name: '5',
                  id: 'D-a-5',
                },
              ]
            },
            {
              name: 'b',
              id: 'D-b',
              child: [
                {
                  name: '1',
                  id: 'D-b-1',
                },
                {
                  name: '2',
                  id: 'D-b-2',
                },
                {
                  name: '3',
                  id: 'D-b-3',
                },
                {
                  name: '4',
                  id: 'D-b-4',
                },
                {
                  name: '5',
                  id: 'D-b-5',
                },
              ]
            },
            {
              name: 'c',
              id: 'D-c',
              child: [
                {
                  name: '1',
                  id: 'D-c-1',
                },
                {
                  name: '2',
                  id: 'D-c-2',
                },
                {
                  name: '3',
                  id: 'D-c-3',
                },
                {
                  name: '4',
                  id: 'D-c-4',
                },
                {
                  name: '5',
                  id: 'D-c-5',
                },
              ]
            },
          ]
        },
        {
          name: 'E',
          id: 'E',
          child: [
            {
              name: 'a',
              id: 'E-a',
              child: [
                {
                  name: '1',
                  id: 'E-a-1',
                  child: [
                    {
                      name: '1-1',
                      id: 'E-a-1-1',
                      child: [
                        {
                          name: '1-1-1',
                          id: 'E-a-1-1-1',
                        }
                      ]
                    }
                  ]
                },
                {
                  name: '2',
                  id: 'E-a-2',
                },
                {
                  name: '3',
                  id: 'E-a-3',
                },
                {
                  name: '4',
                  id: 'E-a-4',
                },
                {
                  name: '5',
                  id: 'E-a-5',
                },
              ]
            },
            {
              name: 'b',
              id: 'E-b',
              child: [
                {
                  name: '1',
                  id: 'E-b-1',
                },
                {
                  name: '2',
                  id: 'E-b-2',
                },
                {
                  name: '3',
                  id: 'E-b-3',
                },
                {
                  name: '4',
                  id: 'E-b-4',
                },
                {
                  name: '5',
                  id: 'E-b-5',
                },
              ]
            },
            {
              name: 'c',
              id: 'E-c-3',
            },
          ]
        },
      ],
      checkedKeys: [
          'A-a-2',
          'A-a-1-1',
          'A-b-3',
          'A-c-3-1',
          'B-b-1',
          'E-a-1-1-1',
          'B-a-3',
          'C-b-2',
          'E-c-3',
          'D-a-2',
      ],
      list1: [],
    }
  },
  computed: {
    getOwnTag() {
      return function(item) {
        // console.log(items)
        this.checkedKeys.forEach((id)=>{
          getNodesFromTree(item, id)
        })
        return this.checkedKeys
      }
    }
  },
  methods: {

  }
}
</script>

<style>
.box {
  position: relative;
}
.selected {
  position: absolute;
  right: 300px;
  top: 100px;
}
.about {
  width: 50%;
  margin-right: auto;
}
</style>
