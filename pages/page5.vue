<template>
  <div>Page 5</div>

  <div>
    <button @click="handleButtonClick">hello</button>
    <Comp class="font-semibold" :v="val"></Comp>
    <Comp2 class="font-semibold" :v="val"></Comp2>
    <div>
      {{ val }}
    </div>
  </div>
</template>

<script setup lang="ts">
import { defineComponent, h, ref } from 'vue';
import SlowComponent from '../components/SlowComponent.vue';

const val = ref();

const Comp = defineComponent({
  props: {
    v: {
      type: String,
      required: false,
    },
  },
  setup(props, context) {
    console.log('Comp');
    console.log(props);
    return () =>
      h(
        SlowComponent,
        {
          ...props,
          ...context.attrs,
        },
        () => [
          context.slots.default ? context.slots.default() : props.v,
          h(SlowComponent, null, () => 'ABC'),
        ]
      );
  },
});

const Comp2 = (props, context) => {
  console.log('Comp2');
  console.log(props);
  console.log(context);
  return h(
    SlowComponent,
    {
      ...props,
    },
    () => [
      context.slots.default ? context.slots.default() : props.v,
      h(SlowComponent, null, () => 'ABC'),
      h('div', null, [
        h('input', {
          value: props.v,
        }),
        props.v,
      ]),
    ]
  );
};

function handleButtonClick() {
  val.value = new Date().getTime().toString();
}
</script>
