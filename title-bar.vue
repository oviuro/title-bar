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