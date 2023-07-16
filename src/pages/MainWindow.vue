<template>
  <q-page class="q-pa-md">
    <div class="q-gutter-md">
      <!-- 头像部分 -->
      <q-card class="q-pa-md" :flat="true" :bordered="true">
        <div class="q-items-center text-left text-h5">
          <div>{{ userName }}</div>
        </div>
      </q-card>

      <!-- 房间列表部分 -->
      <q-card class="q-gutter-md">
        <q-tree
          :nodes="customize"
          node-key="label"
          default-expand-all
          v-model:expanded="expanded"
          no-connectors
        >
          <template v-slot:header-root="prop">
            <div class="row items-center">
              <div class="text-bold" :style="{ fontSize: '18px' }">
                {{ prop.node.label }}
                <q-badge color="orange" class="q-ml-sm">{{
                  prop.node.children.length
                }}</q-badge>
              </div>
            </div>
          </template>

          <template v-slot:header-generic="prop">
            <div class="row items-center">
              <q-btn
                flat
                rounded
                color="primary"
                :label="prop.node.label"
                :on-click="onRoomSelected"
                class="text-bold"
                :style="{ fontSize: '16px' }"
              >
                <q-badge class="q-ml-sm" color="green" rounded />
              </q-btn>
            </div>
          </template>
        </q-tree>
      </q-card>

      <!-- 调音台部分 -->
      <q-card class="q-pa-md q-gutter-md">
        <q-btn label="调音台" @click="showAudioControlDialog" :icon="tune" />
        <q-btn
          label="麦克风"
          :color="micOn ? 'positive' : 'negative'"
          @click="micOn = !micOn"
        />
        <q-btn
          label="扬声器"
          :color="speakerOn ? 'positive' : 'negative'"
          :icon="settings_voice"
          @click="speakerOn = !speakerOn"
        />
      </q-card>
    </div>
    <q-dialog v-model="audioControlDialogVisible" persistent>
      <q-card>
        <q-card-section>
          <div class="q-gutter-md">
            <div class="q-pa-md">音量</div>
            <q-slider v-model="volume" />
          </div>
        </q-card-section>
        <q-card-actions align="right">
          <q-btn label="取消" @click="audioControlDialogVisible = false" />
          <q-btn
            label="确定"
            color="primary"
            @click="audioControlDialogVisible = false"
          />
        </q-card-actions>
      </q-card>
    </q-dialog>

    <!-- 设备管理 -->
    <div class="column">
                <q-btn-dropdown color="primary" label="使用的麦克风设备">
                  <q-list>
                    <q-item clickable v-close-popup @click="onItemClick">
                      <q-item-section>
                        <q-item-label>Microphone 1</q-item-label>
                      </q-item-section>
                    </q-item>

                    <q-item clickable v-close-popup @click="onItemClick">
                      <q-item-section>
                        <q-item-label>Microphone 2</q-item-label>
                      </q-item-section>
                    </q-item>

                  </q-list>
                </q-btn-dropdown>

                <q-btn-dropdown color="primary" label="使用的扬声器设备">
                  <q-list>
                    <q-item clickable v-close-popup @click="onItemClick">
                      <q-item-section>
                        <q-item-label>Speaker 1</q-item-label>
                      </q-item-section>
                    </q-item>

                    <q-item clickable v-close-popup @click="onItemClick">
                      <q-item-section>
                        <q-item-label>Speaker 1</q-item-label>
                      </q-item-section>
                    </q-item>

                  </q-list>
                </q-btn-dropdown>

                <q-btn label="麦克风测试"></q-btn>
              </div>
  </q-page>
</template>

<script>
import { ref } from "vue";

export default {
  data() {
    return {
      userAvatarUrl:
        "https://www.gravatar.com/avatar/205e460b479e2e5b48aec07710c08d50",
      userName: "John Doe",
      selectedRoom: null,
      audioControlDialogVisible: false,
      volume: 50,
      micOn: true,
      speakerOn: true,

      expanded: ref(["刷刷刷", "坐牢"]),

      customize: ref([
        {
          label: "刷刷刷",
          header: "root",
          children: [
            {
              label: "超哥哥",
              header: "generic",
            },
            {
              label: "马楼",
              header: "generic",
            },
          ],
        },
        {
          label: "打抢",
          header: "root",
          children: [
            {
              label: "超哥哥",
              header: "generic",
            },
            {
              label: "马楼",
              header: "generic",
            },
            {
              label: "甘霖",
              header: "generic",
            },
          ],
        },
        {
          label: "坐牢",
          header: "root",
          children: [
            {
              label: "超哥哥",
              header: "generic",
            },
            {
              label: "马楼",
              header: "generic",
            },
            {
              label: "甘霖",
              header: "generic",
            },
          ],
        },
      ]),
    };
  },
  methods: {
    onRoomSelected(node) {
      if (node.leaf) {
        console.log(`User ${node.label} selected in room ${node.parent.label}`);
      }
    },
    showAudioControlDialog() {
      this.audioControlDialogVisible = true;
    },
  },
};
</script>

<style scoped>
.q-card {
  border: 1px solid #ccc;
  border-radius: 4px;
}
</style>
