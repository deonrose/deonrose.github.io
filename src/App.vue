<template>
  <v-app>
    <v-container class="white">
      <v-row no-gutters justify="center" align="center">
        <v-col>
          <v-card class="pa-2" justify="center" align="center">
            <p id="hitokoto_text">获取中...</p>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </v-app>
</template>

<script>
export default {
  name: "App",

  components: {},

  data: () => ({
    //
  }),
};

fetch("https://v1.hitokoto.cn")
  .then((response) => response.json())
  .then((data) => {
    const hitokoto = document.getElementById("hitokoto_text");
    hitokoto.href = "https://hitokoto.cn/?uuid=" + data.uuid;
    hitokoto.innerText = data.hitokoto;
  })
  .catch(console.error);
</script>