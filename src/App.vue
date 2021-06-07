<template>
  <div id="app" class="app">
    <Nav />
    <article class="app_container">
      <div class="app_container_top">
        <Header />
        <Content />
      </div>
      <div class="app_container_bottom">
        <!-- <CardAction />
        <AccordionContainer /> -->
      </div>
      <Menu />
    </article>
  </div>
</template>

<script>
import Header from './components/Header';
import Content from './components/Content';
import Menu from './components/Menu';
// import CardAction from './components/CardAction';
// import AccordionContainer from './components/AccodionContainer';
import Nav from './components/Nav';

export default {
  name: 'App',
  components: {
    Header,
    Content,
    Menu,
    // CardAction,
    // AccordionContainer,
    Nav
  }
}
</script>

<style lang="scss">
.app {
  &_container {
    &_top {
     // position: fixed;
      background: $background-blue;
      width: 100%;
      z-index: $index2;
      top: 0;
    }

    &_bottom {
      position: relative;
      z-index: $index3;
      // margin-top: 50rem;
      background: $white;
      padding-bottom: 5rem;
      border-radius: 16px;
    }
  }
}

@include MediaQueries($desktop-and-above) {
  .app {
    @include flex();
    width: 100%;

    &_container {
      width: 75%;
      background: $white;
      &_top {
        position: relative;
        background: $white;
      }
      .menu {
        display: none;
      }
    }
  }
}
</style>
