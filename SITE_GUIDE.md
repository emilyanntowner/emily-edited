# Emily Edited - Site Management Guide

## Quick Start: Adding a New Post

### 1. Create the Post File
Create a new file in the `_posts/` directory with this naming format:
```
YYYY-MM-DD-post-title-slug.md
```

Example: `2025-06-10-understanding-anxiety.md`

### 2. Add Post Frontmatter
Start your file with this template:
```yaml
---
title: "Your Post Title Here"
date: 2025-06-10 10:00:00 +0100
layout: post
image: /assets/images/posts/2025/06/10/image-name.png
categories: [psychology]
tags: [anxiety, mental-health, coping-strategies]
---
```

### 3. Add Your Content
Write your post content below the frontmatter using Markdown:
```markdown
Your introduction paragraph here...

## First Section

Content here...

## Second Section

More content...
```

### 4. Add a Featured Image
1. Create the date-based folder structure in `assets/images/posts/`
   - Example: `assets/images/posts/2025/06/10/`
2. Add your image (recommended: 800px wide, PNG or JPG)
3. Name it based on your post slug (e.g., `understanding-anxiety.png`)

### 5. Test Locally
```bash
bundle exec jekyll serve
```
Visit http://localhost:4000/emily-edited/ to preview

### 6. Deploy
```bash
git add .
git commit -m "Add new post: Understanding Anxiety"
git push
```

## Categories & Tags

### Available Categories
Only use these 4 categories:
- `science`
- `psychology` 
- `neuroscience`
- `academia`

### Tag Guidelines
- Use descriptive, specific tags
- Separate multi-word tags with hyphens in URLs
- Example tags: `cognitive-bias`, `brain-health`, `research-methods`

## Common Tasks

### Update About Page
Edit `about.md` with your bio and information.

### Modify Site Title/Description
Edit `_config.yml`:
```yaml
title: Emily Edited
description: Science and Psychology.
```

### Change Social Links
Edit social links in `_config.yml` under `minima.social_links`.

## File Structure Overview

```
emily-edited/
├── _posts/              # Blog posts
├── _layouts/            # Page templates
├── _includes/           # Reusable components
├── _sass/minima/        # Custom styles
├── assets/images/posts/ # Post images
├── _config.yml          # Site configuration
├── index.md             # Homepage
├── posts.md             # Posts archive
└── about.md             # About page
```

## Image Guidelines

- **Size**: 800px width recommended
- **Format**: PNG or JPG
- **Location**: `/assets/images/posts/YYYY/MM/DD/image-name.png`
- **Naming**: Use post slug (e.g., `brain-reward-system.png`)

## Deployment

The site automatically deploys when you push to the `main` branch:
1. Make your changes
2. Commit and push to GitHub
3. GitHub Actions builds and deploys
4. Site updates at https://emilyanntowner.github.io/emily-edited/

## Tips

- **Preview excerpts**: First paragraph becomes the excerpt
- **Control excerpt length**: Add `<!--more-->` where you want to cut off
- **Draft posts**: Save in `_drafts/` folder (won't be published)
- **Schedule posts**: Use future dates - they won't appear until that date

## Troubleshooting

**Site not updating?**
- Check GitHub Actions tab for build errors
- Ensure post date isn't in the future
- Verify frontmatter formatting (proper YAML syntax)

**Images not showing?**
- Check file path matches exactly (case-sensitive)
- Ensure baseurl is included: `/emily-edited/assets/images/...`
- Verify image exists in the correct folder

**Categories not working?**
- Only use the 4 approved categories
- Check spelling (lowercase in frontmatter)
- Ensure square brackets are used: `[science, psychology]`

Need more help? Check the full documentation in CLAUDE.md.