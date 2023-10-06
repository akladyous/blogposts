---
title: The Art of Web Development
date: 2023-10-01
tags: [javascript, frontend]
---

# blogposts

Lorem ipsum dolor sit amet, consectetur adipisicing elit. Tempora ducimus porro quidem, magni nisi
ad iure.

```js
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
