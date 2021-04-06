<template>
  <v-app>
    <wel-app-bar />
    <v-sheet>
      <v-container
        fluid
        :style="{ maxWidth: '1280px' }"
      >
        <v-row
          v-for="(menu, i) in menus"
          :key="`menu-${i}`"
        >
          <v-col cols="12">
            <div :is="`wel-${menu.title}`" />
          </v-col>
        </v-row>
      </v-container>
    </v-sheet>
    <bef-login-fotter />
  </v-app>
</template>

<script>
import welAppBar from "~/components/welcome/welAppBar.vue";
import welProducts from "~/components/welcome/welProducts.vue";
import welPrice from "~/components/welcome/welPrice.vue";
import welContact from "~/components/welcome/welContact.vue";
import welCompany from "~/components/welcome/welCompany.vue";
import befLoginFotter from '~/components/beforeLogin/befLoginFotter.vue';

export default {
  components: { 
    welAppBar,
    welProducts,
    welPrice,
    welContact,
    welCompany,
    befLoginFotter
  },
  data () {
    return {
      menus: [
        { title: 'about', subtitle: 'このサイトはブログ"独学プログラマ"で公開されているチュートリアルのデモアプリケーションです' },
        { title: 'products', subtitle: '他にはない優れた機能の数々' },
        { title: 'price', subtitle: '会社の成長に合わせた3つのプラン' },
        { title: 'contact', subtitle: 'お気軽にご連絡を' },
        { title: 'company', subtitle: '私たちの会社' }
      ]
    }
  }
}
</script>
