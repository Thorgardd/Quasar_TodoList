<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn flat dense round icon="menu" aria-label="Menu" @click="toggleLeftDrawer"/>
        <q-toolbar-title>
          Todo List
        </q-toolbar-title>
      </q-toolbar>
    </q-header>

    <q-drawer :breakpoint="767" v-model="leftDrawerOpen" show-if-above bordered>
      <q-list>
        <q-item-label header>
          Liens Essentiels
        </q-item-label>

        <q-item v-for="link in links" clickable :to="link.route" exact>
          <q-item-section avatar>
            <q-icon :name="link.icon"/>
          </q-item-section>
          <q-item-section>
            <q-item-label>
              {{ link.label }}
            </q-item-label>
          </q-item-section>
        </q-item>

      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>

    <q-footer elevated>
      <q-tabs>
        <q-route-tab v-for="link in links"
                     :key="link.id"
                     :to="link.route"
                     :icon="link.icon"
                     :label="link.label"
                     exact/>
      </q-tabs>
    </q-footer>
  </q-layout>
</template>

<script>
export default {
  name: 'MainLayout',
  data () {
    return {
      leftDrawerOpen: false,
      links: [
        {
          id: 0,
          label: "Tâches",
          icon: "list",
          route: "/"
        },
        {
          id: 1,
          label: "Paramètres",
          icon: "settings",
          route: "/params"
        }
      ]
    }
  },
  methods: {
    toggleLeftDrawer () {
      this.leftDrawerOpen = !this.leftDrawerOpen
    }
  }
}
</script>

<style>
@media screen and (min-width: 768px) {
  .q-footer {
    display: none;
  }
}

@media screen and (max-width: 767px ) {
  .q-drawer{
    display: none;
  }
  .q-btn{
    display: none;
  }
}
</style>
