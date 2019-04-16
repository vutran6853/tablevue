<template>
  <div class="">
    <!-- <div class="h3Box" >
      <h3 v-for='newHeader in header' >
        {{ newHeader }}
      </h3>
    </div>

     <div class="innderBox" @click='handleClickRow($event)'>
        <ul v-for='newRow in row' >
          <li>{{ newRow }}</li>
        </ul>
      </div>

    <div v-if='this.isRowClick === true' class="innderBoxs">
        <select>
          <option value="value1">value1</option>
          <option value="value2">value2</option>
          <option value="value3">value3</option>
          <option value="value4">value4</option>
        </select>
    </div>
    <div v-else=''>
      <p>false</p>
    </div> -->



<div class="grid-container" @click='handleClickRow($event)'>
  <div class="grid-item">1</div>
  <div class="grid-item">2</div>
  <div class="grid-item">3</div>  
  <div class="grid-item">4</div>
  <div class="grid-item">5</div>
  <div class="grid-item">6</div>  
  <div class="grid-item">7</div>
  <div class="grid-item">8</div>
  <div class="grid-item">9</div>  
</div>

    <!-- <table @click='handleClickRow($event)'>
      <tr >
        <th>First Name</th>
        <th>Last Name</th>
        <th>Points</th>
      </tr>
      <tr>
        <td>Peter</td>
        <td>Griffin</td>
        <td>$100</td>
      </tr>
      <tr>
        <td>Lois</td>
        <td>Griffin</td>
        <td>$150</td>
      </tr>
      <tr>
        <td>Joe</td>
        <td>Swanson</td>
        <td>$300</td>
      </tr>
      <tr>
        <td>Cleveland</td>
        <td>Brown</td>
        <td>$250</td>
      </tr>
    </table>


        <div v-if='this.isRowClick === true' class="innderBoxs">
        <select>
          <option value="value1">value1</option>
          <option value="value2">value2</option>
          <option value="value3">value3</option>
          <option value="value4">value4</option>
        </select>
    </div>
    <div v-else=''>
      <p>false</p>
    </div> -->
  </div>
</template>

<script>
export default {
  name: 'ShowRow',
  data() {
    return {
      header: ['col 1', 'col 2', 'col 3', 'col 4', 'col 5'],
      row: ['row 1', 'row 2', 'row 3', 'row 4', 'row 5'],
      isRowClick: false
    }
  },
  methods: {
    handleClickRow(event) {
      console.log('event', event.srcElement.className);

      if(event.srcElement.className === 'grid-item') {
        console.log('grid-item', true);
      }

      
      console.log(this.isRowClick);
      if(!this.isRowClick) {
        console.log(true, this.isRowClick);
        this.isRowClick = true
      } else {
        this.isRowClick = !this.isRowClick
      }
    }
  }
}
</script>

<style>

.grid-container {
  display: grid;
  grid-row-gap: 50px;
  grid-template-columns: auto auto auto;
  background-color: #2196F3;
  padding: 10px;
}

.grid-item {
  background-color: rgba(255, 255, 255, 0.8);
  border: 1px solid rgba(0, 0, 0, 0.8);
  padding: 20px;
  font-size: 30px;
  text-align: center;
  border: 5px solid red;

}

.h3Box {
  display: grid;
  grid-column-gap: 50px;
  grid-template-columns: auto auto auto auto auto;
  background-color: #2196F3;
  padding: 10px;
  border: 5px solid yellow;
}

.innderBox {
  display: grid;
  grid-column-gap: 50px;
  grid-template-columns: auto auto auto auto auto;
  /* grid-auto-rows: auto auto auto auto auto; */
  background-color: #2196F3;
  /* padding: 10px; */
  border: 5px solid red;
}

table {
  border-collapse: collapse;
  width: 100%;
}

th, td {
  text-align: left;
  padding: 8px;
}

tr:nth-child(even) {
  background-color: #f2f2f2;
}
</style>
