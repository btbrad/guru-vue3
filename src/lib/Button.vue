<template>
  <button class="guru-button" :class="classes">
    <slot/>
  </button>
</template>

<script lang="ts">
import { defineComponent, computed, PropType } from 'vue'

export enum ButtonType {
  Default = 'default',
  Primary = 'primary',
  Danger = 'danger',
  Link = 'link'
}

export enum ButtonSize {
  Normal = 'normal',
  Small = 'small',
  Large = 'large'
}

export default defineComponent({
  name: 'Guru-Button',
  props: {
    size: {
      type: String as PropType<ButtonSize>,
      default: 'normal'
    },
    type: {
      type: String as PropType<ButtonType>,
      default: 'default'
    },
    disabled: {
      type: Boolean,
      default: false
    }
  },
  setup (props) {
    const { size, type, disabled } = props
    const classes = computed(() => {
      return {
        [`guru-${size}`]: size,
        [`guru-${type}`]: type,
        [`disabled`]: disabled
      }
    })
    return {
      classes
    }
  }
})
</script>

<style lang="scss" scoped>
@mixin button-size($padding-x, $padding-y, $font-size, $border-radius) {
  padding: $padding-y $padding-x;
  font-size: $font-size;
  border-radius: $border-radius;
}

@mixin button-style(
  $background,
  $border,
  $color,
  $hover-background: lighten($background, 7.5%),
  $hover-border: lighten($border, 10%),
  $hover-color: $color
) {
  color: $color;
  background: $background;
  border-color: $border;
  &:hover {
    color: $hover-color;
    background: $hover-background;
    border-color: $hover-border;
  }
  &:focus, &.focus {
    color: $hover-color;
    background: $hover-background;
    border-color: $hover-border;
  }
  &[disabled], &.disabled {
    color: $color;
    background: $background;
    border-color: $border;
  }
}


.guru-button {
  border: 1px solid #ccc;
  @include button-size($btn-padding-x, $btn-padding-y, $btn-font-size, $btn-border-radius);
  cursor: pointer;
  transition: $btn-transition;
  box-shadow: $btn-box-shadow;
  &:hover {
    background: $primary;
    color: #fff;
    border-color: #fff;
  }
  &.disabled, &[disabled] {
    cursor: not-allowed;
    opacity: $btn-disabled-opacity;
    box-shadow: none;
    pointer-events: none;
    > * {
      pointer-events: none; // no pointer event
    }
  }
  &.guru-large {
    @include button-size($btn-padding-x-lg, $btn-padding-y-lg, $btn-font-size-lg, $btn-border-radius-lg);
  }
  &.guru-small {
    @include button-size($btn-padding-x-sm, $btn-padding-y-sm, $btn-font-size-sm, $btn-border-radius-sm);
  }

  &.guru-primary {
    @include button-style($primary, $primary, $white);
  }
  &.guru-danger {
    @include button-style($danger, $danger, $white);
  }
  &.guru-default {
    @include button-style($white, $gray-400, $body-color);
  }

  &.guru-link {
    font-weight: $font-weight-normal;
    color: $btn-link-color !important;
    text-decoration: $link-decoration;
    border: none;
    box-shadow: none;
    background: none;
    &:hover {
      color: $btn-link-hover-color !important;
      text-decoration: $link-hover-decoration !important;
    }
    &:focus, &.focus {
      text-decoration: $link-hover-decoration !important;
      box-shadow: none;
    }
    &.disabled {
      color: $body-color !important;
      text-decoration: none !important;
    }
  }
}
</style>