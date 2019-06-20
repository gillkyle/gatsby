---
title: Gatsby MDX API
---

Gatsby supports using MDX for adding the ability to embed components in markdown via `gatsby-plugin-mdx`. The MDX plugin is a fully featured MDX transformer, runtime, and ecosystem integration for ambitious projects. It integrates MDX with Gatsby to enable rich JAMStack applications. Using `gatsby-plugin-mdx`, you can build [interactive software documentation sites](/docs/mdx/interactive-code-blocks/), [apply design system components](/docs/mdx/customizing-components/) to rendered markdown, and more.

## Usage

To start working with Gatsby MDX, install the `gatsby-plugin-mdx` package as well as required dependencies `@mdx-js/mdx` and `@mdx-js/react`. Then, reference the `gatsby-plugin-mdx` package in your `gatsby-config.js` file.

```bash
npm install --save gatsby-plugin-mdx @mdx-js/mdx @mdx-js/react
```

```js:title=gatsby-config.js
module.exports = {
  plugins: [`gatsby-plugin-mdx`],
}
```

<GuideList slug={props.slug} />
