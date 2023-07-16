<template>
  <q-layout view="hHh lpR fFf">

    <!--自定义操作栏-->
    <q-header elevated class="bg-primary text-white">
      <q-bar class="q-electron-drag">
          <q-space />
          <q-btn dense flat icon="minimize" />
          <q-btn dense flat icon="crop_square" />
          <q-btn dense flat icon="close" />
      </q-bar>
      <q-toolbar>
        <q-toolbar-title>
          <q-avatar>
            <img src="https://cdn.quasar.dev/logo-v2/svg/logo-mono-white.svg">
          </q-avatar>
          DreamerTalk
        </q-toolbar-title>
      </q-toolbar>
    </q-header>

    <!--用户头像栏-->

    <q-page-container>
      <div class="q-pa-md row justify-center">
        <div style="width: 80%; max-width: 400px">
          <q-chat-message
            label="Sunday, 19th"
          />

          <q-chat-message
            name="me"
            avatar="https://cdn.quasar.dev/img/avatar4.jpg"
            :text="['hey, how are you?']"
            sent
            stamp="7 minutes ago"
          />
          <q-chat-message
            name="Jane"
            avatar="https://cdn.quasar.dev/img/avatar3.jpg"
            :text="['doing fine, how r you?']"
            stamp="4 minutes ago"
          />
        </div>
      </div>
    </q-page-container>

  </q-layout>
</template>

<script>
export default {
  setup () {
    // we rely upon
    function minimize () {
      if (process.env.MODE === 'electron') {
        window.myWindowAPI.minimize()
      }
    }

    function toggleMaximize () {
      if (process.env.MODE === 'electron') {
        window.myWindowAPI.toggleMaximize()
      }
    }

    function closeApp () {
      if (process.env.MODE === 'electron') {
        window.myWindowAPI.close()
      }
    }

    return { minimize, toggleMaximize, closeApp }
  }
}
</script>
