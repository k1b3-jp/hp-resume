<template>
  <!-- 現在ページの表示 -->
  <div class="current-num">
    <div class="num-circle" :class="checkCurrentPage(1)">
      {{ checkCurrentPage(1)["passed-page"] ? "✔︎" : 1 }}
    </div>
    <div class="num-circle" :class="checkCurrentPage(2)">
      {{ checkCurrentPage(2)["passed-page"] ? "✔︎" : 2 }}
    </div>
    <div class="num-circle" :class="checkCurrentPage(3)">
      {{ checkCurrentPage(3)["passed-page"] ? "✔︎" : 3 }}
    </div>
    <div class="num-circle" :class="checkCurrentPage(4)">
      {{ checkCurrentPage(4)["passed-page"] ? "✔︎" : 4 }}
    </div>
    <div class="num-circle" :class="checkCurrentPage(5)">
      {{ checkCurrentPage(5)["passed-page"] ? "✔︎" : 5 }}
    </div>
  </div>

  <div class="form-section">
    <div class="container">
      <!-- １ページ目のコンテンツの表示 -->
      <div class="contact-form" v-show="currentPage === 1">
        <div class="select">
          <h3 class="select__title">名前</h3>
          <input
            class="mt20"
            maxlength="50"
            name="contactName"
            v-model="contactName"
            placeholder=""
          />
        </div>

        <div class="select">
          <h3>性別</h3>
          <div class="selects sepa3">
            <input
              id="gender-select-1"
              type="radio"
              name="gender-select-1"
              v-model="gender"
              value="男性"
            />
            <label
              for="gender-select-1"
              class="select-button"
              :class="genderSelected('男性')"
            >
              男性
            </label>
            <input
              id="gender-select-2"
              type="radio"
              name="gender-select-2"
              v-model="gender"
              value="女性"
            />
            <label
              for="gender-select-2"
              class="select-button"
              :class="ageSelected('女性')"
            >
              女性
            </label>
            <input
              id="gender-select-3"
              type="radio"
              name="gender-select-3"
              v-model="gender"
              value="その他"
            />
            <label
              for="gender-select-3"
              class="select-button"
              :class="ageSelected('その他')"
            >
              その他
            </label>
          </div>
        </div>

        <div class="select">
          <h3>年齢</h3>
          <div class="selects sepa3">
            <input
              id="age-select-1"
              type="radio"
              name="age-select-1"
              v-model="age"
              value="20歳未満"
            />
            <label
              for="age-select-1"
              class="select-button"
              :class="ageSelected('20歳未満')"
            >
              20歳未満
            </label>
            <input
              id="age-select-2"
              type="radio"
              name="age-select-2"
              v-model="age"
              value="20歳以上"
            />
            <label
              for="age-select-2"
              class="select-button"
              :class="ageSelected('20歳以上')"
            >
              20歳以上
            </label>
          </div>
        </div>

        <div class="select">
          <h3 class="select__title">生息地</h3>
          <input
            class="mt20"
            maxlength="50"
            name="contactArea"
            v-model="contactArea"
            placeholder=""
          />
        </div>

        <div class="select">
          <h3 class="select__title">FC</h3>
          <h4>(複数選択可)</h4>
          <div class="selects selects--multi">
            <div class="selects--multi__item">
              <label for="fc-select-1" class="select-button">ハロプロ</label>
              <input
                id="fc-select-1"
                type="checkbox"
                name="fc-select-1"
                value="ハロプロ"
                v-model="selectFc"
              />
            </div>
            <div class="selects--multi__item">
              <label for="fc-select-2" class="select-button">M-line</label>
              <input
                id="fc-select-2"
                type="checkbox"
                name="fc-select-2"
                value="M-line"
                v-model="selectFc"
              />
            </div>
            <div class="selects--multi__item">
              <label for="fc-select-3" class="select-button">未加入</label>
              <input
                id="fc-select-3"
                type="checkbox"
                name="fc-select-3"
                value="未加入"
                v-model="selectFc"
              />
            </div>
          </div>
        </div>

        <div class="select">
          <h3 class="select__title">ヲタ歴</h3>
          <input
            class="mt20"
            maxlength="50"
            name="contactYear"
            v-model="contactYear"
            placeholder=""
          />
        </div>

        <div class="btn_wrap">
          <button class="b-next" @click="nextCurrentPage()">次へ</button>
        </div>
      </div>

      <!-- ２ページ目のコンテンツの表示 -->
      <div class="contact-form" v-show="currentPage === 2">
        <div class="select">
          <h3 class="select__title">推しグループ</h3>
          <h4>(複数選択可)</h4>
          <div class="selects selects--multi">
            <div class="selects--multi__item">
              <label for="group-select-1" class="select-button"
                >モーニング娘。</label
              >
              <input
                id="group-select-1"
                type="checkbox"
                name="group-select-1"
                value="モーニング娘。"
                v-model="selectGroup"
              />
            </div>
            <div class="selects--multi__item">
              <label for="group-select-2" class="select-button"
                >アンジュルム</label
              >
              <input
                id="group-select-2"
                type="checkbox"
                name="group-select-2"
                value="アンジュルム"
                v-model="selectGroup"
              />
            </div>
            <div class="selects--multi__item">
              <label for="group-select-3" class="select-button"
                >Juice=Juice</label
              >
              <input
                id="group-select-3"
                type="checkbox"
                name="group-select-3"
                value="Juice=Juice"
                v-model="selectGroup"
              />
            </div>
            <div class="selects--multi__item">
              <label for="group-select-4" class="select-button"
                >つばきファクトリー</label
              >
              <input
                id="group-select-4"
                type="checkbox"
                name="group-select-4"
                value="つばきファクトリー"
                v-model="selectGroup"
              />
            </div>
            <div class="selects--multi__item">
              <label for="group-select-5" class="select-button"
                >BEYOOOOONDS</label
              >
              <input
                id="group-select-5"
                type="checkbox"
                name="group-select-5"
                value="BEYOOOOONDS"
                v-model="selectGroup"
              />
            </div>
            <div class="selects--multi__item">
              <label for="group-select-6" class="select-button"
                >OCHA NORMA</label
              >
              <input
                id="group-select-6"
                type="checkbox"
                name="group-select-6"
                value="OCHA NORMA"
                v-model="selectGroup"
              />
            </div>
            <div class="selects--multi__item">
              <label for="group-select-7" class="select-button"
                >ハロプロ研修生</label
              >
              <input
                id="group-select-7"
                type="checkbox"
                name="group-select-7"
                value="ハロプロ研修生"
                v-model="selectGroup"
              />
            </div>
          </div>
        </div>

        <div class="select">
          <h3 class="select__title">推しメン</h3>
          <textarea
            class="mt20"
            cols="100"
            rows="8"
            maxlength="1000"
            name="contactMember"
            v-model="contactMember"
            placeholder=""
          ></textarea>
        </div>

        <div class="select">
          <h3 class="select__title">好きな曲</h3>
          <textarea
            class="mt20"
            cols="100"
            rows="8"
            maxlength="1000"
            name="contactSong"
            v-model="contactSong"
            placeholder=""
          ></textarea>
        </div>

        <div class="btn_wrap">
          <button class="b-back" @click="prevCurrentPage()">戻る</button>
          <button class="b-next" @click="nextCurrentPage()">次へ</button>
        </div>
      </div>

      <!-- ３ページ目のコンテンツの表示 -->
      <div class="contact-form" v-show="currentPage === 3">
        <div class="select">
          <h3 class="select__title">ヲタ活</h3>
          <h4>(複数選択可)</h4>
          <div class="selects selects--multi">
            <div class="selects--multi__item">
              <label for="action-select-1" class="select-button"
                >コンサート</label
              >
              <input
                id="action-select-1"
                type="checkbox"
                name="action-select-1"
                value="コンサート"
                v-model="selectAction"
              />
            </div>
            <div class="selects--multi__item">
              <label for="action-select-2" class="select-button">握手</label>
              <input
                id="action-select-2"
                type="checkbox"
                name="action-select-2"
                value="握手"
                v-model="selectAction"
              />
            </div>
            <div class="selects--multi__item">
              <label for="action-select-3" class="select-button">チェキ</label>
              <input
                id="action-select-3"
                type="checkbox"
                name="action-select-3"
                value="チェキ"
                v-model="selectAction"
              />
            </div>
            <div class="selects--multi__item">
              <label for="action-select-4" class="select-button"
                >イベント</label
              >
              <input
                id="action-select-4"
                type="checkbox"
                name="action-select-4"
                value="イベント"
                v-model="selectAction"
              />
            </div>
            <div class="selects--multi__item">
              <label for="action-select-5" class="select-button"
                >グッズ収集</label
              >
              <input
                id="action-select-5"
                type="checkbox"
                name="action-select-5"
                value="グッズ収集"
                v-model="selectAction"
              />
            </div>
            <div class="selects--multi__item">
              <label for="action-select-6" class="select-button"
                >創作(イラスト・加工等)</label
              >
              <input
                id="action-select-6"
                type="checkbox"
                name="action-select-6"
                value="創作(イラスト・加工等)"
                v-model="selectAction"
              />
            </div>
            <div class="selects--multi__item">
              <label for="action-select-7" class="select-button"
                >動画投稿</label
              >
              <input
                id="action-select-7"
                type="checkbox"
                name="action-select-7"
                value="動画投稿"
                v-model="selectAction"
              />
            </div>
            <div class="selects--multi__item">
              <label for="action-select-8" class="select-button">在宅</label>
              <input
                id="action-select-8"
                type="checkbox"
                name="action-select-8"
                value="在宅"
                v-model="selectAction"
              />
            </div>
            <div class="selects--multi__item">
              <label for="action-select-9" class="select-button">その他</label>
              <input
                id="action-select-9"
                type="checkbox"
                name="action-select-9"
                value="その他"
                v-model="selectAction"
              />
            </div>
          </div>
        </div>

        <div class="select">
          <h3 class="select__title">主な垢利用法</h3>
          <h4>(複数選択可)</h4>
          <div class="selects selects--multi">
            <div class="selects--multi__item">
              <label for="purpose-select-1" class="select-button"
                >ハロプロ</label
              >
              <input
                id="purpose-select-1"
                type="checkbox"
                name="purpose-select-1"
                value="ハロプロ"
                v-model="selectPurpose"
              />
            </div>
            <div class="selects--multi__item">
              <label for="purpose-select-2" class="select-button"
                >趣味（他趣味兼）</label
              >
              <input
                id="purpose-select-2"
                type="checkbox"
                name="purpose-select-2"
                value="趣味（他趣味兼）"
                v-model="selectPurpose"
              />
            </div>
            <div class="selects--multi__item">
              <label for="purpose-select-3" class="select-button">日常</label>
              <input
                id="purpose-select-3"
                type="checkbox"
                name="purpose-select-3"
                value="日常"
                v-model="selectPurpose"
              />
            </div>
            <div class="selects--multi__item">
              <label for="purpose-select-4" class="select-button">創作</label>
              <input
                id="purpose-select-4"
                type="checkbox"
                name="purpose-select-4"
                value="創作"
                v-model="selectPurpose"
              />
            </div>
            <div class="selects--multi__item">
              <label for="purpose-select-5" class="select-button">ROM専</label>
              <input
                id="purpose-select-5"
                type="checkbox"
                name="purpose-select-5"
                value="ROM専"
                v-model="selectPurpose"
              />
            </div>
          </div>
        </div>

        <div class="btn_wrap">
          <button class="b-back" @click="prevCurrentPage()">戻る</button>
          <button class="b-next" @click="nextCurrentPage()">次へ</button>
        </div>
      </div>

      <!-- ４ページ目のコンテンツの表示 -->
      <div class="contact-form" v-show="currentPage === 4">
        <div class="select">
          <h3>異性のおとももち</h3>
          <div class="selects sepa3">
            <input
              id="friend-select-1"
              type="radio"
              name="friend-select-1"
              v-model="friend"
              value="NG"
            />
            <label
              for="friend-select-1"
              class="select-button"
              :class="friendSelected('NG')"
            >
              NG
            </label>
            <input
              id="friend-select-2"
              type="radio"
              name="friend-select-2"
              v-model="friend"
              value="OK"
            />
            <label
              for="friend-select-2"
              class="select-button"
              :class="friendSelected('OK')"
            >
              OK
            </label>
            <input
              id="friend-select-3"
              type="radio"
              name="friend-select-3"
              v-model="friend"
              value="大歓迎"
            />
            <label
              for="friend-select-3"
              class="select-button"
              :class="friendSelected('大歓迎')"
            >
              大歓迎
            </label>
          </div>
        </div>

        <div class="select">
          <h3>現場交流</h3>
          <div class="selects sepa3">
            <input
              id="site-select-1"
              type="radio"
              name="site-select-1"
              v-model="site"
              value="NG"
            />
            <label
              for="site-select-1"
              class="select-button"
              :class="siteSelected('NG')"
            >
              NG
            </label>
            <input
              id="site-select-2"
              type="radio"
              name="site-select-2"
              v-model="site"
              value="同性のみ"
            />
            <label
              for="site-select-2"
              class="select-button"
              :class="siteSelected('同性のみ')"
            >
              同性のみ
            </label>
            <input
              id="site-select-3"
              type="radio"
              name="site-select-3"
              v-model="site"
              value="OK"
            />
            <label
              for="site-select-3"
              class="select-button"
              :class="siteSelected('OK')"
            >
              OK
            </label>
          </div>
        </div>

        <div class="select">
          <h3 class="select__title">自己アピール欄</h3>
          <textarea
            class="mt20"
            cols="100"
            rows="8"
            maxlength="1000"
            name="contactAppeal"
            v-model="contactAppeal"
            placeholder=""
          ></textarea>
        </div>

        <div class="btn_wrap">
          <button class="b-back" @click="prevCurrentPage()">戻る</button>
          <button class="b-next" @click="nextCurrentPage()">次へ</button>
        </div>
      </div>

      <div class="contact-form contact-form--export" v-show="currentPage === 5">
        <div class="select">
          <h3 class="select__title">プロフィール画像</h3>
          <input type="file" ref="preview" @change="uploadFile" />
        </div>
        <div class="btn_wrap">
          <button class="b-back" @click="prevCurrentPage()">戻る</button>
          <button class="b-next" @click="nextCurrentPage()">次へ</button>
        </div>
      </div>

      <!-- 履歴書書き出しの表示 -->
      <div class="contact-form contact-form--export" v-show="currentPage === 6">
        <div class="btn_wrap">
          <button class="b-canvas" @click="exportImage()">保存する</button>
        </div>

        <div class="resume" id="capture">
          <div class="resume__title">
            <h4>ハロプロ履歴書</h4>
            <p v-show="date">{{ date }}現在</p>
          </div>
          <div class="resume__flex">
            <div class="resume__photo">
              <div v-if="url">
                <img :src="url" />
              </div>
            </div>
            <table class="resume__top">
              <tbody>
                <tr>
                  <td class="title title--md">名前</td>
                  <td colspan="3">{{ contactName }}</td>
                </tr>
                <tr>
                  <td class="title title--md">性別</td>
                  <td>{{ gender }}</td>
                  <td class="title title--md">年齢</td>
                  <td>{{ age }}</td>
                </tr>
                <tr>
                  <td class="title title--md">生息地</td>
                  <td colspan="3">{{ contactArea }}</td>
                </tr>
              </tbody>
            </table>
          </div>
          <table class="resume__main">
            <tbody>
              <tr>
                <td class="title title--sm">FC</td>
                <td>
                  <span v-for="fc in selectFc" :key="fc"> {{ fc }}</span>
                </td>
                <td class="title title--sm">ヲタ歴</td>
                <td>{{ contactYear }}</td>
              </tr>
              <tr>
                <td class="title title--lg">推しグループ</td>
                <td colspan="3">
                  <span v-for="group in selectGroup" :key="group">
                    {{ group }}
                  </span>
                </td>
              </tr>
              <tr>
                <td class="title title--lg">推しメン</td>
                <td colspan="3">{{ contactMember }}</td>
              </tr>
              <tr>
                <td class="title title--lg">好きな曲</td>
                <td colspan="3">{{ contactSong }}</td>
              </tr>
              <tr>
                <td class="title title--lg">ヲタ活</td>
                <td colspan="3">
                  <span v-for="action in selectAction" :key="action">
                    {{ action }}
                  </span>
                </td>
              </tr>
              <tr>
                <td class="title title--lg">主な垢利用法</td>
                <td colspan="3">
                  <span v-for="purpose in selectPurpose" :key="purpose">
                    {{ purpose }}
                  </span>
                </td>
              </tr>
              <tr>
                <td class="title title--lg">異性のおとももち</td>
                <td>{{ friend }}</td>
                <td class="title title--md">現場交流</td>
                <td>{{ site }}</td>
              </tr>
              <tr class="resume__main--appeal">
                <td colspan="4">
                  <span class="title">自己アピール欄</span><br />{{
                    contactAppeal
                  }}
                </td>
              </tr>
            </tbody>
          </table>
        </div>

        <div class="btn_wrap">
          <button class="b-back" @click="prevCurrentPage()">戻る</button>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import { ref } from "vue";
