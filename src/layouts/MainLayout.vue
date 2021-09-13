<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          color="dark"
          @click="leftDrawerOpen = !leftDrawerOpen"
        />
      </q-toolbar>
      <div class="q-px-lg q-pt-l q-mb-md">
        <div style="color: #000">
          <div style="font-size: 25px" class="txt-h">Purchase List</div>
          <div class="text-subtitle1">{{ TodaysDate }}</div>
        </div>
      </div>

      <q-img
        src="../statics/header1-bg.jpg"
        style="height: 131px"
        class="header-image absolute-top"
      />
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      :width="250"
      :breakpoint="600"
    >
      <q-scroll-area
        style="
          height: calc(100% - 131px);
          margin-top: 131px;
          border-right: 1px solid #ddd;
        "
      >
        <q-list padding>
          <q-item to="/" exact clickable v-ripple>
            <q-item-section avatar>
              <q-icon name="shopping_bag" />
            </q-item-section>

            <q-item-section> Purchase List </q-item-section>
          </q-item>

          <q-item to="/product" exact clickable v-ripple>
            <q-item-section avatar>
              <q-icon name="shopping_cart" />
            </q-item-section>

            <q-item-section> Product </q-item-section>
          </q-item>

          <q-item to="/help" exact clickable v-ripple>
            <q-item-section avatar>
              <q-icon name="help" />
            </q-item-section>

            <q-item-section> Description </q-item-section>
          </q-item>
        </q-list>
      </q-scroll-area>

      <q-img
        class="absolute-top"
        src="../statics/user-bg.jpg"
        style="height: 131px;"
      >
        <div class="absolute-bottom bg-transparent">
          <q-avatar size="56px" class="q-mb-sm">
            <img src="https://cdn.quasar.dev/img/boy-avatar.png" />
          </q-avatar>
          <div style="color:#1D1D1D" class="text-weight-bold">AJ B.</div>
          <div style="color:#1D1D1D">@IPteam</div>
        </div>
      </q-img>
    </q-drawer>

    <q-page-container>
      <router-view v-slot="{ Component }">
        <keep-alive>
          <component :is="Component" />
        </keep-alive>
      </router-view>
    </q-page-container>
  </q-layout>
</template>

<script>
import { defineComponent, ref } from "vue";
import { date } from "quasar";

export default defineComponent({
  name: "MainLayout",
  data() {
    return {
      leftDrawerOpen: false,
    };
  },

  components: {
    // EssentialLink,
  },

  setup() {
    return {
      drawer: ref(false),
    };
  },

  computed: {
    TodaysDate() {
      const timeStamp = Date.now();
      return date.formatDate(timeStamp, "dddd D MMMM YYYY");
    },
  },
});
</script>

<style lang="scss">
.header-image {
  height: 100%;
  z-index: -1;
  // opacity: 0.7;
  // filter: grayscale(10%);
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
}
.q-scrollarea__content {
  background-color: #fffcfa;
}
</style>
