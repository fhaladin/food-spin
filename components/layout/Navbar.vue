<template>
  <nav class="navbar navbar-expand-lg navbar-transparent bg-transparent">
    <a class="navbar-brand" href="#">
      <img class="navbar__logo" src="/img/logo.svg" alt="Food Spin Logo">
    </a>

    <div class="navbar__menu collapse navbar-collapse">
      <ul class="navbar-nav ms-auto mb-2 mb-lg-0">
        <li class="nav-item">
          <a class="nav-link" href="#">Breakfast</a>
        </li>

        <li class="nav-item">
          <a class="nav-link" href="#">Lunch</a>
        </li>

        <li class="nav-item">
          <a class="nav-link" href="#">Dinner</a>
        </li>
      </ul>

      <div class="nav-item">
        <a class="nav-link px-0" href="#">
          <IconLock />
        </a>
      </div>
    </div>
  </nav>
</template>

<style lang="scss" scoped>
  .navbar {
    z-index: 12;
    padding: 46px 100px;

    &__menu {
      width: 100%;
    }
  }

  .navbar-brand {
    margin-right: 170px;
  }

  .navbar-nav {
    margin-right: 475px;
  }

  .nav-link {
    color: $black;
    font-style: normal;
    font-weight: 500;
    font-size: 14px;
    line-height: 21px;
  }

  .navbar-expand-lg .navbar-nav .nav-link {
    padding-right: 30px;
    padding-left: 30px;
  }
</style>
