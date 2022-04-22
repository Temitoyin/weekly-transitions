<template>
<nav class="navigation">
    <div class="navigation__logoWrapper">
        <h1 class=navigation__logo>Advertising</h1>
    </div>
    <ol class="navigation__links">
        <li>Benefits</li>
        <li>Costs</li>
        <li>Login</li>
        <li>Signup</li>

    </ol>
</nav>
</template>

<style scoped>
.navigation{
    display: flex;
    justify-content: space-between;
    color: Black;
    padding: 2rem 3rem;
    z-index: 1;
}
.navigation__logo{
    font-size: 2rem;
    font-weight: 500;
}
.navigation__links{
    list-style-type: none;
    display: flex;
}
li{
    font-size: 18px;
    margin-right: 20px;
}
li:last-child{
    margin-right: 0px;
}
</style>