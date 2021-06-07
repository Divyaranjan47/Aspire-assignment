<template>
    <header class="header">
        <div class="header_left">
            <p class="header_left_head">Account balance</p>
            <p class="header_left_desc">
                <button class="header_left_desc_btn">S$</button>
                3,000
            </p>
        </div>
        <div class="header_right">
            <img class="header_right_logo" src="../assets/aspire-logo.svg" alt="" />
            <button class="header_right_new-btn">
                <picture>
                    <source media="(max-width:1024px)" srcset="../assets/box.svg">
                    <img class="img" src="../assets/box-white.svg" alt="">
                </picture>
                New card
            </button>
        </div>
    </header>
</template>
<script>
export default {
    name: 'Header'
}
</script>
<style lang="scss" scoped>
.header{
    @include MediaQueries($tablet-and-below) {
        position: sticky;
        top: 0;
    }
    @include flex();
    @include justify-content(space-between);
    color: $white;
    padding: 1.5rem 2.5rem 2.5rem;

    &_left {
        margin-top: 1.5rem;
        &_head {
            @extend .header-text;
            margin: 0;
        }
        &_desc {
            @include flex();
            @extend .bold-price;
            align-items: center; 
            margin: 1rem 0 0;
            &_btn {
                @extend .white-bold;
                background: $card-color;
                border: 0;
                border-radius: 4px;
                padding: .2rem 1.5rem;
                margin-right: 1rem;
            }
        }
    }

    &_right {
        text-align: right;
        &_new-btn {
            @include flex();
            align-items: center;
            width: 100%;
            background: transparent;
            border: 0;
            color: $blue-text;
            padding: 2.5rem 0 0 0;
            text-align: right;

            .img {
                margin-right: 8px;
            }
        }
    }
}

@include MediaQueries($desktop-and-above) {
    .header {
        padding: 6rem 6rem 3.4rem 6rem;
        &_left {
            &_head {
                color: $black-text;
            }

            &_desc {
                color: $black-text;
            }
        }

        &_right {
            &_logo {
                display: none;
            }

            &_new-btn {
                background: $blue-card;
                color: $white;
                padding: 1rem 1.2rem;
                border-radius: 4px;
            }
        }
    }
}
</style>