<template>
    <header class="main-header">

        <!-- Logo -->
        <div class="logo">
            <!-- mini logo for sidebar mini 50x50 pixels -->
            <span class="logo-mini"><b>La</b>Vu</span>
            <!-- logo for regular state and mobile devices -->
            <span class="logo-lg"><b>Lara</b>Vue</span>
        </div>

        <!-- Header Navbar: style can be found in header.less -->
        <nav class="navbar navbar-static-top">
            <!-- Sidebar toggle button-->
            <a href="#" class="sidebar-toggle" data-toggle="push-menu" role="button">
                <span class="sr-only">Toggle navigation</span>
            </a>
            <!-- Navbar Right Menu -->
            <div class="navbar-custom-menu">
                <ul class="nav navbar-nav">
                    <!-- User Account: style can be found in dropdown.less -->
                    <li class="dropdown user user-menu">
                        <a href="#" class="dropdown-toggle" data-toggle="dropdown">
                            <img src="/images/avatar.png" class="user-image" alt="User Image">
                            <span class="hidden-xs">{{ user.name }}</span>
                        </a>
                        <ul class="dropdown-menu">
                            <!-- User image -->
                            <!--
                              <li class="user-header">
                                  <img src="/images/avatar.png" class="img-circle" alt="User Image">
                                  <p>
                                      Alexander Pierce - Web Developer
                                      <small>Member since Nov. 2012</small>
                                  </p>

                              </li>
                              -->
                            <!-- Menu Body -->
                            <!--
                            <li class="user-body">
                                <div class="row">
                                    <div class="col-xs-4 text-center">
                                        <a href="#">Followers</a>
                                    </div>
                                    <div class="col-xs-4 text-center">
                                        <a href="#">Sales</a>
                                    </div>
                                    <div class="col-xs-4 text-center">
                                        <a href="#">Friends</a>
                                    </div>
                                </div>
                            </li>
                            -->
                            <!-- Menu Footer-->
                            <li class="user-footer">
                                <!--
                                 <div class="pull-left">
                                     <a href="#" class="btn btn-default btn-flat">Profile</a>
                                 </div>
                                 -->
                                <div class="pull-right">
                                    <a @click="signOut" href="javascript:;" class="btn btn-default btn-flat">Sign out</a>
                                </div>
                            </li>
                        </ul>
                    </li>
                </ul>
            </div>
        </nav>
    </header>
</template>

<script>
    import {mapGetters} from 'vuex'

    export default {
        created() {
            this.$store.dispatch('fetchAuthUser')
        },
        computed:
            mapGetters({
                user: 'authUser'
            })
        ,
        methods: {
            signOut() {
                this.$store.dispatch('logOut');
                this.$router.replace({name: 'login'})
            }
        }
    }
</script>