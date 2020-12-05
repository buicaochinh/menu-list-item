<template>
  <div class="wrapper">
    <div class="name" @click="toggle">{{ name }}</div>
    <transition name="item">
      <ul v-if="!hideChildren" class="list-item">
        <slot></slot>
      </ul>
    </transition>
  </div>
</template>

<script>
export default {
  name: "ListItem",
  props: {
    name: {
      type: String,
      default: "List Title"
    }
  },
  data() {
    return {
      hideChildren: true
    };
  },
  methods: {
    toggle() {
      this.hideChildren = !this.hideChildren;
    }
  }
};
</script>

<style scoped>
div.name {
  padding: 0.5rem 0.5rem;
  background-color: black;
  color: #fff;
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
