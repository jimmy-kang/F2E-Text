<template>
  <div class="container">
    <div class="list">
      <div class="status">
        <div class="status-type">
          進行中
        </div>
      </div>
      <div v-for="order in orders" :key="order.name">
        <template v-if="order.status.code === 1 || order.status.code === 2">
          <div class="item">
            <div class="item-left">
              <img class="logo" v-bind:src="order.logo" />
            </div>
            <div class="item-middle">
              <div class="item-info">
                <div class="item-info-status-complete">
                  {{ order.status.type }}
                </div>
                預計出貨 : {{ order.date }}
              </div>
              {{ order.name }}
            </div>
            <div class="item-right">
              <div class="arrow right" />
            </div>
          </div>
        </template>
      </div>
    </div>
    <div class="list">
      <div class="status complete">
        <div class="status-type">
          已完成
        </div>
      </div>
      <div v-for="order in orders" :key="order.name">
        <template v-if="order.status.code === 3 || order.status.code === 4">
          <div class="item">
            <div class="item-left">
              <img class="logo complete" v-bind:src="order.logo" />
            </div>
            <div class="item-middle">
              <div class="item-info">
                {{ order.status.type }}
              </div>
              {{ order.name }}
            </div>
            <div class="item-right">
              <div class="arrow right" />
            </div>
          </div>
        </template>
      </div>
    </div>
  </div>
</template>


<script>
import { getOrders } from '../../utils/list.js'

export default {
  name: 'List',
  data() {
    return {
      orders: getOrders()
    };
  },
}
</script>

<style scoped>

.container {
  height: 100%;
  width: 100%;
}

.list {
  position: relative;
  width: 500px;
  margin: auto;
}

.status {
  position: relative;
  display: flex;
  align-items: center;
  width: 100%;
  height: 40px;
  border: 2px solid gray;
  background: rgba(0, 0, 0, 0.06);
  padding: 0 30px;
  box-sizing: border-box;
}

.status.complete {
  border-top: 0;
}

.status-type {
  font-weight: bold;
  margin-left: 15px;
}

.status-type::before {
  content:"";
  position: absolute;
  top: 0;
  bottom: 0;
  left: 30px;
  margin: auto;
  height: 20px;
  width: 5px;
  background-color: green;
}

.item {
  display: flex;
  padding: 25px 0;
  width: 100%;
  border: 2px solid gray;
  border-top: 0;
  box-sizing: border-box;
}

.item-left {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 160px;
}

.logo {
  height: 100px;
  width: 100px;
  background-size: 100%;
  margin: 5px 0;
}

.logo.complete {
  opacity: 0.6;
}

.item-middle {
  height: 100%;
  width: calc(100% - 160px - 80px);
}

.item-info {
  display: flex;
  margin-bottom: 10px;
  font-weight: 600;
  justify-content: space-between;
}

.item-info-status-complete {
  color: green;
}

.item-right {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 80px;
}

.arrow {
  border: solid black;
  border-width: 0 3px 3px 0;
  display: inline-block;
  padding: 8px;
}

.right {
  transform: rotate(-45deg);
  -webkit-transform: rotate(-45deg);
}

</style>
