<template>
  <div class="wrap">
    <h1>THE 51 메일 서명 생성</h1>
    <h3>* 다우오피스 그룹웨어는 PC 환경에서만 서명 설정가능합니다. *<br/><span>* 모바일 웹, 앱에서 서명 설정 불가 *</span></h3>
    <div class="valueForm">
      <p>* 완료 버튼을 누르지 않으면 코드가 생성되지 않습니다. 입력 후 꼭 버튼을 눌러주세요. *</p>
      <div class="input_wrap">
        <label for="name">이름</label>
        <input type="text" id="name" v-model="name" placeholder="ex) 홍길동">
      </div>
      <hr>
      <div class="input_wrap">
        <label for="position">직위</label>
        <input type="text" id="position" v-model="position" placeholder="ex) 사원">
      </div>
      <hr>
      <div class="input_wrap">
        <label for="rank">직책</label>
        <input type="text" id="rank" v-model="rank" placeholder="ex) 팀원">
      </div>
      <hr>
      <div class="input_wrap">
        <label for="team">부서</label>
        <input type="text" id="team" v-model="team" placeholder="ex) DT Group">
      </div>
      <hr>
      <div class="input_wrap">
        <label for="pn">휴대폰번호</label>
        <input type="text" id="pn" v-model="pn" placeholder="ex) 01012345678">
      </div>
      <hr>
      <div class="input_wrap">
        <label for="com">회사구분</label>
        <select v-model="com">
          <option value="T51">The51</option>
          <option value="T51x">The51X</option>
        </select>
      </div>
      <hr>
      <div class="input_wrap">
        <button @click="[done(), popup('.done')]">입력완료</button>
      </div>
    </div>
    <hr>
    <div class="result">
      <h2>미리보기</h2>
      <p>* 입력한 값이 맞는지 확인해주세요. *</p>
      <div class="table">
        <div>
          <!-- <p>white</p> -->
          <table style="padding: 0; border: none; background: #FFFFFF; font-size: 11pt;">
            <tr>
              <td cellspacing="0" cellpadding="0">
                <span style="font-size: 1.13em; font-weight: 700; font-family: '맑은고딕', '나눔고딕', 'MS Gothic', 'AppleGothic'; line-height: 150%; color: #000000; display: inline-block; padding-right: 4px;">{{이름}}</span>
                <span style="font-size: 1.13em; font-weight: 700; font-family: '맑은고딕', '나눔고딕', 'MS Gothic', 'AppleGothic'; line-height: 150%; color: #000000;">{{직위}}</span><span style="display: inline-block; width: 0.06em;"></span><span style="display: inline-block; width: 0.25em; height: 0.25em; background-color: #E01728;"></span>
              </td>
            </tr>
            <tr style="height: 1.13em;">
              <td cellspacing="0" cellpadding="0">
                <span style="font-size: 0.69em; font-weight: 400; color: #575757; font-family: '맑은고딕', '나눔고딕', 'MS Gothic', 'AppleGothic'; vertical-align: baseline; line-height: 150%;">{{직책}}</span>
                <span style="display: inline-block; width: 0.19em; height: 0.19em; background-color: #BBBBBB; vertical-align: middle; border-radius: 100px; display: inline-block; margin: 0 4px;"></span>
                <span style="font-size: 0.69em; font-weight: 400; color: #575757; font-family: 'Tahoma'; vertical-align: baseline; line-height: 150%;">{{부서}}</span>
              </td>
            </tr>
            <tr style="height: 1.63em; width: 100%;">
              <td>
                <table style="width: 100%; font-size: 11pt;">
                  <tr>
                    <td style="width: 33.3%;" cellspacing="0" cellpadding="0">
                      <span style="font-size: 0.75em; font-weight: 700; color: #E01728; font-family: 'Tahoma'; vertical-align: top; line-height: 150%;">T.</span>&nbsp;<span style="font-size: 0.75em; font-weight: 700; font-family: 'Tahoma'; vertical-align: top; line-height: 150%; color: #000000;">02.332.6251</span>
                    </td>
                    <td style="width: 33.3%;" cellspacing="0" cellpadding="0">
                      <span style="font-size: 0.75em; font-weight: 700; color: #E01728; font-family: 'Tahoma'; vertical-align: top; line-height: 150%;">F.</span>&nbsp;<span style="font-size: 0.75em; font-weight: 700; font-family: 'Tahoma'; vertical-align: top; line-height: 150%; color: #000000;">02.332.6253</span>
                    </td>
                    <td style="width: 33.3%;" cellspacing="0" cellpadding="0">
                      <span style="font-size: 0.75em; font-weight: 700; color: #E01728; font-family: 'Tahoma'; vertical-align: top; line-height: 150%;">M.</span>&nbsp;<span style="font-size: 0.75em; font-weight: 700; font-family: 'Tahoma'; vertical-align: top; line-height: 150%; color: #000000;">{{휴대폰번호}}</span>
                    </td>
                  </tr>
                </table>
              </td>
            </tr>
            <tr>
              <td style="padding: 0;" cellspacing="0" cellpadding="0">
                <img :src="'https://the51dt.github.io/createSignature/sign_' + imgSrc + '.png'" title="logo" alt="logo" width="auto" height="42px" style="display: block;">
              </td>
            </tr>
          </table>
          <div class="input_wrap">
            <button @click="[copyContentWhite(), popup('.copy')]">white 코드 복사하기</button>
          </div>
        </div>
        <!-- 블랙코드 -->
        <!-- <div>
          <p>black</p>
          <table style="padding: 0; border: none; background: #000000; font-size: 11pt;">
            <tr>
              <td cellspacing="0" cellpadding="0">
                <span style="font-size: 1.13em; font-weight: 700; font-family: '맑은고딕', '나눔고딕', 'MS Gothic', 'AppleGothic'; line-height: 150%; color: #000000; display: inline-block; padding-right: 4px;">{{이름}}</span>
                <span style="font-size: 1.13em; font-weight: 700; font-family: '맑은고딕', '나눔고딕', 'MS Gothic', 'AppleGothic'; line-height: 150%; color: #000000;">{{직위}}</span><span style="display: inline-block; width: 0.06em;"></span><span style="display: inline-block; width: 0.25em; height: 0.25em; background-color: #E01728;"></span>
              </td>
            </tr>
            <tr style="height: 1.13em;">
              <td cellspacing="0" cellpadding="0">
                <span style="font-size: 0.69em; font-weight: 400; color: #575757; font-family: '맑은고딕', '나눔고딕', 'MS Gothic', 'AppleGothic'; vertical-align: baseline; line-height: 150%;">{{직책}}</span>
                <span style="display: inline-block; width: 0.19em; height: 0.19em; background-color: #BBBBBB; vertical-align: middle; border-radius: 100px; display: inline-block; margin: 0 4px;"></span>
                <span style="font-size: 0.69em; font-weight: 400; color: #575757; font-family: 'Tahoma'; vertical-align: baseline; line-height: 150%;">{{부서}}</span>
              </td>
            </tr>
            <tr style="height: 1.63em; width: 100%;">
              <td>
                <table style="width: 100%; font-size: 11pt;">
                  <tr>
                    <td style="width: 33.3%;" cellspacing="0" cellpadding="0">
                      <span style="font-size: 0.75em; font-weight: 700; color: #E01728; font-family: 'Tahoma'; vertical-align: top; line-height: 150%;">T.</span>&nbsp;<span style="font-size: 0.75em; font-weight: 700; font-family: 'Tahoma'; vertical-align: top; line-height: 150%; color: #000000;">02.332.6251</span>
                    </td>
                    <td style="width: 33.3%;" cellspacing="0" cellpadding="0">
                      <span style="font-size: 0.75em; font-weight: 700; color: #E01728; font-family: 'Tahoma'; vertical-align: top; line-height: 150%;">F.</span>&nbsp;<span style="font-size: 0.75em; font-weight: 700; font-family: 'Tahoma'; vertical-align: top; line-height: 150%; color: #000000;">02.332.6253</span>
                    </td>
                    <td style="width: 33.3%;" cellspacing="0" cellpadding="0">
                      <span style="font-size: 0.75em; font-weight: 700; color: #E01728; font-family: 'Tahoma'; vertical-align: top; line-height: 150%;">M.</span>&nbsp;<span style="font-size: 0.75em; font-weight: 700; font-family: 'Tahoma'; vertical-align: top; line-height: 150%; color: #000000;">{{휴대폰번호}}</span>
                    </td>
                  </tr>
                </table>
              </td>
            </tr>
            <tr>
              <td style="padding: 0;" cellspacing="0" cellpadding="0">
                <img src="https://the51dt.github.io/createSignature/logo.png" title="logo" alt="logo" width="auto" height="42px" style="display: block;">
              </td>
            </tr>
          </table>
          <div class="input_wrap">
            <button @click="[copyContentBlack(), popup('.copy')]">black 코드 복사하기</button>
          </div>
        </div> -->
      </div>
    </div>
    <hr>
    <div class="guide">
      <h2>서명 설정 방법</h2>
      <p>* 모바일 또는 앱에서는 서명 설정이 불가합니다. *</p>
      <img src="../src/assets/guide.png">
    </div>
    <div class="popup done">
      미리보기에서 입력값을 확인해주세요.
    </div>
    <div class="popup copy">
      코드 복사 완료<br>하단 서명 설정 방법을 따라 서명을 등록해주세요.
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
const name = ref('')
const position = ref('')
const rank = ref('')
const team = ref('')
const pn = ref('')
const com = ref('')
let imgSrc

