<template>
      <div class="main-baner">
      <div class="banner-content">
         <div class="layout-container">
            <h1 class="title">Baner</h1>
            <p class="desc">text</p>
         </div>
      </div>
    </div>
</template>
<script>
export default {
    name:'main-baner'
}
</script>
<style lang="scss">
@import '../styles/variables.scss';
@import '../styles/share.scss';
@import '../styles/bootstrap.scss'; 
.main-baner{
  position: relative;
  &:before {
    display: block;
    content: "";
    width: 100%;
    padding-top: 17.36%;
    background:$symantic-block-color;
  }

  .banner-content{
    text-align: left;
    display:flex;
    position: absolute;
    align-items: center;
    top: 0; 
    right: 0;
    width: 100%;
    height: 100%;

  }
@include media-breakpoint-down(sm) { }
    &:before {
      padding-top: 25%;
    }
  }
</style>

  
  
