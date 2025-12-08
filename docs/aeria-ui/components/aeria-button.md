<script setup lang="ts">
import { ref } from 'vue'
import { AeriaButton } from 'aeria-ui'
import ResultBox from '../../src/components/result-box.vue'

const count = ref(0)
</script>

# aeria-button

This component renders a styled button that will add style controls on top of [`aeria-bare-button`](/frontend/components/aeria-bare-button) functionalities. Buttons can have different sizes and variants and can also have loading and disabled states.

### Example

Will render a button that, when clicked, will increment the `count` variable. If `count` is greater than or equal to `10`, then the button is disabled.

<result-box title="Result">
  <aeria-button
    :disabled="count >= 10"
    @click="count++"
  >
    Increment
  </aeria-button>

  <template #result>
    {{ count }}
  </template>
</result-box>

```vue
<script setup lang="ts">
const count = ref(0)
</script>

<template>
  <aeria-button
    :disabled="count >= 10"
    @click="count++"
  >
    Increment
  </aeria-button>
</template>
```

### Props

- `dummy` <Badge type="tip" text="boolean?" />: Don't capture click events.
- `disabled` <Badge type="tip" text="boolean?" />: Disable click events.
- `loading` <Badge type="tip" text="boolean?" />: Sets button to load state. While in this state, clicking is disabled.

- `variant` <Badge type="tip" text="Size" /> <Badge type="tip" text="default: 'normal'" />: The variant of button styling. Accepted variants are:

```ts
type Variant =
  | 'primary'
  | 'alt'
  | 'transparent'
```

- `size` <Badge type="tip" text="Size" /> <Badge type="tip" text="default: 'medium'" />: The size the button should have. Accepted sizes are:

```ts
type Size = 
  | 'small'
  | 'medium'
  | 'large'
```

- `icon` <Badge type="tip" text="string?" />: The name of an icon from an icon library to be contained inside the button.
- `small` <Badge type="tip" text="boolean?" />: Shorthand property for `size: 'small'`.
- `large` <Badge type="tip" text="boolean?" />: Shorthand property for `size: 'large'`.

## Slots

- `default`: Content to be displayed inside the button.

## CSS overrides

- `--button-border-color: color;`: the color of the border of the button (default: `var(--theme-border-color)`)

