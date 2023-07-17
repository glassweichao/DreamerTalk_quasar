<template>
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
</template>

<script>
import { ref } from "vue";

export default {
  data() {
    return {};
  },

  setup() {
    return {};
  },
};
</script>
