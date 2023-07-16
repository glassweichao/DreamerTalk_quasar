<!-- 这是一个房间列表的页面。结构为一个树形结构，根节点是房间名，叶子节点是用户信息；房间名后面的括号带着房间在线人数；用户信息为用户名加上用户状态的徽标。 -->
<template>
  <div class="q-pa-md q-gutter-sm">
    <q-tree
      :nodes="customize"
      node-key="label"
      default-expand-all
      v-model:expanded="expanded"
      no-connectors
    >
      <template v-slot:header-root="prop">
        <div class="row items-center">
          <div class="text-bold"  :style="{ fontSize: '18px' }">
            {{ prop.node.label }}
            <q-badge color="orange" class="q-ml-sm">{{ prop.node.children.length }}</q-badge>
          </div>
        </div>
      </template>

      <template v-slot:header-generic="prop">
        <div class="row items-center">
          <q-btn flat rounded color="primary" :label="prop.node.label" class="text-bold" :style="{ fontSize: '16px' }">
            <q-badge class="q-ml-sm" color="green" rounded/>
          </q-btn>
        </div>
      </template>

    </q-tree>
  </div>
</template>

<script>
import { ref } from 'vue'

export default {
  setup () {
    return {
      expanded: ref([ 'Satisfied customers (with avatar)', 'Good food (with icon)' ]),

      customize: ref([
        {
          label: '刷刷刷',
          header: 'root',
          children: [
            {
              label: '超哥哥',
              header: 'generic',
            },
            {
              label: '马楼',
              header: 'generic',
            }
          ]
        },
        {
          label: '打抢',
          header: 'root',
          children: [
            {
              label: '超哥哥',
              header: 'generic',
            },
            {
              label: '马楼',
              header: 'generic',
            },
            {
              label: '甘霖',
              header: 'generic',
            }
          ]
        },
        {
          label: '坐牢',
          header: 'root',
          children: [
            {
              label: '超哥哥',
              header: 'generic',
            },
            {
              label: '马楼',
              header: 'generic',
            },
            {
              label: '甘霖',
              header: 'generic',
            }
          ]
        }
      ])
    }
  },

  methods: {

  }
}
</script>

