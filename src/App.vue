<template>
  <div id="app">
    <nav class="sb-topnav navbar navbar-expand navbar-dark bg-dark">
      <!-- Navbar Brand-->
      <a class="navbar-brand ps-3" href="/">Javascript Framework Watcher Dashboard</a>
      <!-- Sidebar Toggle-->
      <button class="btn btn-link btn-sm order-1 order-lg-0 me-4 me-lg-0" id="sidebarToggle" href="#!">
        <i class="fas fa-bars"></i>
      </button>
      <!-- Navbar Search-->

      <!-- Navbar-->
      <ul class="navbar-nav ms-auto ms-end-0 me-3 me-lg-4">
        <!-- <li class="nav-item dropdown">
          <a
            class="nav-link dropdown-toggle"
            id="navbarDropdown"
            href="#"
            role="button"
            data-bs-toggle="dropdown"
            aria-expanded="false"
          ></a>
          <ul class="dropdown-menu dropdown-menu-end" aria-labelledby="navbarDropdown">
            <li><a class="dropdown-item" href="#!">Settings</a></li>
            <li><a class="dropdown-item" href="#!">Activity Log</a></li>
            <li><hr class="dropdown-divider" /></li>
            <li><a class="dropdown-item" href="#!">Logout</a></li>
          </ul>
        </li> -->
      </ul>
    </nav>

    <router-view />
    <footer class="footer py-4 bg-light mt-auto">
      <div class="px-4">
        <div class="d-flex align-items-center justify-content-between small">
          <div class="text-muted">Copyright &copy; Your Website 2021</div>
          <div>
            <a href="#">Privacy Policy</a>
            &middot;
            <a href="#">Terms &amp; Conditions</a>
          </div>
        </div>
      </div>
    </footer>
  </div>
</template>

<style>
#app {
  margin-top: 75px;
  margin-left: 10px;
}
.block {
  flex: 0 0 auto;
}
.container {
  --bs-gutter-x: 1.5rem;
  --bs-gutter-y: 0;
  display: flex;
  flex-wrap: wrap;
  padding: 50px;
}
.container1 {
  font-family: arial;
  font-size: 24px;
  margin: 25px;

  display: flex;
  justify-content: center;
}
.footer {
  position: fixed;
  bottom: 0px;
  width: 100%;
}
a {
  text-decoration: none;
}
</style>
