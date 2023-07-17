<template>
  <q-layout view="hHh lpR fFf">
    <!-- 头部-头像、ID、网络状态等 -->
    <q-header class="transparent text-white q-pa-md">
      <q-chip outline>
        <q-avatar color="primary"> C </q-avatar>
        Charles Wei
      </q-chip>
    </q-header>

    <q-footer class="transparent text-white">
      <!-- 调音台 -->
      <div class="row justify-center items-center q-pa-md">
        <div class="col-4 text-center relative-position">
          <q-btn
            v-morph:btn_equalizer:mygroup:300.resize="morphGroupModel"
            round
            color="primary"
            icon="equalizer"
            @click="nextMorph"
          />

          <q-card
            v-morph:card_audio_manage:mygroup:500.resize="morphGroupModel"
            class="absolute-bottom-left q-ma-lg text-blue text-left"
            style="width: 300px"
          >
            <!-- 调音台 -->
            <q-card-section>
              <q-checkbox
                class="text-primary"
                label="声音增强"
                v-model="check1"
              />
              <q-checkbox
                class="text-primary"
                label="降噪增强"
                v-model="check2"
              />
              <q-checkbox
                class="text-primary"
                label="回声消除增强"
                v-model="check3"
              />
            </q-card-section>

            <q-item class="q-ma-sm">
              <q-item-section side>
                <q-icon color="teal" name="volume_down" />
              </q-item-section>
              <q-item-section>
                <q-slider
                  v-model="volume"
                  :min="0"
                  :max="100"
                  label
                  color="teal"
                />
              </q-item-section>
            </q-item>

            <q-item class="q-ma-sm">
              <q-item-section side>
                <q-icon color="primary" name="mic" />
              </q-item-section>
              <q-item-section>
                <q-slider v-model="mic" :min="0" :max="100" label />
              </q-item-section>
            </q-item>

            <q-card-actions align="right">
              <q-btn flat label="试麦" @click="nextMorph" />
              <q-btn flat label="关闭" @click="cancelMorph" />
            </q-card-actions>
          </q-card>

          <q-card
            v-morph:card_dev_manage:mygroup:500.tween="morphGroupModel"
            class="absolute-bottom-left q-ma-lg text-primary"
            style="width: 300px"
          >
            <q-card-section>
              <q-btn-dropdown
                color="pink"
                label="Dropdown Button"
                icon="mic"
                dropdown-icon="mic"
              >
                <q-list>
                  <q-item clickable v-close-popup @click="onItemClick">
                    <q-item-section>
                      <q-item-label>麦克风设备</q-item-label>
                    </q-item-section>
                  </q-item>
                </q-list>
              </q-btn-dropdown>
            </q-card-section>

            <q-card-section>
              <q-btn-dropdown
                color="pink"
                label="Dropdown Button"
                icon="volume_up"
                dropdown-icon="volume_up"
              >
                <q-list>
                  <q-item clickable v-close-popup @click="onItemClick">
                    <q-item-section>
                      <q-item-label>扬声器设备</q-item-label>
                    </q-item-section>
                  </q-item>
                </q-list>
              </q-btn-dropdown>
            </q-card-section>

            <q-card-section>
              <div class="row items-center q-ma-md">
                <div class="col-4">
                  <q-btn label="开始试麦" size="sm" />
                </div>
                <div class="col-8">
                  <q-linear-progress
                    rounded
                    size="15px"
                    :value="0.5"
                    color="teal"
                  />
                </div>
              </div>
            </q-card-section>

            <q-card-actions align="right">
              <q-btn flat label="关闭" @click="cancelMorph" />
            </q-card-actions>
          </q-card>
        </div>

        <div class="col-4 text-center">
          <q-btn
            round
            color="primary"
            :icon="micOn ? 'mic' : 'mic_off'"
            @click="micOn = !micOn"
          />
        </div>
        <div class="col-4 text-center">
          <q-btn
            round
            color="teal"
            :icon="speakerOn ? 'volume_up' : 'volume_off'"
            @click="speakerOn = !speakerOn"
          />
        </div>
      </div>
    </q-footer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import { defineComponent, ref } from "vue";

const audioManageStep = {
  btn_equalizer: "card_audio_manage",
  card_audio_manage: "card_dev_manage",
};

export default defineComponent({
  name: "MainLayout",

  data() {
    return {
      micOn: true,
      speakerOn: true,
    };
  },

  setup() {
    const leftDrawerOpen = ref(false);
    const morphGroupModel = ref("btn_equalizer");
    return {
      leftDrawerOpen,
      toggleLeftDrawer() {
        leftDrawerOpen.value = !leftDrawerOpen.value;
      },
      check1: ref(true),
      check2: ref(false),
      check3: ref(false),

      volume: ref(80),
      mic: ref(80),

      morphGroupModel,
      nextMorph() {
        morphGroupModel.value = audioManageStep[morphGroupModel.value];
      },
      cancelMorph() {
        morphGroupModel.value = "btn_equalizer";
      },
    };
  },
});
</script>
