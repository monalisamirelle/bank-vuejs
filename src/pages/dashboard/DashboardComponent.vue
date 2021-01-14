<template>
    <div class="main">
        <div class="sidebar">
            <SideBarComponent />
        </div>

        <div class="content-right">
            <div class="navbar">
                <NavBarComponent />
            </div>

            <div class="pages">
                <slot name="slot-pages"></slot>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import Vue from 'vue';
import SideBarComponent from '../dashboard/components/SideBarComponent.vue';
import NavBarComponent from '../dashboard/components/NavBarComponent.vue';
export default Vue.extend({
    name: 'DashboardComponent',
    components: {
        SideBarComponent,
        NavBarComponent
    }
})
</script>

<style lang="scss" src="./style.scss" scoped />