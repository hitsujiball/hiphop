<template>
  <div class="container">
    <div class="inner">
      <h1 class="title">
        HIPHOP用語変換ツール
      </h1>

      <div class="inputedText">
        <input type="text" v-model:value="prevText" v-on:keyup="changeHiphop">
      </div>

      <div class="result">
        <p>{{ resultText }}</p>
      </div><!--/.result -->

    </div>
    <div class="bg"></div>
  </div>
</template>

<script>
// import Textbox from '~/components/Textbox.vue'

export default {
  // components: {
  //   Textbox
  // },

  data: function() {
    return {
      prevText: '',
      inputText: '',
      resultText: 'Rapで白黒つけようぜ！'
    }
  },

  methods: {
    changeHiphop: function() {
      // ヒップホップ変換用語に変換

      const target = {
        'illな': '良い',
        'wackな': 'ダサい',
        'ビーフ': '争い',
        'ディス': '否定',
        'プチャヘンザッ': '手を上げて',
        'a.k.a': 'またの名を',
        'レペゼン': '代表',
        'ホーミー': '友達',
        'ドープな': 'イカした',
        'リスペクト': '尊敬',
        'チェケラッ': '確認',
        'crew': '仲間',
        'hood': '地元',
        'リリック': '歌詞',
        'インダハウス': 'ここにいる'
      };

      this.inputText = this.prevText;

      for(const key in target) {
        // console.log('key:' + key);
        // console.log('target:' + target[key]);

        let regExp = new RegExp(target[key], 'g');
        // 必ずdata内のinputTextに代入すること
        this.inputText = this.inputText.replace(regExp, key);
      }

      // resultTextに結果を代入
      return this.resultText = this.inputText;
    }
  }
}
</script>

<style>
.container {
  position: relative;
  overflow: hidden;
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.inner {
  position: relative;
  padding: 80px 120px;
  color: #fff;
  background-color: rgba(0, 0, 0, 0.8);
  z-index: 100;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 500;
  font-size: 42px;
  letter-spacing: 1px;
}

.inputedText {
  margin-top: 32px;
}
input {
  width: 500px;
  font-size: 20px;
}
button {
  display: block;
  width: 120px;
  height: 32px;
  margin: 12px auto 0;
  border: none;
  font-size: 16px;
  font-weight: bold;
  color: #fff;
  background-color: #dc143c;
}

.result {
  margin-top: 24px;
  font-size: 18px;
  font-weight: bold;
  color: #dc143c;
}

.bg {
  position: absolute;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background: url('/images/dj_img.jpg') no-repeat center center;
  background-size: cover;
  z-index: 0;
}
</style>
