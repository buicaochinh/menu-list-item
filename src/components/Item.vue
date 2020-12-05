<template>
  <li>
    <div v-if="!isLeaf" class="wrapper-li">
      <div class="value" @click="toggleChild">{{ value }}</div>
      <transition name="item">
        <ul v-if="!hideChildren" class="list-sub-items">
          <slot></slot>
        </ul>
      </transition>
    </div>
    <div v-if="isLeaf" class="value">{{ value }}</div>
  </li>
</template>

<script>
export default {
  name: "Item",
  props: {
    value: {
      type: String,
      default: "Item"
    },
    isLeaf: {
      type: Boolean,
      default: false
    }
  },
  data() {
    return {
      hideChildren: true
    };
  },
  methods: {
    toggleChild() {
      this.hideChildren = !this.hideChildren;
    }
  }
};
</script>

<style scoped>
li {
  padding-left: 10px;
}

div.value {
  padding: 0.5rem 0.5rem;
}

.item-enter {
  /*transform: translateY(0px);*/
}

.item-enter-active {
  animation: slide-in 0.1s ease-out forwards;
}

.item-leave {
}

.item-leave-active {
  animation: slide-out 0.1s ease-out forwards;
}

@keyframes slide-in {
  from {
    transform: translateY(-20px);
  }
  to {
    transform: translateY(0px);
  }
}

@keyframes slide-out {
  from {
    transform: translateY(0px);
  }
  to {
    transform: translateY(-20px);
  }
}
</style>
