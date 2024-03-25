<template>
  <q-layout view="hHh lpR fFf" class="bg-white">
    <!-- header -->
    <q-header unelevated class="bg-white text-black q-py-xs" height-hint="58">
      <q-toolbar>
        <q-btn flat dense round @click="toggleLeftDrawer" v-if="$q.screen.gt.xs" aria-label="Menu" icon="menu" />
        <q-btn v-else flat dense round @click="toggleDrawer" aria-label="Menu" icon="menu" />
        <q-btn flat no-caps no-wrap class="logo">
          <q-icon :name="fabYoutube" color="red" size="28px" />
          <q-toolbar-title shrink class="text-weight-bold">
            YouTube
          </q-toolbar-title>
        </q-btn>
        <q-space />
        <div class="YL__toolbar-input-container row no-wrap ">
          <q-input dense outlined rounded v-model="search" placeholder="Search" class="bg-white col ">
            <template v-slot:append>
              <q-icon v-if="search === ''" name="keyboard" />
              <q-icon v-else name="clear" class="cursor-pointer" @click="search = ''" />
              <q-btn unelevated outlined rounded color="grey-3" class="search-btn" text-color="black" icon="search">
              </q-btn>
            </template>
          </q-input>

        </div>
        <div class="micro-icon">
          <q-btn unelevated color="white" text-color="black" icon="micro"></q-btn>
        </div>
        <q-space />
        <div class="q-gutter-sm row items-center no-wrap" v-if="$q.screen.gt.xs">

          <q-btn round flat icon="more_vert">
            <q-menu auto-close :offset="[110, 0]">
              <q-list style="min-width: 150px">
                <q-item clickable>
                  <q-item-section>Contact data</q-item-section>
                </q-item>
                <q-item clickable>
                  <q-item-section>Block</q-item-section>
                </q-item>
                <q-item clickable>
                  <q-item-section>Select messages</q-item-section>
                </q-item>
                <q-item clickable>
                  <q-item-section>Silence</q-item-section>
                </q-item>
                <q-item clickable>
                  <q-item-section>Clear messages</q-item-section>
                </q-item>
                <q-item clickable>
                  <q-item-section>Erase messages</q-item-section>
                </q-item>
              </q-list>
            </q-menu>
          </q-btn>
          <q-btn outline rounded color="primary" class="q-py-sm">
            <q-btn unelevated round color="primary" size="8px" text-color="white" icon="person" class="q-p" />
            <div class="profile">profile</div>
          </q-btn>
          <q-icon size="20px"><img src="/icons/drop.png" alt="Drop Image" class="drop-icon"></q-icon>

        </div>
        <div v-else>
          <q-btn round flat icon="more_vert">
            <q-menu auto-close :offset="[110, 0]">
              <q-list style="min-width: 150px">
                <q-item clickable>
                  <q-item-section>Contact data</q-item-section>
                </q-item>
                <q-item clickable>
                  <q-item-section>Block</q-item-section>
                </q-item>
                <q-item clickable>
                  <q-item-section>Select messages</q-item-section>
                </q-item>
                <q-item clickable>
                  <q-item-section>Silence</q-item-section>
                </q-item>
                <q-item clickable>
                  <q-item-section>Clear messages</q-item-section>
                </q-item>
                <q-item clickable>
                  <q-item-section>Erase messages</q-item-section>
                </q-item>
              </q-list>
            </q-menu>
          </q-btn>
        </div>

      </q-toolbar>
    </q-header>
    <!-- menu  drawer-->
    <q-drawer v-model="leftDrawerOpen" show-if-above class="bg-white" :width="defautDrawerOpen ? 100 : 200">
      <q-scroll-area class="fit">
        <q-list padding>
          <q-item :class="defautDrawerOpen ? 'q_item' : ''" v-for="link in links1" :key="link.text" v-ripple clickable>
            <q-item-section avatar>
              <q-icon color="black" :name="link.icon" />
            </q-item-section>
            <q-item-section>
              <q-item-label color="black">{{ link.text }}</q-item-label>
            </q-item-section>
          </q-item>
          <q-item :class="defautDrawerOpen ? 'q_item' : ''" v-for="link in links2" :key="link.text" v-ripple clickable>
            <q-item-section avatar>
              <q-icon color="black" :name="link.icon" />
            </q-item-section>
            <q-item-section>
              <q-item-label color="black">{{ link.text }}</q-item-label>
            </q-item-section>
          </q-item>
        </q-list>
      </q-scroll-area>
    </q-drawer>
    <!-- page content -->
    <q-page-container>
      <div class="bg-white ">
        <IndexPage />
      </div>
    </q-page-container>
  </q-layout>
