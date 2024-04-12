<template>
<nav class="navbar fixed-top" :class="'navbar-' + theme + ' bg-' + theme">
      <div class="container-fluid">
        <a class="navbar-brand" href="#">{{text.link.text}}</a>
        <button class="navbar-toggler" type="button" data-bs-toggle="offcanvas" data-bs-target="#offcanvasDarkNavbar" aria-controls="offcanvasDarkNavbar" aria-label="Toggle navigation">
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="offcanvas offcanvas-end" :class="'text-bg-' + theme" tabindex="-1" id="offcanvasDarkNavbar" aria-labelledby="offcanvasDarkNavbarLabel">
          <div class="offcanvas-header">
            <h5 class="offcanvas-title" id="offcanvasDarkNavbarLabel">{{ theme }}</h5>
            <button type="button" class="btn-close btn-close-white" data-bs-dismiss="offcanvas" aria-label="Close"></button>
          </div>
          <div class="offcanvas-body">
            <ul class="navbar-nav justify-content-end flex-grow-1 pe-3">
              <div v-for="(page, index) in pages" :key="index">
                <li class="nav-item">
                  <a @click.prevent="func(index)" :title="'Esse site vai para o ' + page.link.text" class="nav-link" :href="page.link.url">{{ page.link.text }}</a>
                </li>
              </div>
              <li class="nav-item dropdown">
                <a class="nav-link dropdown-toggle" href="#" role="button" data-bs-toggle="dropdown" aria-expanded="false">Mais opções</a>
                <ul class="dropdown-menu" :class="'dropdown-menu-' + theme">
                  <li><a class="dropdown-item" href="#">
                    <button type="button" @click.prevent="change" :class="['btn', 'btn-' + theme]"> {{modo}} </button>
                  </a></li>
                  <li><a class="dropdown-item" href="#">Another action</a></li>
                </ul>
              </li>
            </ul>
          </div>
        </div>
      </div>
    </nav>
</template>

<script>
export default{
    props: ['text','pages','theme','change','modo','func'],

}
</script>