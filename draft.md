---
title: Ruby on Rails Action Mailer Configuration
data: 2023-10-05
date: 2023-10-01
tags: ['action mailer']
---

# blogposts

repellat **earum**, **_sint ullam_** eaiure laboriosam amet ex tempora qui? Error? At corrupti sit
voluptates voluptas quidem. Accusamus consectetur eos facere doloribus odio id delectus repellendus!
Molestiae iste totam ratione, nihil culpa fuga illo! Nobis eveniet nostrum ab eaque porro laborum.
Quidem sequi eveniet suscipit dolorem quam eius praesentium id iste, corporis _labore_ quis ad
illum.

<CodeHeader text='TestComponent.tsx' />

<Video id='6ih_3m_UPKg' />

<CustomImage
  src='https://raw.githubusercontent.com/akladyous/blogposts/main/images/_redux.png'
  alt='Redux.JS'
/>

<CustomImage
  src='https://raw.githubusercontent.com/akladyous/blogposts/main/images/_react-js.png'
  alt='React.JS'
/>

```ts
export default async function BlogPosts() {
  console.group('Blog');
  const posts = await getPostsMeta('blogposts');
  if (!posts) {
    return <div>not posts</div>;
  }

  return (
    <main>
      <h4>Blog Post</h4>
      {posts.map((post, i) => {
        // debugger;
        return (
          <ul className='m-2' key={i}>
            {
              <li className='my-2'>
                <Link href={`blog/${post.id}`}>{post.title}</Link>
              </li>
            }
          </ul>
        );
      })}
    </main>
  );
}
```

<Video id='6ih_3m_UPKg' />

```ts
export default async function BlogPosts() {
  console.group('Blog');
  const posts = await getPostsMeta('blogposts');
  if (!posts) {
    return <div>not posts</div>;
  }

  return (
    <main>
      <h4>Blog Post</h4>
      {posts.map((post, i) => {
        // debugger;
        return (
          <ul className='m-2' key={i}>
            {
              <li className='my-2'>
                <Link href={`blog/${post.id}`}>{post.title}</Link>
              </li>
            }
          </ul>
        );
      })}
    </main>
  );
}
```

Lorem ipsum dolor sit amet, consectetur adipisicing elit. Tempora ducimus porro quidem, magni nisi
ad iure. Corrupti nisi reiciendis esse alias eveniet nostrum tempore ut! Doloremque labore magni
suscipit neque? At, officia! Quae temporibus suscipit nam omnis voluptatem dignissimos commodi illum
voluptatibus aperiam, alias, nihil in ipsam quia labore velit sint sit facere facilis aliquam quas
quaerat saepe amet optio. Ex pariatur eaque sapiente architecto neque exercitationem, fuga officia
saepe, ipsam quae incidunt corrupti, tempore maiores! Nobis similique.

Optionesciunt labore est consectetur ipsa architecto laboriosam ipsum, dolore voluptate neque
ratione nulla asperiores!.

Corrupti nisi reiciendis esse alias eveniet nostrum tempore ut! Doloremque labore magni suscipit
neque? At, officia! Quae temporibus suscipit nam omnis voluptatem dignissimos commodi illum
voluptatibus aperiam, alias, nihil in ipsam quia labore velit sint sit facere facilis aliquam quas
quaerat saepe amet optio. Ex pariatur eaque sapiente architecto neque exercitationem, fuga officia
saepe, ipsam quae incidunt corrupti, tempore maiores! Nobis similique, repellat earum, sint ullam ea
iure laboriosam amet ex tempora qui? Error? At corrupti sit voluptates voluptas quidem. Accusamus
consectetur eos facere doloribus odio id delectus repellendus! Molestiae iste totam ratione, nihil
culpa fuga illo! Nobis eveniet nostrum ab eaque porro laborum. Quidem sequi eveniet suscipit dolorem
quam eius praesentium id iste, corporis labore quis ad illum. Optio nesciunt labore est consectetur
ipsa architecto laboriosam ipsum, dolore voluptate neque ratione nulla asperiores!