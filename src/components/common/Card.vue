<template>
    <article class="card">
        <button class="card_btn" @click="toogleCardView">
            <img class="card_btn_icon" src="../../assets/eye-icon.svg" alt="" />
            {{btnText}} card number
        </button>
        <section class="card_box">
          <div class="card_box_header">
              <img class="card_box_header_icon" src="../../assets/card-logo.svg" alt="" />
          </div>  
          <p class="card_box_name">{{cardInfo.name}}</p>
          <p class="card_box_number">
            <card-dot v-for="num in cardNum" :key="cardInfo.id + num.value" :number="num"></card-dot>
          </p>
          <p class="card_box_details">
            <label class="card_box_details_label">Thru: </label>
            <span class="card_box_details_text">{{cardInfo.validTill}}</span>
            <label class="card_box_details_cvv">CVV: </label>
            <span class="card_box_details_text">{{cardInfo.cvv}}</span>
          </p>
          <div class="card_box_logo">
              <img class="card_box_logo_icon" src="../../assets/visa-logo.svg" alt="" />
          </div>
        </section>
    </article>
</template>
<script>
import CardDot from './CardDot';

export default {
  name: 'Card',
  components:  {
    CardDot
  },
  computed: {
    cardNum() {
      let numArr = [];
      let len = 0;
      while(len  < this.cardInfo.cardNumber.length) {
          const temp = {
            isDot: this.isHide && len <= 8,
            value: this.cardInfo.cardNumber.substr(len, 4)
          }
          numArr.push(temp);
          len += 4;
      }
      return numArr;
    }
  },
  props: {
    cardInfo: Object
  },
  data() {
      return {
        headerText: 'aspire',
        isHide: true,
        btnText: 'Show'
      }
  },
  methods: {
    toogleCardView() {
      this.isHide = !this.isHide
      this.btnText = this.isHide ? 'Show' : 'Hide';
    }
  }
}
</script>
<style lang="scss" scoped>
.card {
  color: $white;
  position: relative;
  width: 358px;
  margin: 2.5rem auto 0;

  &_btn {
    @include flex();
    align-items: center;
    position: absolute;
    cursor: pointer;
    height: 40px;
    width: 151px;
    padding-bottom: 15px;
    border: 0;
    right: 0;
    top: -25px;
    color: $card-color;
    background: $white;
    z-index: 1;
    border-radius: 6px;
    @include MediaQueries($desktop-and-above) {
      background: none;
    }
    &_icon {
      margin-right: 8px;
    }
  } 
  &_box {
    position: relative;
    margin-top: 25px;
    background: $card-color;
    border-radius: 1.2rem;
    z-index: 2;
    padding: 0 2.5rem 2.5rem;
    box-sizing: border-box;

    &_header, &_logo {
      @include flex();
      @include justify-content(flex-end);
    }

    &_header {
      padding-top: 2.5rem;
    }

    &_name {
      @extend .card-header;
      text-align: left;
      margin: 2.5rem 0;
    }

    &_number {
      @include flex();
      @extend .card-number;
      text-align: left;
      margin: 0;
    }

    &_details {
      @extend .card-details;
      margin: 1.3rem 0 0;
      text-align: left;
      &_cvv {
        margin-left: 3rem;
      }
    }
  }
}
</style>
