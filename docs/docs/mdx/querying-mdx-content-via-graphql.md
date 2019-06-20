---
title: "Querying MDX Content via GraphQL"
---

In order to query MDX content, it must be included in the node system using a source like the `gatsby-source-filesystem` plugin first. Instructions for sourcing content from somewhere like your `src/pages` directory can be found on the [filesystem plugin's README](/packages/gatsby-source-filesystem/).

Then, MDX files that are sourced via `gatsby-source-filesystem` can be queried via `allMdx` on the root query, like in this example query:

```graphql
query MDXQuery {
  allMdx {
    edges {
      node {
        parent {
          ... on File {
            name
            absolutePath
            relativePath
          }
        }
        timeToRead
        frontmatter {
          title
        }
      }
    }
  }
}
```

Like `gatsby-transformer-remark`, `gatsby-plugin-mdx` adds fields to the MDX node like `wordCount` and `timeToRead` for convenience.
The following fields are added to each MDX node:

- `frontmatter`
- `exports`
- `rawBody`
- `fileAbsolutePath`
- `code`
- `excerpt`
- `headings`
- `html`
- `tableOfContents`
- `timeToRead`
- `wordCount`

The `exports` field is unique in that all static exports – values that would be valid JSON – from a `.mdx` file are queryable
through it. Adding an export like this:

<!-- prettier-ignore -->
```mdx{1,3}:title=example.mdx
export const metadata = {
  name: "World",
}

# Title

Some content here
```

Allows `metadata` to be queried under the `exports` field. The name `metadata` isn't important, the values exported can be of whatever name you define.

```graphql{5-9}
query MDXQuery {
  allMdx {
    edges {
      node {
        exports {
          metadata {
            name
          }
        }
      }
    }
  }
}
```

> **Note**: all fields can also be found and [queried](/docs/introducing-graphiql/) in your site's generated GraphQL schema
