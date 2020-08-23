# Vue Dropdown

A dropdown component for Vue 2.x.

## Install

``` bash
npm install @codinglabs/vue-dropdown --save
```

In your app.js:
``` javascript
import Vue from 'vue'
import Dropdown from '@codinglabs/vue-dropdown';

Vue.use(Dropdown)
```
## Basic Usage

``` html
<dropdown text="Menu">
    <dropdown-item href="/settings">Settings</dropdown-item>
    <dropdown-item href="#">Logout</dropdown-item>
</dropdown>
```

## Slots
#####button
Replaces the button entirely
``` html
<dropdown ref="dropdown">
    <button slot="button" class="flex items-center" @click="handleClick">
        <div class="mr-2">Menu</div>
        <i class="fas fa-caret-down"></i>
    </button>
</dropdown>
```
Note: if you replace the button entirely you will need to manually handle the toggling of the dropdown via a ref to the dropdown component e.g. `this.$refs.dropdown.toggle()`

#####button-content
Replaces the content inside the button
``` html
<dropdown>
    <div slot="button-content" class="p-2">
        <i class="fas fa-ellipsis-h"></i>
    </div>
</dropdown>
```

## Props
**Dropdown**
| Prop        | Type   | Default   | Description |
| ----------- | ------ | --------- | ----------- |
| text        | String | "Options" | Button text
| textClasses | String | -         | String containing space separeted classes to style button text
| menuClasses | String | -         | String containing space separated classes to style menu dropdown

**Dropdown Item**
| Prop    | Type    | Default | Description |
| ------- | ------- | ------- | ----------- |
| href    | String  | ''      | Url to redirect to. 
| inertia | Boolean | false   | Calls $inertia.visit() using the provided href instead of a normal redirect

## Events
**Dropdown Item**
| Event | Description |
| ----- | ----------- |
| @click | Dropdown item has been clicked. 

## Styling
This plugin uses [Tailwindcss](https://tailwindcss.com/) classes by default. If you would prefer to use your own classes then you can override them using the **textClasses** and **menuClasses** props on the dropdown component.

## About Coding Labs
Coding Labs is a web app development agency based on the Gold Coast, Australia. 

## License
The MIT License (MIT). Please see [License File](LICENSE) for more information.
