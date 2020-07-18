<template>
  <div id="app">
      <div id="hover">
          <div id="buttons">
              <button v-on:click="click(menu[1])" v-for="menu in menus" :key="menu[1]" :src="menu[1]" :class="{ selected: menu[1] == select}">{{ menu[0] }}</button>
          </div>
      </div>
      <iframe :src="select"></iframe>
<!--      <iframe src="https://sonarr.slnk.icu"></iframe>-->
<!--      <iframe src="https://jellyfin.slnk.icu"></iframe>-->
  </div>
</template>

<script>

export default {
  name: 'App',
    data() {
        return {
            select: 'https://sonarr.slnk.icu',
            menus: [['Radarr', 'https://radarr.slnk.icu'],
                    ['Sonarr', 'https://sonarr.slnk.icu'],
                    ['Transmission', 'https://transmission.slnk.icu'],
                    ['Jellyfin', 'https://jellyfin.slnk.icu'],
            ]
        }
    }   ,
    methods: {
    click: function (url) {
        this.select = url;
    }
  }
}
</script>

<style>
body {
    margin: 0;
    padding: 0;
}
#buttons{
    height: 100vh;
    width: 200px;
    background-color: #42b983;
    z-index: 2;
    background-color: rgba(30,30,30,0.9);
}
#hover{
    padding-right: 1px;
    z-index: 1;
    position: fixed;
    height: 100vh;
    width: 200px;
    left: -199px;
    /*background-color: red;*/
    transition: left 500ms;

}
#hover:hover {
    left: 0;
}
.selected {
    background-color: rgba(0,0,0, 0.7);
}
button {
    width: 100%;
    height: 50px;
    background-color: rgba(0,0,0,0);
    border: none;
    color: white;
}
button:hover {
    background-color: rgba(0,0,0, 0.4);
}
button:active {
    background-color: rgba(0,0,0, 0.6);
}
iframe {
    position: fixed;
    top: 0;
    left: 0;
    height: 100vh;
    width: 100vw;
    border: none;
}
</style>
