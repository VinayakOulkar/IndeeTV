<template>
    <div id="HeaderContainer" class="d-flex flex-column">
        <div id="HeaderContainer-div1"></div>
        <div id="HeaderContainer-div2" class="container text-center">

            <div id="text" class="pt-3 pb-2">OTHER WAYS TO WATCH</div>
            
            <div id="HeaderImgs" class="row justify-content-center mb-1">
                <!-- Apple-Tv icon -->
                <div class="col-2">
                    <img :src="apple_tv" style="width: 2rem;"/>
                </div>
                <!-- IOS icon -->
                <div class="col-2">
                    <img :src="ios_logo"/>
                </div>
                <!-- Roku icon -->
                <div class="col-2">
                    <img :src="roku_logo"/>
                </div>
                <!-- Amazon-Fire icon -->
                <div class="col-2 pt-1">
                    <img :src="amazon_logo"/>
                </div>
            </div>
            
            <div id="text" class="pt-2 pb-4" style="font-size: 0.6rem;">Search for AppleTV+ FYC on your App Store</div>
        </div>
    </div>
    
</template>

<script>
export default {
  name: 'HeaderContainer',
  data() {
    return {
      apple_tv: require('@/assets/Images/apple-tv.png'),
      ios_logo: require('@/assets/Images/ios-logo.jpg'),
      roku_logo: require('@/assets/Images/roku.png'),
      amazon_logo: require('@/assets/Images/amazon-fire.png')
    };
  }
}
</script>

<style>

    #HeaderContainer
    {
        margin: 0 0 0 0 !important;
    }
    
    #HeaderContainer-div1
    {
        background-color: rgba(45, 49, 55, 1);
        height: 4vh;
        margin: 0 0 0 0 !important;
    }

    #HeaderContainer-div2
    {
        color:rgba(213, 213, 213, 1);
        background-color: rgba(36, 39, 44, 1);
        margin: 0 0 0 0 !important;
    }

    #HeaderImgs img
    {
        width: 2.3rem;
    }

    #HeaderContainer-div2 #text
    {
        font-size: 0.7rem;
    }

    #HeaderImgs img:hover
    {
        cursor: pointer;
    }

</style>
