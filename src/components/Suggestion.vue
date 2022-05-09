<template>
<div class="suggestionbox" >
  <div class="suggestForm" :class="chooseOne!==null?'stepTwo':''" v-if="showSuggestion">
    <h4>How would you rate your experience?</h4>
    <p>您使用本页面的体验如何？</p>
    <div class="suggestIcon">
      <span :class="chooseOne==='Hate'?'hover':''" @click="chooseOne==='Hate'?chooseOne=null:chooseOne='Hate'">
        <b class="zkmIconfont zkm-zhongchaping"></b>
        <p class="animated slideInUp"><i class="zkmIconfont zkm-chaping2"></i> Hate</p>
      </span>
      <span :class="chooseOne==='Neutral'?'hover':''" @click="chooseOne==='Neutral'?chooseOne=null:chooseOne='Neutral'">
        <b class="zkmIconfont zkm-zhongping"></b>
        <p class="animated slideInUp"><i class="zkmIconfont zkm-zhongping2"></i> Neutral</p>
      </span>
      <span :class="chooseOne==='Love'?'hover':''" @click="chooseOne==='Love'?chooseOne=null:chooseOne='Love'">
        <b class="zkmIconfont zkm-haoping"></b>
        <p class="animated slideInUp"><i class="zkmIconfont zkm-haoping2"></i> Love</p>
      </span>
    </div>
    <div class="suggestContent animated fadeIn" v-if="chooseOne!==null">
      <a-textarea placeholder="Tell us about your experience…" :rows="4" v-model="experience"  style="resize:none" />
    </div>
    <div class="suggestBut animated fadeIn" v-if="chooseOne!==null">
      <a-button :type="experience?'primary':''" >
        Send
      </a-button>
    </div>
  </div>
  <!-- 悬浮提示 -->
  <span class="suggestion"  :class="showSuggestion?'hover':''" @click="showSuggestion = !showSuggestion">
    <i class="zkmIconfont zkm-tousujianyi"></i>
    <i class="zkmIconfont zkm-guanbi"></i>
  </span>
</div>
</template>

<script>
export default {
  name: 'Suggestion',
  data () {
    return {
      showSuggestion: false,
      chooseOne: null,
      experience: null
    }
  },
  methods: {

  }
}
</script>

<style scoped>
.suggestionbox{
  position: fixed;
  right: 82px;
  bottom: 110px;
  z-index: 99;
}
.suggestion{
  position: absolute;
  bottom:0;
  right:0;
  width: 40px;
  height: 40px;
  background: #1890FF;
  border-radius: 100%;
  /* box-shadow: 0 2px 10px 1px #999999; */
  text-align: center;
  line-height: 40px;
  cursor: pointer;
  transition: all 0.5s;
}
.suggestion:hover{
  box-shadow: 0 2px 20px 1px #999999;
}
.suggestion.hover{
  border-radius: 3px;
}
.suggestion .zkm-tousujianyi{
  display: block;
}
.suggestion .zkm-guanbi{
  display: none;
}
.hover .zkm-tousujianyi{
  display: none;
}
.hover .zkm-guanbi{
  display: block;
}
.zkmIconfont{
  color: #FFFFFF;
  font-size: 20px;
}
.suggestForm{
  position: absolute;
  bottom:40px;
  right:0;
  width: 380px;
  min-height: 210px;
  background: #FFFFFF;
  border: 1px solid #eee;
  border-radius: 5px;
  border-bottom-right-radius: 0;
  box-shadow:  0 2px 10px 1px #999999;
  padding: 20px;
}
.suggestForm h4{
  font-size: 16px;
  text-align: center;
}
.suggestForm>p{
  text-align: center;
}
.suggestIcon{
  display: flex;
  flex-direction: row;
  justify-content: space-around;
}
.suggestIcon span{
  display: flex;
  flex-direction: column;
  width: 33%;
  text-align: center;
}
.suggestIcon span p{
  font-size: 16px;
  display: flex;
  align-items: baseline;
  display: none;
}
.suggestIcon span p .zkmIconfont{
  font-size: 18px;
  line-height: 20px;
  width: 20px;
  height: 20px;
  border-radius: 100%;
  background-color: #DDDDDD;
  color:#FFFFFF!important;
  margin-right: 10px;
  text-align: center;
}
.suggestIcon .zkmIconfont{
  font-size: 40px;
  color: #DDDDDD;
  cursor: pointer;
}
.suggestIcon .zkmIconfont:hover{
  color: #1890FF;
}
.suggestIcon span:hover p{
  display: block;
}
.suggestIcon span.hover .zkmIconfont{
  color: #1890FF;
}
.suggestIcon span.hover p{
  display: block;
}
.suggestIcon span.hover p .zkmIconfont{
  background-color: #1890FF;
}
.stepTwo>h4,.stepTwo>p{
  display: none;
}
.stepTwo .suggestIcon span b{
  font-size: 30px;
}
.suggestBut{
  margin-top:10px;
  text-align: right;
}
</style>