import html2canvas from "html2canvas";
import moment from "moment";
export default {
  name: "ContactForm",
  data() {
    return {
      selectPurpose: [],
      selectAction: [],
      selectGroup: [],
      selectFc: [],
      url: "",
      date: "",
    };
  },
  setup() {
    // 現在のページ管理
    let currentPage = ref(1);
    const checkCurrentPage = (number) => {
      return {
        "current-page": currentPage.value === number,
        "passed-page": currentPage.value > number,
      };
    };
    const nextCurrentPage = () => currentPage.value++;
    const prevCurrentPage = () => currentPage.value--;

    /* １ページ目のデータ管理 */
    let contactName = ref(null);
    let age = ref("");
    const ageSelected = (radioValue) => {
      return { selected: age.value === radioValue };
    };
    let gender = ref("");
    const genderSelected = (radioValue) => {
      return { selected: gender.value === radioValue };
    };
    let contactArea = ref(null);
    let contactYear = ref(null);

    /* ２ページ目のデータ管理 */
    let contactMember = ref(null);
    let contactSong = ref(null);

    /* ４ページ目のデータ管理 */
    let friend = ref("");
    const friendSelected = (radioValue) => {
      return { selected: friend.value === radioValue };
    };
    let site = ref("");
    const siteSelected = (radioValue) => {
      return { selected: site.value === radioValue };
    };
    let contactAppeal = ref(null);

    return {
      contactName,
      gender,
      genderSelected,
      contactArea,
      contactYear,
      contactMember,
      contactSong,
      friendSelected,
      siteSelected,
      contactAppeal,
      currentPage,
      checkCurrentPage,
      nextCurrentPage,
      prevCurrentPage,
      age,
      ageSelected,
    };
  },
  methods: {
    uploadFile() {
      const file = this.$refs.preview.files[0];
      this.url = URL.createObjectURL(file);
    },
    exportImage() {
      html2canvas(document.querySelector("#capture"), {
        scale: 2,
      }).then((canvas) => {
        const link = document.createElement("a");
        link.href = canvas.toDataURL();
        link.download = `hello-project-resume.png`;
        link.click();
      });
    },
    printDate: function () {
      return new Date().toLocaleDateString();
    },
  },
  mounted: function () {
    this.date = moment(this.printDate()).format("YYYY年MM月DD日");
  },
};
</script>

