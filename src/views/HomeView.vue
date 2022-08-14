<template>
  <div class="home">
    <!-- <a :href="book.url">{{book.name}}</a> -->
    <button
    @click="btnClicked"
    v-show="isAcitve">表示</button>
    <ul>
      <li
      v-for="vfor in vFors"
      :key="vfor.id">
      {{vfor}}
      </li>
    </ul>
    <div class="total">{{totalPrice}}</div>
</div>
</template>

<style lang="scss">

/* =============================================
  //よく使うfont
  ============================================= */
$fontFamilyHiraGo:'Hiragino Sans', Meiryo;
$fontFamilyHiraGo: "ヒラギノ角ゴ Pro W3", "Hiragino Kaku Gothic Pro", "メイリオ", "Meiryo", sans-serif;
$fontFamilyYuMin: "游明朝", "YuMincho", "ヒラギノ明朝 Pro W3", "Hiragino Mincho Pro", "ＭＳ Ｐ明朝", "MS PMincho", serif;
$fontFamilyHiraMin: "ヒラギノ明朝 Pro W3", "Hiragino Mincho Pro", "ＭＳ Ｐ明朝", "MS PMincho", serif;
$fontFamilyMeiryo: "メイリオ", "Meiryo", "ヒラギノ角ゴ Pro W3", "Hiragino Kaku Gothic Pro", "ＭＳ Ｐゴシック", sans-serif;
$fontFamilyGaramondPremierPro: "garamond-premier-pro", serif;

/* =============================================
  //レスポンシブの設定
  ============================================= */
$tab: 767px;
@mixin tab {
    @media (max-width: ($tab)) {
        @content;
    }
}

.pc_contents{
    display: block;
    @include tab(){
        display: none !important;
    }
}

.sp_contents{
    display: none !important;
    @include tab(){
        display: block !important;
    }
}

/* =============================================
/ get_vwの設定
============================================= */
@function get_vw($size, $viewport: 1536) {
    $rate: 100 / $viewport;
    @return $rate * $size * 1vw;
}

p{
  margin: 0;
}

ul{
  list-style: none;
  padding: 0;
}

</style>

<script>
// @ is an alias to /src

export default {
  name: 'HomeView',
  data () {
    return {
      google: 'https://google.com',
      books: [
        {
          name: 'あああああ',
          url: 'https://google.com'
        },
        {
          name: 'いいいいい',
          url: 'https://google.com'
        },
        {
          name: 'ううううううう',
          url: 'https://google.com'
        },
        {
          name: 'えええええええ',
          url: 'https://google.com'
        }
      ],
      isAcitve: true,
      vFors: ['item01', 'item02', 'item03', 'item04', 'item05', 'item06'],
      price: 1,
      items: 1
    }
  },
  created () {
    // これはdomが描画される前の処理
  },
  mounted () {
    // これはdomが描画された後の処理
  },
  watch: {
    // dataの特定のものが変更されると処理を行う（computedの進化？）
    // 他のcomputedなどが変更されたときも発火する
    books: {
      handler () {
        console.log('変更しました。')
      },
      deep: true,
      immediate: true
    }
  },
  computed: {
    // dataの中身が変わる段階で処理がされる
    totalPrice () {
      return this.price * this.items
    }
  },
  methods: {
    btnClicked () {
      console.log('clicked!!')
    }
  }
}
</script>