const 이름 = ref()
const 직위 = ref()
const 직책 = ref()
const 부서 = ref()
const 휴대폰번호 = ref()
const 회사구분 = ref()

let codeW = ref('')
let codeB = ref('')

const done = () => {
  이름.value = name.value
  직위.value = position.value
  직책.value = rank.value
  부서.value = team.value
  휴대폰번호.value = pn.value.replace(/[^0-9]/g, '').replace(/^(\d{3})(\d{4})(\d{4})$/, `$1.$2.$3`)
  회사구분.value = com.value
  
  if (회사구분.value) {
    imgSrc = 회사구분.value
  }

  // const pnArr = []
  // pnArr.push(pn.value.substring(0,3))
  // pnArr.push(pn.value.substring(3,7))
  // pnArr.push(pn.value.substring(7,11))
  // 휴대폰번호.value = pnArr.join('.')

  codeW.value = `
  <table style="padding: 0; border: none; background: #FFFFFF; font-size: 11pt;">\n<tr>\n
      <td cellspacing="0" cellpadding="0">\n
        <span style="font-size: 1.13em; font-weight: 700; font-family: '맑은고딕', '나눔고딕', 'MS Gothic', 'AppleGothic'; line-height: 150%; color: #000000;">${이름.value}</span>\n
        <span style="font-size: 1.13em; font-weight: 700; font-family: '맑은고딕', '나눔고딕', 'MS Gothic', 'AppleGothic'; line-height: 150%; color: #000000;">${직위.value}</span><span style="display: inline-block; width: 0.06em;"></span><span style="display: inline-block; width: 0.25em; height: 0.25em; background-color: #E01728;"></span>\n
      </td>\n
    </tr>\n
    <tr style="height: 1.13em;">\n
      <td cellspacing="0" cellpadding="0">\n
        <span style="font-size: 0.69em; font-weight: 400; color: #575757; font-family: '맑은고딕', '나눔고딕', 'MS Gothic', 'AppleGothic'; vertical-align: baseline; line-height: 150%;">${직책.value}</span>\n
        <span style="display: inline-block; width: 0.19em; height: 0.19em; background-color: #BBBBBB; vertical-align: middle; border-radius: 100px;"></span>\n
        <span style="font-size: 0.69em; font-weight: 400; color: #575757; font-family: 'Tahoma'; vertical-align: baseline; line-height: 150%;">${부서.value}</span>\n
      </td>\n
    </tr>\n
    <tr style="height: 1.63em; width: 100%;">\n
      <td>\n
        <table style="width: 100%; font-size: 11pt;">\n
          <tr>\n
            <td style="width: 33.3%;" cellspacing="0" cellpadding="0">\n
              <span style="font-size: 0.75em; font-weight: 700; color: #E01728; font-family: 'Tahoma'; vertical-align: top; line-height: 150%;">T.</span>&nbsp;<span style="font-size: 0.75em; font-weight: 700; font-family: 'Tahoma'; vertical-align: top; line-height: 150%; color: #000000;">02.332.6251</span>\n
            </td>\n
            <td style="width: 33.3%;" cellspacing="0" cellpadding="0">\n
              <span style="font-size: 0.75em; font-weight: 700; color: #E01728; font-family: 'Tahoma'; vertical-align: top; line-height: 150%;">F.</span>&nbsp;<span style="font-size: 0.75em; font-weight: 700; font-family: 'Tahoma'; vertical-align: top; line-height: 150%; color: #000000;">02.332.6253</span>\n
            </td>\n
            <td style="width: 33.3%;" cellspacing="0" cellpadding="0">\n
              <span style="font-size: 0.75em; font-weight: 700; color: #E01728; font-family: 'Tahoma'; vertical-align: top; line-height: 150%;">M.</span>&nbsp;<span style="font-size: 0.75em; font-weight: 700; font-family: 'Tahoma'; vertical-align: top; line-height: 150%; color: #000000;">${휴대폰번호.value}</span>\n
            </td>\n
          </tr>\n
        </table>\n
      </td>\n
    </tr>\n
    <tr>\n
      <td style="padding: 0;" cellspacing="0" cellpadding="0">\n
        <img src="https://the51dt.github.io/createSignature/sign_${imgSrc}.png" title="logo" alt="logo" width="auto" height="42px" style="display: block;">\n
      </td>\n
    </tr>\n
  </table>`

  codeB.value = `
  test`
}

