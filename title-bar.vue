<template>
    <div class="title-bar">
        <span class="title-bar__name">Dany</span>
        <span class="title-bar__options">
            <span class="title-bar__item" @click="minimize">-</span>
            <span class="title-bar__item" @click="maximize">{}</span>
            <span class="title-bar__item title-bar__item--exit" @click="exit">x</span>
        </span>
    </div>
</template>

<style lang="scss">
$red: #cd5c5c;
$white: #f5f5f5;
$grey: #eee;

$title-bar--height: 30px;
$title-bar--exit-bg: $red;
$title-bar--exit-color: $white;
$title-bar--item-bg: $grey;

.title-bar {
  height: $title-bar--height;
  -webkit-app-region: drag;
  &__name {
    display: inline-block;
    line-height: $title-bar--height;
  }
  &__options {
    float: right;
    -webkit-app-region: no-drag;
  }
  &__item {
    display: inline-block;
    line-height: $title-bar--height;
    text-align: center;
    height: $title-bar--height;
    width: 50px;
    cursor: pointer;
    &:hover {
      background-color: $title-bar--item-bg;
      transition: background-color 0.3s ease;
    }
  }
  &__item--exit {
    &:hover {
      color: $title-bar--exit-color;
      background-color: $title-bar--exit-bg;
    }
  }
}
</style>


<script>
    const { remote } = require('electron')
    export default {
        name: 'title-bar',
        methods: {
            exit() { remote.getCurrentWindow().close() },
            maximize() {
                if(remote.getCurrentWindow().isMaximized())
                    remote.getCurrentWindow().unmaximize()
                else
                    remote.getCurrentWindow().maximize()
            },
            minimize() { remote.getCurrentWindow().minimize() }
        }
    }
</script>