<template>
    <div class="container-page">
        <el-header>
            <TopBar></TopBar>
        </el-header>
        <el-container>
            <!-- <LoginPage></LoginPage> -->
            <el-aside width="200px">
                <AsideBarLeft></AsideBarLeft>
            </el-aside>
            <el-container>
                <el-main>
                    <BodyContent></BodyContent>
                </el-main>
                <el-footer>
                    <FooterBar></FooterBar>
                </el-footer>
            </el-container>
        </el-container>
    </div>
</template>

<script>
import TopBar from './Main/Top/TopBar.vue';
import BodyContent from './Main/Body/BodyContent.vue';
import AsideBarLeft from './Main/Aside/AsideBarLeft.vue';
import FooterBar from './Main/Footer/FooterBar.vue';

// import LoginPage from './Login/LoginPage.vue';
TopBar;
export default {
    name: 'ContainerPage',
    components: {
        // LoginPage,
        TopBar,
        BodyContent,
        AsideBarLeft,
        FooterBar,
    },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.container-page {
    width: 100%;
    height: 100%;
}
</style>
