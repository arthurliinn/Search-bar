<template>
    <div class="result-item">
        <div class="icon">
            <i class="fas fa-globe-americas"></i>
        </div>
        <div class="post">
            <h1>{{post.title.split("").splice(0,15).join("") }}...</h1>
            <p>{{post.body.split("").splice(0,50).join("") }}</p>
        </div>
    </div>
</template>

<script>
export default {
  props: ['post'],
};
</script>

<style scoped>
h1{
    margin-top: 0px;
    margin-bottom: .25em;
    font-size:14px;
}

p{
    margin-top: 0em;
    font-size: 12px;
}
.result-item{
    clear: both;

    zoom: 0;
    overflow: hidden;
}

.icon, .post{
    float: left;
}

.icon{
    width: 32px;

    font-size:24px;
    color: #8385FF;
}

.post{
    width: calc(100% - 32px);
    padding-left: .5em;

    box-sizing: border-box;
}
</style>
