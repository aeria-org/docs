<script setup lang="ts">
import { ref } from 'vue'
import { AeriaOptions } from 'aeria-ui'
import ResultBox from '../../src/components/result-box.vue'

const singleChoice = ref('a')
const multipleChoice = ref([])
</script>

# aeria-options

This component renders a group of checkboxes (or radio inputs) depending on the property type.

### Example

A radio-style option list.

<result-box title="Single choice">
  <aeria-options
    v-model="singleChoice"
    :property="{
      enum: [
        'a',
        'b',
        'c',
      ]
    }"
  ></aeria-options>

  <template #result>
    {{ singleChoice }}
  </template>
</result-box>

```vue
<script setup lang="ts">
const choice = ref('')
</script>

<template>
  <aeria-options
    v-model="choice"
    :property="{
      enum: [
        'a',
        'b',
        'c',
      ]
    }"
  ></aeria-options>
  <pre>Single choice: {{ choice }}</pre>
</template>
```

---

A select-style option list. Picked options will be appended to the beggining of the `choice` array.

<result-box title="Multiple choice">
  <aeria-options
    v-model="multipleChoice"
    :property="{
      type: 'array',
      items: {
        enum: [
          'a',
          'b',
          'c',
        ]
      }
    }"
  ></aeria-options>

  <template #result>
    {{ multipleChoice }}
  </template>
</result-box>


```vue
<script setup lang="ts">
const choice = ref([])
</script>

<template>
  <aeria-options
    v-model="choice"
    :property="{
      type: 'array',
      items: {
        enum: [
          'a',
          'b',
          'c',
        ]
      }
    }"
  ></aeria-options>
  <pre>Multiple choice: {{ choice }}</pre>
</template>
```

