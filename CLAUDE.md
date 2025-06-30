# Claude Code Project Guide - Mark Rondina Portfolio

## Project Overview
Jekyll-based portfolio website for markrondina.com featuring UX/design projects and blog posts.

## Development Environment

### Prerequisites
- Ruby (for Jekyll)
- Bundler gem
- Jekyll and required gems (see Gemfile)

### Setup Commands
```bash
# Install dependencies
bundle install

# Serve locally with live reload
bundle exec jekyll serve --livereload

# Build for production
bundle exec jekyll build

# Clean build artifacts
bundle exec jekyll clean
```

## Project Structure

### Content Collections
- `_posts/` - Blog articles (markdown files with YAML front matter)
- `_projects/` - Portfolio projects (markdown files with YAML front matter)
- `_pages/` - Static pages (about, contact, etc.)

### Templates & Components
- `_layouts/` - Page templates (default, post, project, page, prototype)
- `_includes/` - Reusable components (header, footer, sections, widgets)
- `_sass/` - Modular Sass architecture (settings, tools, base, modules, layouts)

### Asset Directories
- `images/` - All image assets
- `js/` - JavaScript files
- `fonts/` - Font files
- `_site/` - Generated site (don't edit directly)

## Content Management

### Adding Blog Posts
Create files in `_posts/` with format: `YYYY-MM-DD-title.md`
Required front matter:
```yaml
---
layout: post
title: "Post Title"
date: YYYY-MM-DD
categories: [category1, category2]
featured_image: /images/featured-image.jpg
---
```

### Adding Projects
Create files in `_projects/` with format: `YYYY-MM-DD-project-name.md`
Required front matter:
```yaml
---
layout: project
title: "Project Title"
date: YYYY-MM-DD
client: "Client Name"
role: "Your Role"
featured_image: /images/project-image.jpg
---
```

## Development Best Practices

### Before Making Changes
1. Always run `bundle exec jekyll serve --livereload` for local development
2. Test changes locally before committing
3. Check responsive design on multiple screen sizes

### Code Style
- Follow existing Sass architecture (0-settings, 1-tools, 2-base, 3-modules, 4-layouts)
- Use semantic HTML and proper accessibility attributes
- Maintain consistent indentation (2 spaces)
- Use meaningful class names following BEM methodology where possible

### Image Optimization
- Optimize images before adding to `/images/` directory
- Use appropriate formats (JPG for photos, PNG for graphics, SVG for icons)
- Include alt text for all images

## Debugging

### Common Issues
- **Build failures**: Check YAML front matter syntax
- **Sass errors**: Verify import paths in `_sass/` files
- **Layout issues**: Check that layout exists in `_layouts/`
- **Missing images**: Verify file paths relative to site root

### Debug Commands
```bash
# Verbose build output
bundle exec jekyll build --verbose

# Check for broken links/references
bundle exec jekyll doctor

# Serve with detailed error messages
bundle exec jekyll serve --trace
```

## Production Deployment

### Pre-deployment Checklist
1. Run `bundle exec jekyll build` successfully
2. Test built site in `_site/` directory
3. Verify all images load correctly
4. Check responsive design
5. Validate HTML/CSS
6. Test contact forms and external links

### Build Commands
```bash
# Clean build for production
bundle exec jekyll clean && bundle exec jekyll build

# Build with production environment
JEKYLL_ENV=production bundle exec jekyll build
```

## Content Guidelines

### Writing Style
- Use clear, concise language
- Include proper headings hierarchy (H1 → H2 → H3)
- Add meta descriptions for SEO

### Project Documentation
- Include project timeline, role, and outcomes
- Use high-quality images and screenshots
- Provide context for design decisions

## Maintenance

### Regular Tasks
- Update Ruby gems: `bundle update`
- Optimize images periodically
- Review and update outdated content
- Monitor site performance and loading times

### Backup
- Keep source files in version control
- Back up image assets
- Document any custom configurations

## Claude Code Specific Notes

### When working with Claude Code on this project:
- Specify file paths relative to project root
- Mention if changes affect multiple collections (posts, projects, pages)
- Indicate if Sass compilation is needed after style changes
- Test locally before considering changes complete

### Common Tasks for Claude Code:
- Adding new blog posts or projects
- Updating styles in `_sass/` files
- Modifying layout templates
- Optimizing existing content
- Debugging build issues