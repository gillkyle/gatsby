---
title: "Interactive Code Blocks with MDX"
---

To make every markdown code block an editable live example, you can [pass in a custom `code` element](/docs/mdx/customizing-components/) to `MDXProvider` and use a library like [react-live](https://github.com/FormidableLabs/react-live) to preview code changes.

```javascript
import React, { Component } from "react"
import { LiveProvider, LiveEditor, LiveError, LivePreview } from "react-live"
import { MDXProvider } from "@mdx-js/react"

// a custom component to use in place of <code>
const MyCodeComponent = ({ children, ...props }) => (
  <LiveProvider code={children}>
    <LiveEditor />
    <LiveError />
    <LivePreview />
  </LiveProvider>
)

export default class MyPageLayout extends Component {
  render() {
    return (
      // highlight-next-line
      <MDXProvider components={{ code: MyCodeComponent }}>
        <div>{this.props.children}</div>
      </MDXProvider>
    )
  }
}
```

Then in an `mdx` file, using triple backticks will render your custom live code component and be editable:

````mdx
# Live Code Editor

```javascript
<span>You can edit me! :)</span>
```
````

## Other Resources

- [Egghead tutorial](https://egghead.io/lessons/react-create-a-live-code-component-with-gatsby-mdx-and-react-live) on building this example by Chris Biscardi
