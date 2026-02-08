# Blog Publishing Guide

This guide explains how to add, edit, and manage blog posts on this Jekyll-based site.

## File Structure

```
├── blog.html                 # Blog listing page (serves at /blog)
├── posts/                    # All blog post markdown files
│   └── my-post.md
├── _data/
│   └── posts.yml             # Registry of posts shown on blog listing
├── _layouts/
│   ├── posts.html            # Layout for the blog listing page
│   └── post.html             # Layout for individual blog posts
└── media/                    # Images and media for blog posts
```

## Adding a New Blog Post

### Step 1: Create the Markdown File

Create a new `.md` file in the `posts/` folder. The filename becomes the URL slug.

**Example:** `posts/my-new-article.md` → accessible at `/posts/my-new-article`

### Step 2: Add Front Matter

Every post must start with YAML front matter:

```yaml
---
layout: post
title: Your Post Title
sub_title: A brief subtitle or description
read_time: 5
date: Jan 2025
featured_image: https://yourdomain.com/media/image.png
---
```

| Field | Required | Description |
|-------|----------|-------------|
| `layout` | Yes | Always use `post` |
| `title` | Yes | The main title displayed on the page |
| `sub_title` | No | Subtitle shown below the title |
| `read_time` | Yes | Estimated reading time in minutes |
| `date` | Yes | Display date (e.g., "Jan 2025", "Dec 2024") |
| `featured_image` | No | URL for social sharing preview image |

### Step 3: Write Your Content

Below the front matter, write your post content in Markdown:

```markdown
---
layout: post
title: My Post Title
sub_title: A subtitle
read_time: 5
date: Jan 2025
featured_image: https://example.com/image.png
---

![Header Image](/media/my-image.png)

Introduction paragraph here...

## Section Heading

More content...

### Subsection

- Bullet points
- Work like this

```javascript
// Code blocks are supported
const example = "hello";
```
```

### Step 4: Register the Post

Add an entry to `_data/posts.yml` to display the post on the blog listing page:

```yaml
- title: My Post Title
  link: my-new-article
  date: Jan 2025
```

**Important:** The `link` value must exactly match the filename (without `.md`).

## Adding Images

1. Place images in the `media/` folder
2. Reference them in your post: `![Alt text](/media/your-image.png)`
3. For featured images, use the full URL in front matter

## Optional Front Matter Fields

```yaml
---
layout: post
title: Your Title
sub_title: Subtitle
read_time: 10
date: Feb 2025
featured_image: https://yourdomain.com/media/image.png
image-theme: dark          # Add 'dark' class to main element
updated: March 2025        # Shows "Updated March 2025" on the post
synopsis: Brief summary    # Used for meta description
---
```

## Editing Existing Posts

1. Find the post in `posts/` folder
2. Edit the markdown content
3. Update `_data/posts.yml` if title or date changed
4. Jekyll will regenerate the site on next build

## Removing a Post

1. Delete the `.md` file from `posts/`
2. Remove the corresponding entry from `_data/posts.yml`

## Local Development

```bash
# Install Jekyll (if not installed)
gem install bundler jekyll

# Run local server
bundle exec jekyll serve

# Site will be available at http://localhost:4000
```

## Deployment

The site auto-deploys via GitHub Pages when changes are pushed to the main branch.

## Troubleshooting

| Issue | Solution |
|-------|----------|
| Post not showing on /blog | Check that `_data/posts.yml` has the correct `link` value |
| 404 on post URL | Verify filename matches the `link` in posts.yml |
| Images not loading | Ensure images are in `media/` and path starts with `/media/` |
| Formatting issues | Check for unclosed code blocks or markdown syntax errors |