</template>

<script>
import { ref } from 'vue'
import IndexPage from '../pages/IndexPage.vue';
import { fabYoutube } from '@quasar/extras/fontawesome-v6'




export default {
  name: 'MyLayout',
  components: {
    IndexPage,
  },

  setup() {
    // Define ref variables for state
    const leftDrawerOpen = ref(false)
    const defautDrawerOpen = ref(false)
    const search = ref('')


    function toggleLeftDrawer() {
      defautDrawerOpen.value = !defautDrawerOpen.value
     
    }
    function toggleDrawer() {
      leftDrawerOpen.value = !leftDrawerOpen.value
    }
    return {
      fabYoutube,


      leftDrawerOpen,
      defautDrawerOpen,
      search,

      toggleLeftDrawer,
      toggleDrawer,

      links1: [
        { icon: 'home', text: 'Home' },
        { icon: 'whatshot', text: 'Trending' },
        { icon: 'subscriptions', text: 'Subscriptions' }
      ],
      links2: [
        { icon: 'folder', text: 'Library' },
        { icon: 'restore', text: 'History' },
        { icon: 'watch_later', text: 'Watch later' },
        { icon: 'thumb_up_alt', text: 'Liked videos' }
      ],
      links3: [
        { icon: fabYoutube, text: 'YouTube Premium' },
        { icon: 'local_movies', text: 'Movies & Shows' },
        { icon: 'videogame_asset', text: 'Gaming' },
        { icon: 'live_tv', text: 'Live' }
      ],
      links4: [
        { icon: 'settings', text: 'Settings' },
        { icon: 'flag', text: 'Report history' },
        { icon: 'help', text: 'Help' },
        { icon: 'feedback', text: 'Send feedback' }
      ],
      buttons1: [
        { text: 'About' },
        { text: 'Press' },
        { text: 'Copyright' },
        { text: 'Contact us' },
        { text: 'Creators' },
        { text: 'Advertise' },
        { text: 'Developers' }
      ],

    }
  }
}
</script>

<style >
/* Assuming you want to reset border-radius and padding for all q-input components */
.q-field--outlined .q-field__control {
  border-radius: 0;
  /* Reset border-radius */
  padding: 0px 1px 0px 10px;
  /* Reset padding */
}

.YL__toolbar-input-container {
  min-width: 100px;
  width: 55%
}

.micro-icon {
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 0px 30px;
}

.profile {
  padding: 0px 0px 0px 10px;
}

.q_item {
  display: flex;
  flex-direction: column;

}

.cutom-dots {
  font-weight: bolder;
  color: black;
  font-size: 25px;
}

.drop-icon {
  object-fit: cover;
  width: 30px;
  height: 30px;
  border-radius: 10px;
  cursor: pointer;
}

.q-btn__content {
  display: flex;
  flex-wrap: unset;
}

@media (max-width: 600px) {

  .q-btn .q-icon,
  .q-btn .q-spinner {
    font-size: 16px;
  }

  .q-btn--round {
    border-radius: 50%;
    padding: 0;
    min-width: unset;
  }

  .micro-icon {
    margin: 0px 0px;
  }

  .q-btn {
    padding: 0px;
  }

  .logo {
    padding: 0px;
  }

  .q-icon,
  .material-icons {
    justify-content: unset;
  }

  .search-btn {
    padding: 0px 15px;
  }

  .q-toolbar__title {
    font-size: 12px;
    padding: 0 2px;

  }
}</style>