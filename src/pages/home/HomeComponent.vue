<template>
    <DashboardComponent>
        <div slot="slot-pages" class="content-pages">
            <div class="mt-5">
                <div class="row">
                    <div class="col-12 col-md-12">
                        <ListComponent />
                    </div>
                </div>
            </div>
        </div>
    </DashboardComponent>
</template>

<script lang="ts">
import Vue from 'vue';
import DashboardComponent from '../dashboard/DashboardComponent.vue';
import ListComponent from '../../components/ListComponent.vue';

export default Vue.extend({
    name: 'HomeComponent',
    mounted() {

    },
    methods: {

    },
    components: {
        DashboardComponent,
        ListComponent
    }
})
</script>

<style scoped>

</style>