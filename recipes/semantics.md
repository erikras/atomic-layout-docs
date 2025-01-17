# Semantics

Atomic layout values and encourages layout semantic. By default, components generated by the library will render `<div>` tags, which may not be a valid HTML element depending on your use case.

You can provide a custom HTML element or a React component to render instead of the default one by using [polymorphic prop](https://www.styled-components.com/docs/api#as-polymorphic-prop) `styled-components` feature.

{% hint style="info" %}
See [Polymorphic prop API](https://www.styled-components.com/docs/api#as-polymorphic-prop) ****in styled components' documentation.
{% endhint %}

## Using HTML element

To render a different HTML element provide its name as a value of the `as` prop of any component exported or generated by the library:

```jsx
import React from 'react'
import { Box } from 'atomic-layout'

const Header = (props) => (
  <Box as="header" {...props} />
)

export default Header
```

## Using React component

To render a custom React component provide its reference as a value to the `as` prop.

{% hint style="warning" %}
You must spread the props in your custom component to propagate class names generated by `styled-components`.
{% endhint %}

```jsx
import React from 'react'
import { Box } from 'atomic-layout'
import styled from 'styled-components'

const Header = (props) => (
  // Spreading the props assigns "className" (SC)
  // and the props from Atomic layout.
  <div {...props} />
)

const MyComponent = () => (
  <Box as={Header} height={50} padding={10} />
)

export default MyComponent
```

## Custom areas components

Polymorphic prop can be used on the generated areas components when using `Composition`.

```jsx
import React from 'react'
import { Composition } from 'atomic-layout'
import { Footer as CustomFooter } from '@components'

const PageContent = () => (
  <Composition as="main" areas="header footer">
    {({ Header, Footer }) => (
      <>
        <Header as="header">{...}</Header>
        <Footer as={CustomFooter}>{...}</Footer>
      </>
    )}
  </Composition>
)

export default PageContent
```

