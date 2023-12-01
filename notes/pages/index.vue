<template>
    <div class="container">
        <div>
            <br/>
            <logo />
            <center><h1 class="title text-xl">Notes for your life</h1></center>
            <figure>
                <img src="../public/images/assets/images.png">

                <center><h1 class="note">Login or register to continue</h1></center>

                <NuxtLink to="/login" class="login text-base bg-blue-600
px-6 py-2 text-white rounded-lg hover:bg-blue-600/80">Login</NuxtLink>
<NuxtLink to="/register" class="register text-base bg-blue-600
px-6 py-2 text-white rounded-lg hover:bg-blue-600/80">Register</NuxtLink>
            </figure>
        </div>
    </div>
</template>

<style scoped>
.note{
    margin: 20px
}
.login{
    margin: 0px 415px;
}
.register{
    margin: 0px -312px;
}
img{
    margin: 30px 545px;
    width: 30px;

}
</style>