<template>
  <div class="door-area" @click="$emit('onSelect', number)">
    <div class="door-frame" :class="{ selected: isSelect && !isOpen }">
      <gift-box v-if="isOpen && hasGift"></gift-box>
    </div>
    <div class="door" :class="{ open: isOpen }">
      <div class="number" :class="{ selected: isSelect }">{{ number }}</div>
      <div
        class="knob"
        :class="{ selected: isSelect }"
        @click.stop="
          () => {
            if (isSelect) {
              $emit('onOpen', hasGift, number);
            }
          }
        "
      ></div>
    </div>
  </div>
</template>

<script>
import GiftBox from "./GiftBox.vue";
export default {
  name: "DoorGift",
  components: { GiftBox },
  props: {
    number: {},
    hasGift: {
      type: Boolean,
      default: false,
    },
    isSelect: {
      type: Boolean,
      default: false,
    },
    isOpen: {
      type: Boolean,
      default: false,
    },
  },
};
</script>

<style>
:root {
  --door-border: 5px solid brown;
  --selected-border: 5px solid #fff;
}

.door-area {
  position: relative;
  width: 200px;
  height: 310px;
  border-bottom: 10px solid #aaa;
  margin-bottom: 20px;
  font-size: 3rem;

  display: flex;
  justify-content: center;
}

.door-frame {
  position: absolute;
  height: 300px;
  width: 180px;

  border-left: var(--door-border);
  border-top: var(--door-border);
  border-right: var(--door-border);
  display: flex;
  justify-content: center;
  align-items: flex-end;
}

.door {
  position: absolute;
  top: 5px;
  height: 295px;
  width: 170px;
  background-color: chocolate;

  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 20px;
}

.door.open {
  background-color: #fff3;
}

.door .number {
  color: brown;
}

.door .number.selected {
  color: #fff;
}

.door .knob {
  height: 20px;
  width: 20px;
  border-radius: 50%;
  background-color: brown;
  align-self: flex-start;
  margin-top: 60px;
}

.door-frame.selected {
  border-left: var(--selected-border);
  border-top: var(--selected-border);
  border-right: var(--selected-border);
}

.door .knob.selected {
  background-color: #fff;
}

.door.open .knob,
.door.open .number {
  background-color: #fff0;
  color: #fff0;
}
</style>
