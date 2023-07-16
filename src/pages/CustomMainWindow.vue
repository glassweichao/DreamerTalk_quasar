<template>
  <q-layout view="hHh lpR fFf">
    <!-- 头部-头像、ID、网络状态等 -->
    <q-header class="transparent text-white q-pa-md">
      <q-chip outline>
        <q-avatar color="primary"> C </q-avatar>
        Charles Wei
      </q-chip>
    </q-header>

    <!-- 调音台 -->
    <q-drawer v-model="leftDrawerOpen" side="left" overlay bordered>
      <!-- drawer content -->
      <div class="row justify-end">
        <div class="row-1 justify-end">
          <q-btn label="x" text-color="red" flat="" round @click="leftDrawerOpen = false" />
        </div>
        <div class="fit">
          <!-- 调音台 -->
          <q-item tag="label" v-ripple>
            <q-item-section side top>
              <q-checkbox v-model="check1" />
            </q-item-section>

            <q-item-section>
              <q-item-label>麦克风增强</q-item-label>
            </q-item-section>
          </q-item>

          <q-item tag="label" v-ripple>
            <q-item-section side top>
              <q-checkbox v-model="check2" />
            </q-item-section>

            <q-item-section>
              <q-item-label>变声</q-item-label>
            </q-item-section>
          </q-item>

          <q-item>
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

          <q-item>
            <q-item-section side>
              <q-icon color="primary" name="mic" />
            </q-item-section>
            <q-item-section>
              <q-slider v-model="mic" :min="0" :max="100" label />
            </q-item-section>
          </q-item>
        </div>
      </div>
    </q-drawer>

    <q-page-container>
      <div class="q-pa-md">
        <q-btn-dropdown
          class="full-width"
          color="primary"
          label="Room List"
          rounded
          size="18px"
          unelevated
          @show="refleshRoomList"
        >
          <q-list>
            <q-item clickable v-close-popup @click="onItemClick">
              <q-item-section>
                <q-item-label>Photos</q-item-label>
              </q-item-section>
            </q-item>

            <q-item clickable v-close-popup @click="onItemClick">
              <q-item-section>
                <q-item-label>Videos</q-item-label>
              </q-item-section>
            </q-item>

            <q-item clickable v-close-popup @click="onItemClick">
              <q-item-section>
                <q-item-label>Articles</q-item-label>
              </q-item-section>
            </q-item>
          </q-list>
        </q-btn-dropdown>
      </div>

      <div class="q-pa-md">
        <q-list flat bordered>
          <q-item clickable v-ripple>
            <q-item-section avatar>
              <q-avatar color="primary" text-color="white"> R </q-avatar>
            </q-item-section>

            <q-item-section> 一剑宛春秋 </q-item-section>

            <q-item-section side>
              <q-badge rounded color="green" />
            </q-item-section>
          </q-item>

          <q-item clickable v-ripple>
            <q-item-section avatar>
              <q-avatar color="primary" text-color="white"> R </q-avatar>
            </q-item-section>

            <q-item-section> 一剑宛春秋 </q-item-section>

            <q-item-section side>
              <q-badge rounded color="green" />
            </q-item-section>
          </q-item>

          <q-item clickable v-ripple>
            <q-item-section avatar>
              <q-avatar color="primary" text-color="white"> R </q-avatar>
            </q-item-section>

            <q-item-section> 一剑宛春秋 </q-item-section>

            <q-item-section side>
              <q-badge rounded color="green" />
            </q-item-section>
          </q-item>

          <q-item clickable v-ripple>
            <q-item-section avatar>
              <q-avatar color="primary" text-color="white"> R </q-avatar>
            </q-item-section>

            <q-item-section> 一剑宛春秋 </q-item-section>

            <q-item-section side>
              <q-badge rounded color="green" />
            </q-item-section>
          </q-item>

          <q-item clickable v-ripple>
            <q-item-section avatar>
              <q-avatar color="primary" text-color="white"> R </q-avatar>
            </q-item-section>

            <q-item-section> 一剑宛春秋 </q-item-section>

            <q-item-section side>
              <q-badge rounded color="green" />
            </q-item-section>
          </q-item>
        </q-list>
      </div>
    </q-page-container>

    <q-footer class="transparent text-white">
      <div class="row justify-center items-center q-pa-md">
        <div class="col-4 text-center">
          <q-btn
            round
            color="primary"
            icon="equalizer"
            @click="leftDrawerOpen = !leftDrawerOpen"
          />
          <!-- <q-btn-dropdown
            persistent
            rounded
            color="deep-orange"
            dropdown-icon="equalizer"
            no-icon-animation
          >
          </q-btn-dropdown> -->
        </div>
        <div class="col-4 text-center">
          <q-btn
            round
            color="deep-orange"
            :icon="micOn ? 'mic' : 'mic_off'"
            @click="micOn = !micOn"
          />
        </div>
        <div class="col-4 text-center">
          <q-btn
            round
            color="deep-orange"
            :icon="speakerOn ? 'volume_up' : 'volume_off'"
            @click="speakerOn = !speakerOn"
          />
        </div>
      </div>
    </q-footer>
  </q-layout>
</template>

<script>
import { ref } from "vue";

export default {
  data() {
    return {
      micOn: true,
      speakerOn: true,
    };
  },

  setup() {
    const leftDrawerOpen = ref(false);
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
    };
  },
};
</script>
