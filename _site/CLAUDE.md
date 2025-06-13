# Emily's Jekyll Blog - Development Documentation

This file provides comprehensive guidance for Claude Code and other developers working on this Jekyll blog project.

## Project Overview

A custom Jekyll blog built on Minima v3 theme with extensive customizations for academic and scientific content. Features responsive design, custom layouts, and specialized styling for research-focused content.

## Development Commands

```bash
# Install dependencies
bundle install

# Run development server with live reload (default: http://localhost:4000)
bundle exec jekyll serve

# Build the site for production
bundle exec jekyll build

# Serve with drafts visible
bundle exec jekyll serve --drafts
```

## Architecture

### Key Files & Their Purpose

**Configuration**
- `_config.yml` - Jekyll site configuration
- `Gemfile` - Ruby dependencies

**Layouts** (`_layouts/`)
- `post.html` - Individual blog posts with featured images and metadata
- `archive.html` - Category archive pages 
- `gallery.html` - Homepage grid layout

**Includes** (`_includes/`)
- `header.html` - Custom navigation with fixed category links and social icons
- `sidebar.html` - Posts page sidebar with categories/tags
- `footer.html` - Site footer with copyright notice
- `social-icons/` - Custom SVG icons (Web/Globe, Bluesky, Donation, Layers)

**Styling** (`_sass/minima/`)
- `custom-styles.scss` - Main custom styles (1400+ lines, organized by component)
- `custom-variables.scss` - SCSS variables and typography scales

**Content**
- `_posts/` - Blog posts in markdown format
- `assets/images/posts/` - Featured images organized by date
- `index.md` - Homepage using gallery layout
- `posts.md` - Posts archive page
- `about.md` - About page

### Theme Customization
- Base theme: Minima v3 with extensive overrides
- Typography: Lato (body) + Caveat (site title) fonts
- Custom base font size: 14px
- Responsive design with mobile-first approach

## Custom Features Implemented

### Navigation System
- **Desktop**: Horizontal category links in centered header with social icons
- **Mobile**: Progressive text sizing with centered navigation and footer
- **Categories**: Reduced to 4 core categories: science, psychology, neuroscience, academia
- **Social Icons**: Website (globe), Instagram, TikTok, YouTube, Bluesky, Support links
- **Responsive breakpoints**: 1200px, 900px, 600px with progressive text sizing

### Category System
- **Core Categories**: science, psychology, neuroscience, academia (reduced from 9 to 4)
- **Storage**: Lowercase in frontmatter, display converts to uppercase
- **Functionality**: Clickable category buttons throughout site link to archive pages
- **Archive Pages**: Dedicated filtered views for each category (tags removed from display)

### Post Layout Features
- **Featured Images**: Support with proper positioning and responsive sizing
- **Metadata**: Author/date line with proper styling
- **Category & Tags**: Category on left, tags on right of same line (individual posts only)
- **Tag Links**: Properly slugified URLs (e.g., /tags/scientific-thinking/)
- **Separators**: Horizontal line after category/tags section
- **Responsive Design**: Optimized for all screen sizes

### Homepage Gallery
- **CSS Grid**: 8-item layout with strategic positioning
- **Featured Post**: item-1 gets larger size and prominence
- **Layout Order**: Image, title, author/date, category, excerpt
- **Excerpt Lengths**: Post 1 (50 words), Post 2 (25 words), Posts 3+ (15 words)
- **Tight Spacing**: Negative margins pull titles closer to images (-0.5rem)
- **Responsive**: Collapses to single column on mobile

### Footer Enhancements
- **Copyright Notice**: Centered at bottom with proper styling
- **Mobile Centering**: All footer elements centered on mobile widths
- **Social Icons**: Updated to include website globe icon and layers icon

### Navigation Improvements (Recent)
- **Removed**: Complex hamburger menu that had multiple issues
- **Implemented**: Progressive text sizing approach
- **Benefits**: Better mobile UX, cleaner code, consistent behavior
- **Breakpoints**: 
  - 1200px: 0.7rem text
  - 900px: 0.65rem text  
  - 600px: 0.6rem text with layout adjustments

## Styling Architecture

### SCSS Organization (`custom-styles.scss`)
1. **Typography & Site-wide Styles** (lines 1-91)
   - Base font sizing, heading hierarchies, global link styles
2. **Header & Navigation** (lines 92-277) 
   - Centered header layout, responsive navigation, social icons
3. **Sidebar Components** (lines 278-419)
   - Sidebar styling, categories, tags, recent posts
4. **Posts Page** (lines 420-797)
   - Posts listing layout, featured images, metadata styling
5. **Archive Pages** (lines 798-997)
   - Category archive layouts, post previews
6. **Homepage Gallery Layout** (lines 998-1165)
   - CSS Grid implementation, responsive gallery
7. **Individual Post Styling** (lines 1166-1263)
   - Single post layout, featured images, content styling
8. **Responsive Design** (lines 1264-1405)
   - Mobile breakpoints, responsive adjustments

### Key CSS Classes
- `.homepage-grid` - Main gallery grid container
- `.posts-list` - Posts archive layout
- `.post-featured-image` - Featured image containers
- `.category` - Category button styling (dark background, white text)
- `.posts-author-date` - Metadata line styling
- `.site-nav` - Navigation container with responsive behavior
- `.footer-newsletter` - Newsletter subscription form container
- `.embeddable-buttondown-form` - Buttondown form styling

### Responsive Strategy
- **Mobile-First**: Base styles for mobile, enhanced for larger screens
- **Progressive Enhancement**: Features added at larger breakpoints
- **No Hamburger Menu**: Text sizing approach for better UX
- **Flexible Layouts**: Adapt gracefully to any screen size

## Content Guidelines

