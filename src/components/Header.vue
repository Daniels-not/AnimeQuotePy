<template>
  <header>
      <h1>{{ title }}</h1>
  </header>
</template>

<script>
export default {
    props: ['title'],
}
</script>

<style lang="scss">
@import "../sass/main.scss";

header {
    display: flex;
    justify-content: center;
    @include toRem(padding-top, 24);

    h1{
        @include toRem(font-size, 32);
        color: get_color(dark);
        font-weight: 700;
        text-align: center;
        text-transform: uppercase;
        @include toRem(padding-bottom, 8);
        border-bottom: 0.32rem solid get_color(primary);
    }
}
</style>