<template>
  <header class="main-header header-style-two alternate2 header-black">
    <div class="auto-container">
      <!-- Main box -->
      <div class="main-box">
        <!--Nav Outer -->
        <div class="nav-outer">
          <div class="logo-box">
            <div class="logo">
              <a href="/"
                ><img src="/images/logo.svg" alt="logo-worksaleuz"
              /></a>
            </div>
          </div>

          <nav class="nav main-menu">
            <ul class="navigation" id="navbar">
              <!-- <li class="<%- defaults.url === "/" ? "current" : "" -%>">
                                <a href="/"><span>Главная</span></a>
                            </li>
                            <li class="<%- defaults.url === "/vacancy" ? "current" : "" -%>">
                                <a href="/vacancy"><span>Вакансии</span></a>
                            </li> -->
              <!-- Only for Mobile View -->
              <li class="mm-add-listing">
                <a href="/vacancy/create" class="theme-btn btn-style-one"
                  >Добавить вакансию</a
                >
              </li>
            </ul>
          </nav>
          <!-- Main Menu End-->
        </div>

        <div class="outer-box">
          <!-- Login/Register -->
          <div class="btn-box">
            <a href="/vacancy/create" class="theme-btn btn-style-two"
              ><span class="btn-title">Добавить вакансию</span></a
            >
          </div>
        </div>
      </div>
    </div>

    <!-- Mobile Header -->
    <div class="mobile-header">
      <div class="logo">
        <a href="/"><img src="/images/logo.svg" alt="" title="" /></a>
      </div>

      <!--Nav Box-->
      <div class="nav-outer clearfix">
        <div class="outer-box">
          <!-- Login/Register -->
          <div class="login-box">
            <a href="login-popup.html" class="call-modal"
              ><span class="icon-user"></span
            ></a>
          </div>

          <a href="#nav-mobile" class="mobile-nav-toggler navbar-trigger"
            ><span class="flaticon-menu-1"></span
          ></a>
        </div>
      </div>
    </div>

    <!-- Mobile Nav -->
    <div id="nav-mobile"></div>
  </header>
</template>

<script>
export default {
  name: "Header",
  components: {},
};
</script>

<style></style>