### Post Frontmatter
```yaml
---
title: "Post Title"
date: YYYY-MM-DD HH:MM:SS +0100
layout: post
image: /assets/images/posts/YYYY/MM/DD/slug/image.png
categories: [category1, category2]
tags: [tag1, tag2]
---
```

### Image Organization
- **Path Structure**: `/assets/images/posts/YYYY/MM/DD/image-name.png`
- **Recommended Size**: 800px width for featured images
- **Formats**: PNG or JPG, optimized for web
- **Naming**: Use post slug as filename (e.g., `brain-reward-system.png`)

### Category Usage
- **Format**: Use lowercase in frontmatter: `[science, psychology]`
- **Limitation**: Stick to the 4 core academic categories: science, psychology, neuroscience, academia
- **Linking**: First category used for archive page links
- **Display**: Automatically converts to uppercase in templates

### Tag Usage
- **Format**: Use descriptive tags in frontmatter: `[dopamine, motivation, behavior]`
- **Display**: Only shown on individual post pages (not on archive pages)
- **Linking**: Automatically creates proper slugified URLs
- **Multi-word**: Use spaces in frontmatter, they'll be converted to hyphens in URLs

## Recent Major Changes

### GitHub Actions Deployment (Latest)
- **Added GitHub Actions Workflow**: Created `.github/workflows/deploy.yml` for automated deployment
- **Ruby Version**: Using Ruby 3.2 for compatibility with sass-embedded
- **Deployment Method**: Changed from branch-based to GitHub Actions deployment
- **Benefits**: Allows using Jekyll 4.4.1 and Minima v3 on GitHub Pages

### Site Structure Updates (Latest)
- **Fixed CSS Import**: Updated to Minima v3 syntax (`@import "minima/skins/classic", "minima/initialize"`)
- **Baseurl Configuration**: Set to `/emily-edited` for proper GitHub Pages deployment
- **Archive Excerpt Fix**: Changed `site.minima.show_excerpts` to `site.show_excerpts` in archive layout
- **Created Site Guide**: Added `SITE_GUIDE.md` for easy content management

### Homepage Gallery Redesign
- **Layout Order**: Changed to image, title, author/date, category, excerpt
- **Spacing Optimization**: Negative margins (-0.5rem) for tighter image-title connection
- **Smart Excerpts**: Variable word limits (50/25/15) based on post position
- **Visual Hierarchy**: Improved content flow and readability

### Navigation & Social Integration
- **Category Reduction**: Streamlined from 9 to 4 core categories
- **Social Icons**: Added website globe icon and updated footer layers icon
- **Mobile Centering**: Improved navigation and footer alignment on mobile
- **Progressive Sizing**: Maintained responsive text scaling approach

### Tag System Implementation
- **Individual Posts**: Added tags display alongside categories
- **Proper Slugification**: Fixed multi-word tag URLs (scientific-thinking vs scientific%20thinking)
- **Archive Cleanup**: Removed tag display from category/archive pages
- **URL Structure**: Consistent /tags/tag-name/ format

### Footer & Copyright
- **Copyright Notice**: Added centered "Copyright © 2025 · Emily Towner"
- **Mobile Responsive**: All footer elements properly centered on mobile
- **Site Description**: Updated footer text to reflect site purpose
- **Newsletter Subscription**: Added Buttondown email signup form in right footer column
  - Positioned above social links (Posts/RSS)
  - Compact inline design with email input and subscribe button
  - Mobile responsive (stacks vertically on small screens)
  - No attribution link for cleaner appearance

### Image Management
- **Simplified Structure**: Changed from /YYYY/MM/DD/slug/image.png to /YYYY/MM/DD/image.png
- **Naming Convention**: Use post slug as filename (brain-reward-system.png)
- **Documentation**: Updated CLAUDE.md to reflect new image organization

## Development Workflow

### Common Tasks

**Adding New Post**
1. Create markdown file in `_posts/` with proper frontmatter
2. Add featured image to correct directory structure
3. Use existing categories from core list
4. Test locally with `bundle exec jekyll serve`

**Modifying Styles**
1. Edit `_sass/minima/custom-styles.scss`
2. Use existing variables from `custom-variables.scss`
3. Follow component organization structure
4. Test across all responsive breakpoints

**Navigation Updates**
1. Edit category list in `_includes/header.html` (line 59)
2. Ensure corresponding category archive pages exist
3. Update styling if needed in custom-styles.scss
4. Test mobile responsive behavior thoroughly

### Layout Inheritance Pattern

**CRITICAL**: Always use `layout: page` instead of `layout: default` for custom layouts.

```yaml
# ❌ Wrong - results in unstyled content
---
layout: default
---

# ✅ Correct - inherits proper styling
---
layout: page
---
```

This ensures proper CSS wrapper structure and styling inheritance.

### Performance Considerations
- **Image Optimization**: Compress images before adding to repository
- **CSS Organization**: Maintain component-based structure for maintainability
- **Responsive Images**: Use appropriate sizing for different viewports
- **Minimal JavaScript**: Keep dependencies light for fast loading

## Browser Support
- **Modern Browsers**: Chrome, Firefox, Safari, Edge (latest versions)
- **Mobile**: iOS Safari, Android Chrome (responsive design priority)
- **Progressive Enhancement**: Features degrade gracefully on older browsers
- **No IE Support**: Modern CSS features used throughout

## Testing Checklist
When making changes, test:
- [ ] Desktop navigation layout and functionality
- [ ] Mobile responsive behavior at all breakpoints
- [ ] Category button functionality throughout site
- [ ] Featured image display on all layouts
- [ ] Post metadata display and spacing
- [ ] Homepage gallery grid responsiveness
- [ ] Archive page layouts and filtering

This documentation should be updated as the project evolves to maintain accuracy for future development work.