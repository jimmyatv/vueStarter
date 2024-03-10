<template>
    <section class="ourHero">
        <div class="heroLeft">
            <div>
                <h2>Hi, my name's <br> Aleksandar</h2>
                <p>I am Frontend developer</p>
                <p>and I like what I do !!!</p>
            </div>
        </div>

        <div class="heroRight">
            <div>
                <img :src="mainPhoto" alt="">
            </div>
        </div>
    </section>
</template>



<script>
import mainPhoto from '@/assets/mainPhoto2.png';
export default {
    setup() {
        return {
            mainPhoto: mainPhoto
        }
        
    },
}
</script>


//CSS
<style scoped>
.ourHero {
    display: flex;
    gap: 1rem;
    background: #f4d0d0;
    background-image: url(@/assets/waveBcgr.svg);
    background-size: cover;
    background-position: center;
    /* border: 1px solid red; */

}
.heroLeft {
    flex: 1;
    display: flex;
    justify-content: center;
    align-items: center;
}

.heroRight {
    flex: 1;
    display: flex;
    justify-content: center;
    align-items: end;
}
.heroRight>div>img {
    width: 600px;
    margin-top: 50px;
}

h2 {
    font-size: 3rem;
    color: #fff;
}
p {
    font-size: 2rem;
    color: #f4d0d0;
}

</style>