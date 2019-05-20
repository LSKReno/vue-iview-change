<template>
    <div id="app">
        <router-view/>
    </div>
</template>

<script>
export default {
    name: "app"
};
</script>

<style>
* {
    margin: 0;
    padding: 0;
}
html,
body {
    width: 100%;
    height: 100%;
    min-height: 300px;
}
#app {
    font-family: "Avenir", Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    width: 100%;
    height: 100%;
    background: linear-gradient(90deg, #ff9999 2%, #99ccff 100%);
    box-shadow: inset 0 0 1px 0 rgba(255, 255, 255, 0.5);
    background: linear-gradient(
        48deg,
        #c4759c,
        #7aa3cc,
        #d18f69,
        #88b172,
        #cf5d5d
    );
    background-size: 1000% 1000%;

    -webkit-animation: AnimationName 40s ease infinite;
    -moz-animation: AnimationName 40s ease infinite;
    -o-animation: AnimationName 40s ease infinite;
    animation: AnimationName 40s ease infinite;
}

@-webkit-keyframes AnimationName {
    0% {
        background-position: 0% 42%;
    }
    50% {
        background-position: 100% 59%;
    }
    100% {
        background-position: 0% 42%;
    }
}
@-moz-keyframes AnimationName {
    0% {
        background-position: 0% 42%;
    }
    50% {
        background-position: 100% 59%;
    }
    100% {
        background-position: 0% 42%;
    }
}
@-o-keyframes AnimationName {
    0% {
        background-position: 0% 42%;
    }
    50% {
        background-position: 100% 59%;
    }
    100% {
        background-position: 0% 42%;
    }
}
@keyframes AnimationName {
    0% {
        background-position: 0% 42%;
    }
    50% {
        background-position: 100% 59%;
    }
    100% {
        background-position: 0% 42%;
    }
}
</style>
