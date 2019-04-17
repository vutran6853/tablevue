<template>
  <div class="fluid-container">
    <div class="form-group form-group-lg panel panel-default">
      <div class="panel-heading">
        <h3 class="panel-title">Sortable control</h3>
      </div>

      <div class="panel-body">
        <button type="button" class="btn btn-default" @click='orderList'>Sort by original order</button>
      </div>
    </div>

    <div class="col-md-3">
      <h3>Board Member</h3>
      <draggable class="list-group" tag="ul" v-model='list' v-bind='dragOptions' :move='onMove' @start='isDragging=true' @end='isDragging = false'>
        <transition-group type="transition" :name="'flip-list'">
          <li class="list-group-item" v-for="element in list" :key="element.order">
              {{ element.name }}
            <span class="badge">{{ element.order }}</span>
          </li>
        </transition-group>
      </draggable>
    </div>

    <div class="col-md-3">
      <h3>Table 2</h3>
      <draggable element="span" v-model='list2' v-bind='dragOptions' :move='onMove'>
        <transition-group name="no" class="list-group" tag="ul">
          <li class="list-group-item" v-for='element in list2' :key='element.order'>
              {{ element.name }}
            <span class="badge">{{ element.order }}</span>
          </li>
        </transition-group>
      </draggable>
    </div>

    <div class="list-group col-md-3">
      <pre>{{ listString }}</pre>
    </div>
    <div class="list-group col-md-3">
      <pre>{{ list2String }}</pre>
    </div>

  </div>
</template>

<script>
import draggable from "vuedraggable";

const boardMember1 = [
  {
    id: 1,
    name: "Vu",
  },
  {
    id: 2,
    name: "David"
  },
  {
    id: 3,
    name: "Sus"
  },
  {
    id: 4,
    name: "Paul"
  },
  {
    id: 5,
    name: "Fred"
  },
]

export default {
  name: "hello",
  components: {
    draggable
  },
  data() {
    return {
      list: boardMember1.map((value, index) => {
        console.log('name: ', value.name, index);
        return { name: value.name, order: index + 1, fixed: false };
      }),
      list2: [],
      isDragging: false,
      delayedDragging: false
    };
  },
  methods: {
    orderList() {
      this.list = this.list.sort((one, two) => {
        return one.order - two.order;
      });
    },
    onMove({ relatedContext, draggedContext }) {
      const relatedElement = relatedContext.element;
      const draggedElement = draggedContext.element;
      return (
        (!relatedElement || !relatedElement.fixed) && !draggedElement.fixed
      );
    }
  },
  computed: {
    dragOptions() {
      return {
        animation: 0,
        group: "description",
        ghostClass: "ghost"
      };
    },
    listString() {
      return JSON.stringify(this.list, null, 12);
    },
    list2String() {
      return JSON.stringify(this.list2, null, 12);
    }
  },
  watch: {
    isDragging(newValue) {
      if (newValue) {
        this.delayedDragging = true;
        return;
      }
      this.$nextTick(() => {
        this.delayedDragging = false;
      });
    }
  }
};
</script>

<style>
.flip-list-move {
  transition: transform 0.5s;
}

.no-move {
  transition: transform 0s;
}

.ghost {
  opacity: 0.5;
  background: #c8ebfb;
}

.list-group {
  min-height: 5rem;
  border: 3px solid red;
  display: flex;
  /* flex-direction: row; */
  justify-content: center;
}

.list-group-item {
  cursor: move;
  border: 3px solid blue;

  /* grid-auto-rows: auto auto */
  /* flex-direction: row; */
  /* flex-basis: 10px */

}

.list-group-item > i {
  cursor: pointer;
  color: gray;
}
</style>