<template>
  <div class="currency">
    <div class="container">
      <div class="currencies">
        <div class="currency-header">
          <p class="textdate">Курс EUR на {{date.date}}</p>
          <div class="title-current">
            <ul>
              <li>USD</li>
              <li>RUB</li>
              <li>HRK</li>
              <li>NOK</li>
              <li>JPY</li>
              <li class="active">EUR</li>
              <li>CAD</li>
            </ul>
          </div>
          <div class=" arrow right"><img src="@/assets/right.svg"></div>
          <div class=" arrow left"><img src="@/assets/left.svg"></div>
        </div>
        <div class="currency-body">
          <div class="currency-block">
            <p class="currency-up">5 <span class="pure-currency">EUR =</span></p>
            <p class="currency-down">409,37<span>RUB</span></p>
          </div>
          <div class="currency-block">
            <p class="currency-up">5 <span class="pure-currency">EUR =</span></p>
            <p class="currency-down">3,00<span>CAD</span></p>
          </div>
          <div class="currency-block">
            <p class="currency-up">5 <span class="pure-currency">EUR =</span></p>
            <p class="currency-down">10 000,12<span>HRK</span></p>
          </div>
          <div class="currency-block">
            <p class="currency-up">5 <span class="pure-currency">EUR =</span></p>
            <p class="currency-down currency-small">409 000 000,37<span>JPY</span></p>
          </div>
          <div class="btns">
            <button class=" btn back"><img src="@/assets/left.svg"/><span class="back-text">Назад</span></button>
            <button class="btn forward"><span class="forward-text">Далее</span><img src="@/assets/right.svg"/></button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  data() {
    return {
      courses: null,
      date: ''
    }
  },
  mounted() {
    axios
    .get('https://api.openrates.io/latest')
    .then(response => this.date = response.data)
  }
}
</script>

<style scoped>
.container {
  display: flex;
  justify-content: center;
}
.currencies {
  position: relative;
  height: 582px;
  width: 720px;
  border: 1px solid;
  font-family: 'Roboto';
  color: #2B2D33;
}
.currency-header {
  position: absolute;
  top: 0;
  width: 100%;
  height: 111px;
  background-color: #FFE782;
  padding: 0 24px;
  box-sizing: border-box;
}
.arrow {
  width: 10px;
  position: absolute;
  bottom: 16px;
  cursor: pointer;
}
.right {
  right: 20px;
}
.left {
  left: 20px;
}
.textdate {
  font-size: 21px;
  line-height: 25px;
  margin: 30px 0 0 0;
}
.title-current {
  position: absolute;
  width: 620px;
  height: 48px;
  bottom: 0;
  margin: 0 calc(54px - 24px) 0 calc(46px - 24px);
}
ul li {
  list-style-type: none;
}
ul {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  padding: 0;
}
/* li.active {
  position: absolute;
  background: #fff;
  width: 90px;
  height: 48px;
} */

.currency-body {
  bottom: 0;
  position: absolute;
  width: 100%;
  height: calc(100% - 111px);
  padding: 78px 24px 24px 24px;
  box-sizing: border-box;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  flex-wrap: wrap;
}

.currency-block {
  width: 327px;
  height: 138px;
  box-shadow: 0px 3px 6px rgba(157, 157, 157, 0.16);
  border-radius: 12px;
  padding: 18px 30px 17px 30px;
  box-sizing: border-box;
}
p {
  margin: 0;
}
p span {font-size: 24px;}
span.pure-currency {
  color: #787878;
}

p.currency-up {
  font-size: 24px;
  line-height: 28px;
  letter-spacing: 0.0171429px;
}
p.currency-small {
  font-size: 33px;
}
p.currency-down {
  font-size: 48px;
  line-height: 56px;
  letter-spacing: 0.0342857px;
}


.btns {
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: flex-end;
}
button.btn {
  width: 112px;
  height: 34px;
  box-shadow: 0px 5px 6px rgba(157, 157, 157, 0.16);
  border-radius: 8px;
  font-size: 14px;
  line-height: 16px;
  letter-spacing: 1px;
  text-transform: uppercase;
  border: none;
  outline: none;
  cursor: pointer;
}
button.back {
  margin-right: 19px;
}
button span {
  margin: 0 7px;
}
</style>
