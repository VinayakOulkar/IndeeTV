<template>
    <div id="LogoConatainer" class="">
        <div class="d-flex justify-content-center">
            <img :src="mgmlogo" alt="MGM Logo">
            <p style="line-height: 1;">Global <br/>Distribution</p>
        </div>
    </div>
</template>

<script>
export default {
  name: 'LogoContainer',
  data() {
    return {
      mgmlogo: require('@/assets/Images/MGM_Monogram_OneColor_White.png')
    };
  }
}
</script>

<style>

#LogoConatainer {
    height: 56px;
}

img {
    width: 91px;
}

p {
    color: white;
    font-size: 18px;
}
</style>
