<template>
    <div class="navbar-fixed">
        <nav class=''>
            <div class='container'>
                <div class="nav-wrapper">
                <router-link :to="{name:'Home'}" class="mainFont brand-logo lime-text text-accent-2">
                  <span>Games Loop</span>
                  <img src='../../assets/controller.png'/>
                </router-link>
                <ul class="right hide-on-med-and-down">
                    <li>
                        <form class="browser-default right">
                            <input id="search-input" placeholder="Search" type="text" class="browser-default search-field white" name="q" value="" autocomplete="off" aria-label="Search box">
                            <label for="search-input"><i class="material-icons search-icon">search</i></label> 
                            <i class="material-icons search-close-icon">cancel</i>
                            <div class="search-popup">
                            <div class="search-content">
                                <label class="search-heading">Most Visited</label>
                                <ul class="popup-list">
                                  <li class=""><a class="grey-text" href="#">Google</a></li>
                                  <li class=""><a class="grey-text" href="#">Apple</a></li><li class=""><a class="grey-text" href="#">Microsoft</a></li><li class=""><a class="grey-text" href="#">Github</a></li>
                                </ul>
                            </div>
                            </div>
                        </form>
                    </li>
                    <li class="dds">
                        <a class="dropdown-trigger" data-target="dropdown">
                            <i class="material-icons">arrow_drop_down</i>
                        </a>
                        <ul id="dropdown" class="dropdown-content lime accent-2">
                            <li><a href="#" class=''>Services</a></li>
                            <li><a href="#" class=''>About</a></li>
                            <li><a href="#" class=''>Blog</a></li>
                            <li><a href="#" class=''>Contact</a></li>
                        </ul>
                    </li>
                </ul>

                  <a href="#" data-target="slide-out" class="sidenav-trigger"><i class="material-icons">menu</i></a>
                  <ul id="slide-out" class="sidenav lime accent-2">
                      <li>
                        <router-link :to="{name:'Home'}" class="mainFont brand-logo">
                          <span>Games Loop</span>
                          <img src='../../assets/controller.png'/>
                        </router-link>
                      </li>
                      <li><div class="divider"></div></li>
                      <li><a href="#">Services</a></li>
                      <li><a href="#">About</a></li>
                      <li><a href="#">Blog</a></li>
                      <li><a href="#">Contact</a></li>
                  </ul>
                </div>
            </div>
        </nav>
    </div>
</template>

<script>

    $(document).ready(function(){
        $('.dropdown-trigger').dropdown();
        $('.sidenav').sidenav();
    });

export default {
    name:'navLayout',
    data() {
        return {

        }
    }
}
</script>

<style>

nav {
  background:linear-gradient(rgba(8, 8, 91, 0.4),rgba(8, 8, 91, 0.4)), url('../../assets/noise.png')  center;
  background:#c00;
}

nav .brand-logo {
    font-size:24px;
    display:flex;
    align-items:center;
}

nav .brand-logo img {
  max-width: 55px;
  max-height: 55px;
  margin:0 10px;
}

nav form {
  position: relative;
  height: 100%;
  background: inherit;
}
.nav-wrapper{
  background: inherit;
  
}

.search-close-icon{
  display: none!important;
  position: absolute;
  top: 0;
  left: 100%!important;
  padding-left: 0px;
  color: rgba(0, 0, 0, 0.54);
  transition: color .2s;
  cursor: pointer;
}


.my-grey{
  background: #f7f7f7;
}

input.search-field {
  font-weight: 500;
  color: rgba(0, 0, 0, 0.54);
  border-radius: 2px;
  border: 0;
  border-radius: 5px;
  height: 36px;
  padding: 8px 8px 8px 60px;
  width: 200px;
  background: #f7f7f7;
  transition: background 0.2s, width .2s;
}
input.search-field:hover {
  background: #ebebeb;
}
.searchbox {
  position: relative;
}
::placeholder {
  color: rgba(0, 0, 0, 0.54);
}
input.search-field:focus {
  outline: none;
  width: 500px;
  color: #212121;
}
input.search-field:focus:hover {
  background: #f7f7f7;
}
.search-icon {
  position: absolute;
  top: 0;
  padding-left: 20px;
  color: rgba(0, 0, 0, 0.54);
}
.search-content {
  color: #303c42;
  width: 90%;
  margin: auto;
  height: auto;
  padding: 8px 10px;
}
.search-heading {
  color: #757575;
  display: block;
  font-size: 12px;
  line-height: 30px;
}
input.search-field ~ .search-popup {
  overflow: hidden;
  left: 0px;
  min-height: 50px;
  max-height: 700px;
  width: 200px;
  top: -450px; 
  position: absolute;
  z-index: 1;
  box-shadow: 0 2px 2px 0 rgba(0, 0, 0, 0.14),0 3px 1px -2px rgba(0, 0, 0, 0.12), 0 1px 5px 0 rgba(0, 0, 0, 0.2);
  transition: width .2s, top .2s ease-in-out;
  border-radius: 2px;
  background-color: #fff;
}
input.search-field:focus ~ .search-popup {
  width: 500px;
  top: 50px;
}

.top-margin {
  margin-top: 8px;
}

.dropdown-content {
  top: 70px  !important;
  border-radius:5px  !important;
  min-width:120px !important;
}
.dropdown-content li > a, .dropdown-content li > span {
    color:#173893;
}

.sidenav {
  font-size:30px;
}
.sidenav .brand-logo {    
    color: #c00;
    position: relative;
    font-size: 14px;
    display: flex;
    align-items: center;
    margin: 20px;
}
.sidenav li > a {
    color:#173893;
    display: block;
    font-size: 18px;
    font-weight: 500;
    line-height: 48px;
    padding:30px;
}
.sidenav-overlay {
    background-color: rgba(0,0,0,0);
}

@media only screen and (max-width: 992px) {
  nav .brand-logo {
    font-size:15px;
    transform: translateX(0%);
    right: 0px;
    left: auto;
  }
  nav .brand-logo img {
    max-width:40px;
    max-height:40px;
  }
}

@media only screen and (max-width: 600px) {
  ::placeholder {
    color: transparent;
  }

  input.search-field {
    width: 1px;
    margin-right: 0px;
    padding: 8px 25px;
    border-bottom-right-radius: 0;
    border-top-right-radius: 0;
  }
  input.search-field ~ .search-popup {
    width: 1px;
    margin-right: 0px;
    padding: 8px 25px;
  }

  .search-icon {
    top: 0;
    padding-left: 15px;
    color: rgba(0, 0, 0, 0.54);
  }

  input.search-field:focus {
    margin-right: 0px;
    width: 100vw;
    padding: 8px 8px 8px 50px;
  }

  input.search-field:focus ~ .search-popup {
    width: 100vw;
  }

  .search-content {
    width: 100%;
    padding: 8px 8px;
  }

  nav .nav-wrapper {
    margin-right: 0px;
  }
}
</style>