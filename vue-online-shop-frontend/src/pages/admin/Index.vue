<template>
    <div>
        <div class='admin-new'>
            <div class="container">
                <div class='col-lg-3 col-md-3 col-sm-12 col-xs-12'>
                    <ui class="admin-menu">
                        <li>
                            <router-link to="/admin">View Products</router-link>
                        </li>
                        <li>
                            <router-link to='/admin/new'> New Products</router-link>
                        </li>
                    </ui>
                </div>
                <router-view></router-view>
            </div>
        </div>
    </div>
</template>