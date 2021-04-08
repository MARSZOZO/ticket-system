<template>
  <div class="container">
    <div class="row">
      <div class="col">
        <router-view/>
      </div>
    </div>
  </div>
</template>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

body {
  background-color: #F4F4F4 !important;
}

table {
  font-size: 13px;
}

img {
  border-radius: 7px;
  margin-right: 10px;
}

.badge {
  font-size: .85em !important;
}

.priority-super-high{
	color: darkred;
}
.priority-high{
	color: red;
}
.priority-middle{
	color: green;
}
.priority-low {
	color: darkseagreen;
}

.status-new {
  color: #a9d86e
}
.status-processing {
  color: #ff6c60;
}
.status-postpone {
  color: #fcb322; 
}
.status-close {
  color: #bec3c7;
}

.modal-footer {
  justify-content: flex-start !important;
  border-top: none !important;
}

.btn-success {
  background-color: #78cd51 !important;
  border-color: #78cd51 !important;
  margin-right: 20px;
}
.btn-success:hover {
  background-color: #65ad44!important;
  border-color: #65ad44 !important;
}
.btn-danger {
  background-color: #f67a6e !important;
  border-color: #f67a6e !important;
}
.btn-danger:hover {
  background-color: #f76051 !important;
  border-color: #f76051!important;
}

.modal-header {
  border-bottom: none !important;
}
</style>
