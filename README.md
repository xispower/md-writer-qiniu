# Markdown-Writer for Atom

Use [Atom](https://atom.io/) as a Markdown blogging editor. Great for [Jekyll](http://jekyllrb.com/), [Hexo](http://hexo.io/) and other static blogs.

![Insert Link](http://i.imgur.com/F9dLWsH.png)

## Features

- Dialog to **create new post**.
  In Command Palette (`shift-cmd-P`), type `Markdown Writer: New Post`.
- Dialog to **create new draft**.
  In Command Palette (`shift-cmd-P`), type `Markdown Writer: New Draft`.
- **Publish draft** moves current draft to `posts` directory. It updates `date` and rename the post using `title` in front matter.
  In Command Palette (`shift-cmd-P`), type `Markdown Writer: Publish Draft`.
- Dialog to **manage tags/categories in front matter**.
  In Command Palette (`shift-cmd-P`), type `Markdown Writer: Manage Post Tags/Categories`
- Dialog to **insert link (`cmd-k`) and automatically link to the text next time** (my favorite feature from Windows Live Writer).
  - Insert inline link by default
  - Insert reference link if title is specified
  - Remove link (and its reference) after URL is deleted
- Dialog to insert **image** with width, height auto-detected.
  In Command Palette (`shift-cmd-P`), type `Markdown Writer: Insert Image`
- **Toggle text styles**:
  - `code` (`cmd-'`)
  - **bold** (`cmd-b`)
  - _italic_ (`cmd-i`)
  - ~~strikethrough~~ (`cmd-h`)
  - `` ```codeblock``` `` (no default mapping, in Command Palette, type `Markdown Writer: Toggle Codeblock Text`)
- **Toggle headings**: `alt-[1-5]` to switch among `H1` to `H5`.

## Setup

You need to config markdown-writer to use most of the features.

Go to `Preferences` (`cmd-,`), search `markdown writer` package.

### Settings Explained:

- **siteLocalDir**: The root directory of blog/jekyll
- **siteDraftsDir**: The directory of drafts from the root of `siteLocalDir`. Default is `_draft/`.
- **sitePostsDir**: The directory of posts from the root of `siteLocalDir`. Default is `_posts/{year}`. You can also use `{year}`, `{month}` and `{day}`.
- **urlForTags**: The URL to tags `JSON` file. Refer to next section.
- **urlForPosts**: The URL to posts `JSON` file. Refer to next section.
- **urlForCategories**: The URL to categories `JSON` file. Refer to next section.

### Advance Settings:

To change these settings, open your Atom config file, find `markdown-writer` entry.

- **siteLinkPath**: Path to a `.cson` file that stores all links added for automatic linking next time.
  Default uses `markdown-writer-links.cson` in Atom's config directory.
- **frontMatter**: String of front matter generated in new post/draft.
- **codeblock**: Define the code block fences. Default uses GitHub's fenced code block.
- **imageTag**: Define the image tag inserted. Default uses `![alt](img-url)`.

This is an example of advance settings configuration:

```coffee
'markdown-writer':
  # sync the links in dropbox
  'siteLinkPath': '/Users/zhuochun/Dropbox/blog/links.cson'
  # add an author field in front matter
  'frontMatter': """
  ---
  layout: <layout>
  title: "<title>"
  author: zhuochun
  date: "<date>"
  ---
  """
  # use jekyll highlight code block, change this requires to reload plugin
  'codeblock':
    'before': '{% highlight %}\n'
    'after': '\n{% endhighlight %}'
    'regexBefore': '{% highlight(?: .+)? %}\n'
    'regexAfter': '\n{% endhighlight %}'
  # use img html tag
  'imageTag': '<img alt="<alt>" src="<src>" width="<width>" height="<height>" class="aligncenter" />'
```

## Populate Tags/Categories/Posts

![Manage Tags](http://i.imgur.com/amt2m0Y.png)

To **manage tags/categories in front matter**, you need to provide `JSON` files that list existing tags/categories/posts in your blog.

The `JSON` files contain following information of your blog:

```json
{
  "tags": ["tag a", "tag b", "..."],
  "categories": ["category a", "category b", "..."],
  "posts": [{"title": "title", "url": "url"}]
}
```

For **Jekyll** users, you can add [these scripts](https://gist.github.com/zhuochun/fe127356bcf8c07ae1fb) to your Jekyll directory and upload the generated `JSON` files.

For **Hexo** users, you can install [hexo-generator-atom-markdown-writer-meta](https://github.com/timnew/hexo-generator-atom-markdown-writer-meta) (Thanks to [@timnew](https://github.com/timnew)).

### TODOs

- Insert table
- Insert footnote
- Support multiple blog directories

View [CHANGELOG :notebook_with_decorative_cover:](https://github.com/zhuochun/md-writer/blob/master/CHANGELOG.md).

If you found any bug, please submit an issue [here :octocat:](https://github.com/zhuochun/md-writer/issues).

License in [MIT :unlock:](https://github.com/zhuochun/md-writer/blob/master/LICENSE.md).

## Tips

- Jumping among your posts: `Cmd-t` or `Cmd-p`.
- Markdown Preview: [markdown-preview](https://atom.io/packages/markdown-preview) package.
