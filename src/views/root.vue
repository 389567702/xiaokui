<template>
  <div class="container">
    <h2>热电厂二期项目</h2>
    <div class="form-group">
      <input class="form-control gray" placeholder="搜索过滤建筑物名称">
    </div>

    <div class="content_container" v-for="building in buildings">
      <h3>{{ building.name }}</h3>
      <table class="table">
        <tr>
          <th>计划开始: </th>
          <th>计划完成: </th>
          <th>计划工期: </th>
          <th>已经施工: </th>
        </tr>
        <tr>
          <td>{{ building.start_date }}</td>
          <td>{{ building.end_date }}</td>
          <td>{{ building.total_duration }}天</td>
          <td>{{ building.total_elapsed }}天</td>
        </tr>
        <tr>
          <th colspan="2">实际进度</th>
          <td colspan=2 class="td_blue">{{ building.real_progress * 100 }}%</td>
        </tr>
        <tr>
          <td colspan=4>
            <div class="progress">
              <div class="progress-bar" role="progressbar" v-bind:aria-valuenow="building.real_progress * 100" aria-valuemin="0" aria-valuemax="100" v-bind:style="{width: building.real_progress * 100 + '%'}">
              </div>
            </div>
          </td>
         </tr>
         <tr>
          <th colspan="2">计划进度</th>
          <td colspan=2 class="td_blue">{{ building.plan_progress * 100 }}%</td>
         </tr>
         <tr>
          <td colspan=4>
                <div class="progress">
                  <div class="progress-bar" role="progressbar" v-bind:aria-valuenow="building.plan_progress * 100" aria-valuemin="0" aria-valuemax="100" v-bind:style="{width: building.plan_progress * 100 + '%'}">
                  </div>
                </div>
          </td>
         </tr>
      </table>

      <hr/>
      <div class="btn_container">
        <p>显示分部工程进度</p>
        <a v-on="click: onClick"  class="glyphicon glyphicon-menu-down">触发一个方法函数</a>
      </div>

      <div class="part_container">
        <h4>分布工程</h4>
        <div v-for="part in building.parts">
          <table class="table">
            <tr>
              <th>计划开始: </th>
              <th>计划完成: </th>
              <th>计划工期: </th>
              <th>已经施工: </th>
            </tr>
            <tr>
              <td>{{ part.start_date }}</td>
              <td>{{ part.end_date }}</td>
              <td>{{ part.total_duration }}天</td>
              <td>{{ part.total_elapsed }}天</td>
            </tr>
            <tr>
              <th colspan="2">实际进度</th>
              <td colspan=2 class="td_blue">{{ part.real_progress * 100 }}%</td>
            </tr>
            <tr>
              <td colspan=4>
                <div class="progress">
                  <div class="progress-bar" role="progressbar" v-bind:aria-valuenow="part.real_progress * 100" aria-valuemin="0" aria-valuemax="100" v-bind:style="{width: part.real_progress * 100 + '%'}">
                  </div>
                </div>
              </td>
            </tr>
            <tr>
              <th colspan="2">计划进度</th>
              <td colspan=2 class="td_blue">{{ part.plan_progress * 100 }}%</td>
            </tr>
            <tr>
              <td colspan=4>
                <div class="progress">
                  <div class="progress-bar" role="progressbar" v-bind:aria-valuenow="part.plan_progress * 100" aria-valuemin="0" aria-valuemax="100" v-bind:style="{width: part.plan_progress * 100 + '%'}">
                  </div>
                </div>
              </td>
            </tr>
          </table>
        </div>
      </div>
      <hr>
    </div>

<!--
    <div v-for="building in buildings">
      <h3>{{ building.name }}</h3>
      <ul class="gray">
        <li>计划开始: {{ building.start_date }}</li>
        <li>计划完成: {{ building.end_date }}</li>
        <li>计划工期: {{ building.total_duration }}</li>
        <li>已经施工: {{ building.total_elapsed }}</li>

        <li>下面两个做成进度条</li>
        <li>计划进度: {{ building.plan_progress }}</li>
        <li>实际进度: {{ building.real_progress }}</li>
      </ul>

      <h4>分布工程</h4>
      <ul>
        <li v-for="part in building.parts">
          <ul>
            <li>计划开始: {{ part.start_date }}</li>
            <li>计划完成: {{ part.end_date }}</li>
            <li>计划工期: {{ part.total_duration }}</li>
            <li>已经施工: {{ part.total_elapsed }}</li>

            <li>下面两个做成进度条</li>
            <li>计划进度: {{ part.plan_progress }}</li>
            <li>实际进度: {{ part.real_progress }}</li>
          </ul>
        </li>
      </ul>
      <hr>
    </div>
-->


  </div>
</template>

<script>
export default {
  props: ['db'],
  data () {
    let buildings = this.db.buildings

    return {
      buildings: buildings
    }
  },
  methods: {
      onClick: function (e) {

      }
    }
}
</script>
