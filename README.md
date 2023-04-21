Statamic GraphQL Issue

When you have multiple Bard/Replicator fields, the GraphQL endpoint seems to use only one for available sets on the others.

For example, this will give you an error that _Fragment cannot be spread here as objects of type "Sets_Blocks" can never be of type "Set_Blocks_OtherSample"._ However, if you update the Bard field in either collection to something other than `blocks`, the query works fine. This happens in any time of query, 1 or multiple entries. 
```graphql
{
  entry(collection: "blog_posts", slug: "test-entry") {
    title
    ... on Entry_BlogPosts_BlogPost {
      blocks {
        ... on BardText {
          type
          text
        }
        ... on Set_Blocks_Video {
          type
          url
        }
      }
    }
  }
  home: entry(collection: "pages", slug: "home") {
    title
    ... on Entry_Pages_Page {
      blocks {
        ... on BardText {
          type
          text
        }
        ... on Set_Blocks_OtherSample {
          type
          headline
        }
      }
    }
  }
}
```

Credentials:

test@example.com
password

