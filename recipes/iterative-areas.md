# Iterative areas

A single template area may be rendered multiple types, for example during the iteration of a list items rendering.

```jsx
import React from 'react'
import { Composition } from 'atomic-layout'

const List = ({ items }) => (
  <Composition areas="column" gutter={10}>
    {({ Column }) => items.map((item) => (
      <Column key={item.id} col="auto">{item}</Column> 
    ))}
  </Composition>
)

export default List
```

{% hint style="success" %}
By setting `row` and `col` props to "auto" you enable the auto-placing algorithm.
{% endhint %}

