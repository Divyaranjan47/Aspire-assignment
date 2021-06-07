<template>
    <article class="expense-bar">
        <div class="expense-bar_left" :class="transaction.category">
            <img class="expense-bar_left_img" :src="require(`../../assets/${transaction.category}.svg`)" alt=""/>
        </div>
        <div class="expense-bar_center">
            <p class="expense-bar_center_name">{{transaction.name}}</p>
            <p class="expense-bar_center_date">{{transaction.date}}</p>
            <p class="expense-bar_center_msg">
                <span class="expense-bar_center_msg_circle">
                    <img class="img" src="../../assets/business-and-finance.svg" />
                </span>
                {{transaction.comment}}
            </p>
        </div>
        <div class="expense-bar_right" :class="{'credit': isCredit}">
            <span class="expense-bar_right_sign">{{isCredit ? '+' : '-'}}</span>
            {{transaction.amount}}
            <img class="expense-bar_right_icon" src="../../assets/next.svg" alt="" />
        </div>
    </article>
</template>

<script>
export default {
    name: 'ExpenseBar',
    computed: {
        isCredit() {
            return this.transaction.type === 'credit';
        }
    },
    props: {
        transaction: Object
    }
}
</script>

<style lang="scss" scoped>
.expense-bar {
    @include flex();
    @include justify-content(space-between);
    padding: 1.5rem 0;
    border-bottom: 1px solid $border-grey;

    &::last {
        border: none
    }

    &_left {
      height: 4.8rem;
      width: 4.8rem;
      border-radius: 50%;
      text-align: center;

      &.default {
          background: $blue-round;
      }

      &.flights {
          background: $green-round;
      }

      &.megaphone {
          background: $red-round;
      }

      &_img {
          padding: 1.5rem 0;
      }
    }

    &_center {
        margin: 0 0 0 1.2rem;

        &_name {
            @extend .black-title;
        }

        &_date {
            @extend .date-text;
        }

        &_msg {
            @extend .blue-text;
            margin-top: 1.2rem;

            &_circle {
                display: inline-block;
                width: 2.4rem;
                height: 2rem;
                border-radius: 40%;
                background: $blue-card;
                text-align: center;
                .img {
                    padding: 0 0 1px;
                }
            }
        }
    }

    &_right {
        @extend .black-bold;

        &.credit {
            color: $card-color;
        }
    }
}
</style>