<template>
    <div class="sidebar">
        <div class="top">
            <div class="avatar">
                <span><i class="fa fa-user"></i></span>
            </div>

            <div class="info">
                <p class="name">Monalisa</p>
                <p class="status">Online</p>
            </div>
        </div>
        
        <div class="menu">
            <ul>
                <li><router-link :to="{name:'home'}"><i class="fa fa-home"></i> Home</router-link></li>
            </ul>
        </div>
    </div>
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
    name: 'SideBarComponent'
})
</script>

<style lang="scss" >

    .sidebar {

        .top {
            width: 100%;
            display: flex;
            justify-content: center;
            padding: 25px 5px;
            align-items: center;
            margin-top: 50px;
            font-weight: 200;

            .avatar {
                margin-right: 10px;

                span {
                    display: block;
                    width: 50px;
                    height: 50px;   
                    border-radius: 50%;
                    background-color: #FFFFFF;
                    display: flex;
                    justify-content: center;
                    align-items: center;
                    font-size: 25px;
                    color: #666666;
                }
                
            }

            .info {

                p {
                    margin: 0px;
                    color: #FFFFFF;
                }

                .name {
                    font-size: 14px;
                }

                .status {
                    
                    font-size: 12px;
                }
            }
            
        }
    }

    .menu {
        margin-top: 15px;
        padding: 10px 0 15px 5px;

        ul li {
            margin: 15px ;
            font-size: 18px;
            list-style: none;
            font-weight: 200;

            a {
                color: #FFFFFF;
                text-decoration: none;
            }
        }
        
        
    }

</style>