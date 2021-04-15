<template>
  <div class="arm-control">
    <label class="arm-control-label" :for="'arm-toggle-switch-' + _uid">
      <slot name="before"></slot>

      <input
        type="checkbox"
        class="arm-control-checkbox"
        :id="'arm-toggle-switch-' + _uid"
        v-model="value"
      />
      <div class="arm-control-toggle-switch">
        <span class="frame">
          <span class="key"></span>
        </span>
      </div>

      <slot></slot>
    </label>
  </div>
</template>

<script>
export default {
  name: "arm-toggleswitch",
  props: {
    checked: {
      type: Boolean,
      default: false,
    },
  },
  data: () => ({
    value: false,
  }),
  watch: {
    value: function (val) {
      this.$emit("toggle", val);
    },
  },
  mounted: function () {
    this.value = this.checked;
  },
};
</script>

<style scoped>
.arm-control .arm-control-checkbox {
  display: none;
}
.arm-control-toggle-switch {
  display: inline-block;
  vertical-align: middle;
  cursor: pointer;
  position: relative;
  width: 30px;
  height: 16px;
  margin: 0 3px;
}
.arm-control-toggle-switch .frame {
  background-color: #ccc;
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  -webkit-transition: 0.4s;
  -moz-transition: 0.4s;
  -o-transition: 0.4s;
  transition: 0.4s;

  border-radius: 16px;
}

.arm-control-toggle-switch .frame .key {
  background-color: #fff;
  position: absolute;
  width: 12px;
  height: 12px;
  left: 2px;
  bottom: 2px;
  -webkit-transition: 0.4s;
  -moz-transition: 0.4s;
  -o-transition: 0.4s;
  transition: 0.4s;

  border-radius: 50%;
}

input:checked + .arm-control-toggle-switch .frame {
  background-color: #444;
}

input:checked + .arm-control-toggle-switch .frame .key {
  -webkit-transform: translateX(14px);
  -moz-transform: translateX(14px);
  -ms-transform: translateX(14px);
  -o-transform: translateX(14px);
  transform: translateX(14px);
}
</style>
