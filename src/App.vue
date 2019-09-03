<template>
  <div id="app">
    <div class="page-loader" data-toggle="page-loader"></div>

  <a id="#top" href="#content" class="sr-only">Skip to content</a>

  <!-- ======== @Region: #header ======== -->
  <div id="header">

    
    <div data-toggle="sticky">

      <!--Header search region - hidden by default -->
      <div class="header-search collapse" id="search">
        <form class="search-form container">
          <input type="text" name="search" class="form-control search" value="" placeholder="Search">
          <button type="button" class="btn btn-link"><span class="sr-only">Search </span><i class="fa fa-search fa-flip-horizontal search-icon"></i></button>
          <button type="button" class="btn btn-link close-btn" data-toggle="search-form-close"><span class="sr-only">Close </span><i class="fa fa-times search-icon"></i></button>
        </form>
      </div>

      <!--Header & Branding region-->
      <div class="header">

        <!-- all direct children of the .header-inner element will be vertically aligned with each other you can override all the behaviours using the flexbox utilities (flexbox.html) All elements with .header-brand & .header-block-flex wrappers will automatically be aligned inline & vertically using flexbox, this can be overridden using the flexbox utilities (flexbox.htm) Use .header-block to stack elements within on small screen & "float" on larger screens use .order-first or/and .order-last classes to make an element show first or last within .header-inner or .headr-block elements -->
        <div class="header-inner container">
          <!--branding/logo -->
          <div class="header-brand">
            <a class="header-brand-text" href="/home" title="Home">
              <h1 class="h2">
                <span class="header-brand-text-alt">Trick</span>Together<span class="header-brand-text-alt">.</span>
              </h1>
            </a>
            <div class="header-divider d-none d-lg-block"></div>
            <div class="header-slogan d-none d-lg-block"></div>
          </div>
          <!-- other header content -->
          <div class="header-block order-12">

            <!--Search trigger -->
            <a href="#search" class="btn btn-icon btn-link header-btn float-right order-11" data-toggle="search-form" data-target=".header-search"><i class="fa fa-search fa-flip-horizontal search-icon"></i></a>

            <!-- mobile collapse menu button - data-toggle="collapse" = default BS menu - data-toggle="off-canvas" = Off-cavnas Menu - data-toggle="overlay" = Overlay Menu -->
            <a href="#top" class="btn btn-link btn-icon header-btn float-right d-lg-none" data-toggle="off-canvas" data-target=".navbar-main" data-settings='{"cloneTarget":true, "targetClassExtras": "navbar-offcanvas"}'> <i class="fa fa-bars"></i> </a>
            <!--Show/hide trigger for #offcanvas-sidebar -->
            <a href="#" title="Click me you'll get a surprise" class="btn btn-icon btn-link header-btn float-right order-last" data-toggle="off-canvas" data-target="#offcanvas-sidebar" data-settings='{"cloneTarget":false}'> <i class="ion-android-more-vertical"></i> </a>
          </div>

          <div class="navbar navbar-expand-md navbar-static-top">
            <!--everything within this div is collapsed on mobile-->
            <div class="navbar-main collapse">
              <!--main navigation-->
              <ul class="nav navbar-nav navbar-nav-stretch float-lg-right dropdown-effect-fade">

                <!-- Homepages -->
                

                <!-- Pages -->
                <li class="nav-item">
                  <a href="/gyms" class="nav-link" id="pages-drop">All Gyms</a>
                  <!-- Menu -->
                </li>

                <!-- Features -->
                <li class="nav-item dropdown">
                  <a href="#" class="nav-link dropdown-toggle" id="more-drop" data-toggle="dropdown" data-hover="dropdown">Login</a>
                  <div class="dropdown-menu">
                    <router-link to="/" class="dropdown-item">Login</router-link>
                    <router-link to="/users/new" class="dropdown-item">Signup</router-link>
                    <router-link to="/logout" class="dropdown-item">Logout</router-link>
                  </div>
                </li>

                <li class="nav-item">
                  <a href="/day_and_times_new" class="nav-link" id="pages-drop">New Session</a>
                  <!-- Menu -->
                </li>
                <li class="nav-item">
                  <a href="/day_and_times" class="nav-link" id="pages-drop">All Sessions</a>
                </li>
                <li class="nav-item">
                  <a href="/friend_requests" class="nav-link" id="pages-drop">Friend Requests</a>
                </li>
              </ul>
            </div>
            <!--/.navbar-collapse -->
          </div>
        </div>
      </div>
    </div>
  </div>


<!-- MY CODE --------************************************************* -->
      <router-link to="/users/new">New User</router-link> |
      <router-link to="/day_and_times/new">New Session</router-link> |
      <router-link to="/about">About</router-link> |
    <!-- </div>
 --><!-- MY CODE ----------**************************************************** -->
    <router-view/>

  </div>
</template>

<!-- <style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
 -->