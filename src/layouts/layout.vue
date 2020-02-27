<template>
  <q-layout view="hHh lpR fFf">
    <q-header elevated>
      <q-toolbar>
        <q-toolbar-title class="absolute-center">
          TODO App
        </q-toolbar-title>
        <div> 
          <q-btn
          flat
          dense
          round
          @click="leftDrawerOpen = !leftDrawerOpen"
          icon="menu"
          aria-label="Menu"
        /></div>
      </q-toolbar>
    </q-header>
  
      <q-footer elevated>
      <q-tabs>
        <q-route-tab 
        to="/"
        icon="list" 
        label="Todo"
        />
        <q-route-tab 
        to="/settings"
        icon="settings" 
        label="Settings"
        />
      </q-tabs>
      </q-footer>

    <q-drawer
      v-model="leftDrawerOpen"
      :breakpoint="767"
      :width="250"
      show-if-above
      bordered
      content-class="bg-primary"
    >
      <q-list dark>
        <q-item-label header>Navigation</q-item-label>
        <EssentialLink
          v-for="link in essentialLinks"
          :key="link.title"
          v-bind="link"
        />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import EssentialLink from 'components/EssentialLink'

export default {
  name: 'MainLayout',

  components: {
    EssentialLink
  },

  data () {
    return {
      leftDrawerOpen: false,
      essentialLinks: [
        {
          title: 'TODO',
          icon: 'list',
          link: ''
        },
        {
          title: 'Settings',
          icon: 'settings',
          link: '#/settings'
        }
      ]
    }
  }
}
</script>
<style lang="scss">
@media screen and (min-width: 768px) {
.q-footer {
  display: none;
}
}
</style>