const copyContentWhite = async () => {
  try {
    await navigator.clipboard.writeText(codeW.value);
    console.log('Content copied to clipboard');
  } catch (err) {
    console.error('Failed to copy: ', err);
  }
}

// eslint-disable-next-line no-unused-vars
const copyContentBlack = async () => {
  try {
    await navigator.clipboard.writeText(codeB.value);
    console.log('Content copied to clipboard');
  } catch (err) {
    console.error('Failed to copy: ', err);
  }
}

const popup = (el) => {
  const popup = document.querySelector(el)
  popup.style.display = 'block'
  setTimeout(() => {
    popup.style.display = 'none'
  }, 5000);
}
</script>

<style>
.wrap {
  max-width: 800px;
  width: 100%;
  margin: 0 auto;
  font-family: "Noto Sans KR", sans-serif;
}
h1, h2, h3, p {
  text-align: center;
}
h3 span {
  color: #E01728;
}
.valueForm {
  margin-top: 40px;
}
.input_wrap {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 8px;
  gap: 8px;
}
.input_wrap label {
  flex-shrink: 0;
  min-width: 80px;
}
input {
  appearance: none;
  width: 83%;
  padding: 8px;
  border: 1px solid gray;
  border-radius: 6px;
}
select {
  width: 85.25%;
  padding: 7.5px 4px;
  border: 1px solid gray;
  border-radius: 6px;
}
button {
  appearance: none;
  border: none;
  border-radius: 8px;
  background: #E01728;
  color: white;
  width: 100%;
  height: 34px;
  cursor: pointer;
}
.result {
  margin-top: 24px;
}
.table {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  margin: 0 auto;
  margin-bottom: 36px;
}
.table button {
  margin-top: 24px;
}
.guide img {
  width: 100%;
}
.popup {
  display: none;
  position: fixed;
  bottom: 24px;
  width: 768px;
  background: #ffccd0;
  padding: 16px;
  text-align: center;
  border-radius: 16px;
  animation: popup 5s ease-in-out;
  z-index: 99;
}
@keyframes popup {
  0% { opacity: 0; bottom: -75px;}
  15% { opacity: 1; bottom: 24px;}
  85% { opacity: 1; bottom: 24px;}
  100% { opacity: 0; bottom: -75px;}
}
</style>
