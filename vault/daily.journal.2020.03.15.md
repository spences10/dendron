---
id: 947f40de-404c-487f-8fb1-253de1ae5d68
title: '2020-03-15'
desc: ''
updated: 1611437520307
created: 1611437351560
---

- Anyone able to aware me on if it's possible to use gatsby image for
  images from an API??

Say I want to cache the images from the Rick and Morty API:
https://rickandmortyapi-gql.now.sh/

```graphql
{
  characters {
    results {
      name
      image
    }
  }
}
```

- You can do that at build time using the
  createRemoteFilesomethingsomething API
- I wrote about it awhile ago
  (https://alexluong.com/blog/gatsby-image-sharp-from-url)
- Do you use the API to build Gatsby nodes or use
  gatsby-source-graphql?
- If you use the latter, you can use createResolver and then return
  the "createRemoteFileNode" node in the resolver function
- Do you have example code @alexluong? Or is this all covered in your
  blogpost?
- My post was written before createResolver was a thing, but it did
  cover the first use case. And to my knowledge, it's still
  applicable. I don't have example code for the second use case
  unfortunately. Do you know how you're pulling the data from the API
  into Gatsby yet?(edited)
- @ buitd-time with gatsby-source-graphql
- I am doing it at run-time too with useEffect:

  useEffect(() => { async function getRunTimeData() { const res =
  await axios({ url:
  'https://spotify-graphql-server.herokuapp.com/graphql', method:
  'post', data: { query:
  `{ queryArtists(byName:"Cyantific") { name id image albums { name image } } }`,
  }, }) const { data } = res.data setRunTimeData(data)
  setLoading(false) } getRunTimeData() }, [])

- This is a different example but I'd like to be able to do the same
  with that too
- This is just "half pseudo-code", but I think this is the approach:

// gatsby-node.js

```js
exports.createResolvers = ({ createResolvers }) => {
  const resolvers = {
    character: {
      imageFile: {
        resolve(source, args, context, info) {
          return createRemoteFileNode(source.image, etc)
        },
      },
    },
  }
  createResolvers(resolvers)
}
```

- As for the image at run-time, I don't think there's a good way to do
  that. I remembered @jlengstorf (Jason Lengstorf) did something
  similar-ish with Cloudinary, but I'm not entirely sure
- [13:27]
- This is what I'm referring to:
  https://gatsby-transformer-cloudinary.netlify.com/, but it seems
  like it's unrelated
- This is what I'm referring to:
  https://gatsby-transformer-cloudinary.netlify.com/, but it seems
  like it's unrelated
- @alexluong oh! Yeah! I was looking at this too, looks awesome! I saw
  it in reply to Wes Bos asking about better ways to process images
  with Gatsby as he was having issues with the images on his site he's
  moving to GatsbyJS

## Tags

[[gatsby.images]] [[gatsby]] [[graphql]]
