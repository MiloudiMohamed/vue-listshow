# vue-listshow

![](https://img.shields.io/npm/v/vue-listshow.svg?label=version&colorB=blue&style=flat)
![](https://img.shields.io/npm/dt/vue-listshow.svg?style=flat)
![](https://img.shields.io/npm/l/vue-listshow.svg?style=flat)


vue-listshow is a Vue component to create a and display your lists in a beautiful sliding cards.

It's mainly inspired from  the [electronjs](https://electronjs.org/) releases cards


![alt text](/preview/vue-listshow.gif)

## Installation

#### Via YARN
```bash
yarn add vue-listshow
```

#### Via NPM
```bash
npm i vue-listshow
```

Then register it inside your component

```js
import VueListshow from 'vue-listshow'
...
components: {
    ...
    VueListshow,
}

```

## Usage
Now, what you have to do is to pass your array of objects as an `items` prop

and then you'll receive back each  object as an `item` property
```html
<vue-listshow :items="arrayList">
    <template slot-scope="{ item }">
        ...
    </template>
</vue-listshow>
```

You may refer to the [VueJs#scoped-slot](https://vuejs.org/guide/components-slots.html#Scoped-Slots-with-the-slot-scope-Attribute) docs for more information about how to use `scoped slots`

#### Note
By default no styles attached to the cards generated, so you should pass your own style through your `classes` prop
```html
<vue-listshow :items="arrayList" :classes="m-2 w-full bg-black text-grey-light rounded-lg">
    ...
</vue-listshow>
```

#### Available props:

| Prop           | Type     | Default | Required |
| -------------- | -------- | ------- | -------- |
| items          | Array    |   ---   |  true    |
| classes        | String   |   ---   |  false   |
| transition     | Number   |  300ms  |  false   |
| opacity        | Number   |  0.7    |  false   |

**Example of usuage**

```html
<vue-listshow
    :items="items"
    classes="m-2 w-full bg-black text-grey-light rounded-lg"
    :transition="400"
    :opacity=".8"
>
...
</vue-listshow>
```
## Issues and Contribution
If you find any bug or problem please open an issue or create a pull request, Thanks!.

## Licence
The MIT License (MIT). Please see License File for more information.
