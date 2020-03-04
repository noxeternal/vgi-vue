<template>
  <div>
    <v-navigation-drawer :clipped="clipped" v-model="drawer" fixed app>
      <v-list v-if="data" v-for="(item, i) in data" :key="i">
        <label v-text="item.text" class="font-weight-bold"></label>
        <v-list-tile v-for="(item, i) in item.items" :to="item.to" :key="i" router exact>
          <v-list-tile-action>
            <v-icon v-html="item.icon" />
          </v-list-tile-action>
          <v-list-tile-content>
            <!-- <v-checkbox :label="item.title" :value="item.title" /> -->
            <label class="inline">
              <input type="checkbox">
              <v-list-tile-title v-text="item.title" />
              <span style="float:right" v-if="item.count" v-text="'('+item.count+')'" />
            </label>
          </v-list-tile-content>
        </v-list-tile>
      </v-list>
    </v-navigation-drawer>
    <v-toolbar :clipped-left="clipped" fixed app>
      <v-toolbar-side-icon @click="drawer = !drawer" />
      <v-toolbar-title v-text="title"/>
    </v-toolbar> 
  </div>
</template>

<style>
  .inline {
    display: inline-block;
    width: 100%;
  }
  .v-list__tile {
    height: 24px;
    font-weight: normal !important;
  }
  .v-list__tile__title {  
    display: inline;
    width: 100%;
  }
  .v-input__control {
    height: 24px;
  }
</style>

<script>
  export default {
    // async asyncData ({$axios}) {
    //   console.log('getting')
    //   const { data } = await $axios.$get('https://noxeternal.net/server/enumData.php')
    //   console.log('got')
    //   return { data }
    // },
    data () {
      return {
        clipped: false,
        drawer: true,
        fixed: false,
        data: []
      }
    },
    async mounted () {
      const { data } = await this.$axios.$get('https://noxeternal.net/server/enumData.php')
      this.data = data
    }
  }
/* [
          { 
            title: "Console",
            items: [
              {
                  id: 1,
                  title: "NES",
                  link: "nes",
                  count: "9",
                  order: 1
              },
              {
                  id: 2,
                  title: "SNES",
                  link: "super-nintendo",
                  count: "9",
                  order: 2
              },
              {
                  id: 3,
                  title: "N64",
                  link: "nintendo-64",
                  count: "7",
                  order: 3
              },
              {
                  id: 4,
                  title: "Gamecube",
                  link: "gamecube",
                  count: "32",
                  order: 4
              },
              {
                  id: 5,
                  title: "Wii",
                  link: "wii",
                  count: "30",
                  order: 5
              },
              {
                  id: 6,
                  title: "Wii U",
                  link: "wii-u",
                  count: "15",
                  order: 6
              },
              {
                  id: 28,
                  title: "Switch",
                  link: "nintendo-switch",
                  count: "11",
                  order: 7
              },
              {
                  id: 7,
                  title: "Gameboy",
                  link: "gameboy",
                  count: "2",
                  order: 8
              },
              {
                  id: 19,
                  title: "Gameboy Color",
                  link: "gameboy-color",
                  count: "3",
                  order: 9
              },
              {
                  id: 20,
                  title: "Gameboy Advance",
                  link: "gameboy-advance",
                  count: "17",
                  order: 10
              },
              {
                  id: 8,
                  title: "DS",
                  link: "nintendo-ds",
                  count: "18",
                  order: 11
              },
              {
                  id: 21,
                  title: "3DS",
                  link: "nintendo-3ds",
                  count: "25",
                  order: 12
              },
              {
                  id: 11,
                  title: "Playstation",
                  link: "playstation",
                  count: "16",
                  order: 13
              },
              {
                  id: 12,
                  title: "Playstation 2",
                  link: "playstation-2",
                  count: "17",
                  order: 14
              },
              {
                  id: 13,
                  title: "Playstation 3",
                  link: "playstation-3",
                  count: "32",
                  order: 15
              },
              {
                  id: 24,
                  title: "Playstation 4",
                  link: "playstation-4",
                  count: "18",
                  order: 16
              },
              {
                  id: 22,
                  title: "PSOne Classic",
                  link: "",
                  count: "19",
                  order: 17
              },
              {
                  id: 29,
                  title: "PS2 Classic",
                  link: "",
                  count: "2",
                  order: 18
              },
              {
                  id: 14,
                  title: "PSP",
                  link: "psp",
                  count: "10",
                  order: 19
              },
              {
                  id: 15,
                  title: "Playstation Vita",
                  link: "playstation-vita",
                  count: "6",
                  order: 20
              },
              {
                  id: 16,
                  title: "XBox",
                  link: "xbox",
                  count: "14",
                  order: 21
              },
              {
                  id: 17,
                  title: "XBox 360",
                  link: "xbox-360",
                  count: "22",
                  order: 22
              }
            ]
          },
          {
            title: "Condition",
            items: [
              {title: "Used"},
              {title: "Complete"},
              {title: "New"},
              {title: "Digital"}
            ]
          },
          {
            title: "Category",
            items: [
              {title: "Game"},
              {title: "Guide"},
              {title: "Accessory"},
              {title: "Console"}
            ]
          }
        ] */</script>
