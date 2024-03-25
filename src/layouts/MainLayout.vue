<template>
  <q-layout view="hHh lpR fFf" class="bg-white">
    <q-header unelevated class="bg-white text-black q-py-xs" height-hint="58">
      <q-toolbar>
        <q-btn flat dense round @click="toggleLeftDrawer" aria-label="Menu" icon="menu" />

        <q-btn flat no-caps no-wrap class="" v-if="$q.screen.gt.xs">
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
              <q-btn unelevated outlined rounded color="grey-3" text-color="black" icon="search">
              </q-btn>
            </template>
          </q-input>


        </div>



        <div class="micro-icon">
          <q-btn unelevated color="white" text-color="black" icon="micro"></q-btn>
        </div>

        <q-space />

        <div class="q-gutter-sm row items-center no-wrap">


          <q-btn unelevated round color="primary" size="8px" text-color="white" icon="person" />
          <q-btn outline rounded color="primary" class="q-py-sm">
            <q-btn unelevated round color="primary" size="8px" text-color="white" icon="person" class="q-p" />
            <div class="profile">profile</div>
          </q-btn>
          <q-btn unelevated round color="primary" text-color="white" size="8px" icon="person" />
        </div>
      </q-toolbar>
    </q-header>

     <q-drawer v-model="leftDrawerOpen"   class="bg-white" :width="200">
      <q-scroll-area class="fit">
        <q-list padding>
          <q-item v-for="link in links1" :key="link.text" v-ripple clickable>
            <q-item-section avatar>
              <q-icon color="grey" :name="link.icon" />
            </q-item-section>
            <q-item-section  >
              <q-item-label>{{ link.text }}</q-item-label>
            </q-item-section>
          </q-item>
          <q-item v-for="link in links2" :key="link.text" v-ripple clickable>
            <q-item-section avatar>
              <q-icon color="grey" :name="link.icon" />
            </q-item-section>
            <q-item-section >
              <q-item-label>{{ link.text }}</q-item-label>
            </q-item-section>
          </q-item>
        </q-list>
      </q-scroll-area>
    </q-drawer>  

    <!-- <q-drawer v-model="defautDrawerOpen"   class="bg-white" :width="200">
        <q-scroll-area class="fit">
          <q-list padding>
            <q-item v-for="link in links1" :key="link.text" v-ripple clickable>
              <q-item-section avatar>
                <q-icon color="grey" :name="link.icon" />
              </q-item-section>
              <q-item-section  >
                <q-item-label>{{ link.text }}</q-item-label>
              </q-item-section>
            </q-item>
            <q-item v-for="link in links2" :key="link.text" v-ripple clickable>
              <q-item-section avatar>
                <q-icon color="grey" :name="link.icon" />
              </q-item-section>
              <q-item-section >
                <q-item-label>{{ link.text }}</q-item-label>
              </q-item-section>
            </q-item>
          </q-list>
        </q-scroll-area>
      </q-drawer>   -->



    <q-page-container >
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
// import { faRaindrop } from '@quasar/extras/fontawesome-v6'



export default {
  name: 'MyLayout',
  components: {
    IndexPage,
  },

  setup() {
    // Define ref variables for state
    const leftDrawerOpen = ref(true) // Initially set to false
    const defautDrawerOpen = ref(false) // Initially set to false
    const search = ref('')

    function toggleLeftDrawer() {
      // defautDrawerOpen.value = !defautDrawerOpen.value
      leftDrawerOpen.value = !leftDrawerOpen.value
    }

    return {
      fabYoutube,


      leftDrawerOpen,
      defautDrawerOpen,
      search,

      toggleLeftDrawer,

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
      buttons2: [
        { text: 'Terms' },
        { text: 'Privacy' },
        { text: 'Policy & Safety' },
        { text: 'Test new features' }
      ]
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
      </style>