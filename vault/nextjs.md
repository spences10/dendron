---
id: aa9e1c96-14cf-4a98-bf3a-77c1c741139f
title: NextJS
desc: ''
updated: 1611600302157
created: 1611259769209
---

## Data Fetching

Runs at build time: `getStaticProps` (Static Generation): Fetch data
at **build time**.

Runs on render: `getStaticPaths` (Static Generation): Specify dynamic
routes to pre-render based on data.

Runs on refresh: `getServerSideProps` (Server-side Rendering): Fetch
data on each request.

## Example of having nested routes

This is for when you want to have dynamic routes that are more than a
`posts/[slug].js` path, so what do I mean by that, lets take a look at
the typical file structure on the Next.js example sites:

```text
next-js-project/
├─ content/
│  ├─ post-one.md
│  ├─ post-two.md
│  └─ post-three.md
├─ pages/
│  ├─ posts/[slug].js
│  └─ index.js
```

That will give you the path to the files like:

```text
localhost:3000/posts/post-one
localhost:3000/posts/ost-two
localhost:3000/posts/post-three
```

That's fine n' all but what if you have content you want to link with
your Markdown posts like images, that content folder will get a bit
difficult to reason about once you get a lot of content in there.

With Gatsby I have always done a file structure in this format:

```text
content/posts/yyyy/mm/dd/post-title/index.mdx
```

So I went about trying to do that with the Next.js examples.

Thanks to [Eka] in the Party Corgi Discord for pointing out the
section in the [basic features] of the Next.js documentation, it
wasn't entirely clear to me what **catch all routes** was.

:`lib/posts.js`

```js
import globby from 'globby'

const postsDirectory = './content/posts'

export async function getPostPaths() {
  const files = await globby(postsDirectory, {
    expandDirectories: { extensions: ['md*'] },
  })

  return await files
}

export async function getPostSlugs() {
  const files = await getPostPaths()

  const paths = files.map(path => {
    const split = path.split(`/`)
    // remove `content/posts` and `index.md*`
    const removedIndexFile = split.splice(2, split.length - 3)

    return {
      params: {
        slug: removedIndexFile,
      },
    }
  })

  return {
    paths,
    fa,
  }
}
```

:`pages/[...slug].js`

```js
import { getPostSlugs } from '../lib/posts'

export default function Post({ slug }) {
  console.log('=====================')
  console.log(`slug::: ${slug}`)
  console.log('=====================')
  return <Layout>yo</Layout>
}

export const getStaticPaths = async () => {
  return await getPostSlugs()
}

export const getStaticProps = async ({ params: { slug } }) => {
  return {
    props: { slug },
  }
}
```

<!-- Links -->

[eka]: https://github.com/ekafyi
[basic features]:
  https://nextjs.org/docs/basic-features/data-fetching#the-paths-key-required