<style scoped lang="scss">
h3 {
  margin: 0 0 0.5em 0;
}
h4 {
  margin: 0 0 0.5em 0;
}
textarea {
  width: 80%;
}

.current-num {
  padding: 20px 0;
  display: flex;
  flex-wrap: nowrap;
  justify-content: center;
  align-items: center;
  gap: 10px;
  .num-circle {
    background: #fff;
    width: 40px;
    height: 40px;
    line-height: 40px;
    border-radius: 50%;
  }
}
.form-section {
  max-width: 600px;
  margin: 0 auto;
  background: #fff;
  border-radius: 5px;
  -webkit-border-radius: 5px;
  -moz-border-radius: 5px;
  box-shadow: 1px 1px 2px rgb(128 128 128 / 50%);
  margin-bottom: 15px;
  padding: 15px;

  .contact-form {
    &--export {
      .resume {
        margin: 20px auto;
        padding: 15px 10px;
        &__title {
          display: flex;
          justify-content: center;
          align-items: center;
          position: relative;
          h4 {
            display: inline;
          }
          p {
            position: absolute;
            right: 0;
          }
        }
        &__photo {
          flex: 0 0 30%;
          padding: 10px;
          img {
            width: 100%;
            height: auto;
          }
        }
        &__flex {
          display: flex;
        }
        table {
          border-spacing: 0;
          border-collapse: collapse;
          border-right: 1px solid;
          border-bottom: 1px solid;
          &.resume__top {
            border-bottom: none;
          }
          .title {
            font-weight: bold;
          }
          tr {
            td {
              border: 1px solid;
              border-right: 0px;
              border-bottom: 0px;
              padding: 10px 5px;
              &.title {
                &--sm {
                  width: 10%;
                }
                &--md {
                  width: 20%;
                }
                &--lg {
                  width: 30%;
                }
              }
              span {
                margin: 0 1rem;
                display: inline-block;
              }
            }
          }
        }
        &__top {
          width: 70%;
          margin-left: auto;
          tr:last-of-type {
            td {
              border-bottom: none;
            }
          }
        }
        &__main {
          width: 100%;
          &--appeal {
            td {
              text-align: left;
              min-height: 100px;
            }
          }
        }
      }
    }
    .select {
      padding-bottom: 20px;
      margin-bottom: 20px;
      border-bottom: 1px dotted #ccc;
    }
    .selects {
      &--multi {
        display: flex;
        flex-direction: column;
        flex-wrap: nowrap;
        justify-content: flex-start;
        align-items: center;
        &__item {
          display: flex;
          flex-wrap: wrap;
          justify-content: space-around;
          align-items: center;
          margin: 5px auto;
          label {
            width: 200px;
          }
        }
      }
    }
  }

  .btn_wrap {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    align-items: center;
    gap: 10px;
    button {
      display: block;
      width: 160px;
      padding: 0.8em;
      text-align: center;
      text-decoration: none;
      color: #0075c2;
      border: 2px solid #0075c2;
      border-radius: 3px;
      transition: 0.4s;
      &.b-back {
        border: none;
      }
      &.b-canvas {
        margin: 10px auto;
        color: #e070d3;
        border: 2px solid #e070d3;
        &:hover {
          background: #e070d3;
        }
      }
      &:hover {
        background: #0075c2;
        color: #fff;
      }
    }
  }
}
</style>