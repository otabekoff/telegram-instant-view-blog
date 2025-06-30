# Telegram Instant View Blog

A modern Jekyll blog specifically optimized for Telegram's Instant View feature, providing lightning-fast loading and perfect mobile formatting when shared on Telegram.

## 🚀 Features

- ⚡ **Instant View Optimized** - Perfect formatting for Telegram's Instant View
- 📱 **Mobile-First Design** - Responsive and fast on all devices
- 🎨 **Clean Typography** - Beautiful reading experience
- 🔍 **SEO Optimized** - Meta tags, structured data, and Open Graph
- 📡 **RSS Feed** - Automatic feed generation with Jekyll Feed
- 🏷️ **Tags & Categories** - Organized content structure
- 📱 **Telegram Integration** - Share buttons and channel promotion
- 🌟 **GitHub Pages Ready** - Deploy instantly to GitHub Pages

## 📖 Live Demo

- **Live Site**: [https://otabekoff.github.io/telegram-instant-view-blog](https://otabekoff.github.io/telegram-instant-view-blog)
- **Telegram Channel**: [@yourchannel](https://t.me/yourchannel)

## 🛠️ Quick Start

### Prerequisites

- Git installed on your system
- GitHub account
- Basic knowledge of Markdown and Jekyll (optional)

### 1. Fork or Use This Template

**Option A: Fork this repository**
1. Click the "Fork" button at the top of this repository
2. Clone your fork locally

**Option B: Use as template**
1. Click "Use this template" button
2. Create a new repository
3. Clone your new repository

```bash
git clone https://github.com/YOUR_USERNAME/telegram-instant-view-blog.git
cd telegram-instant-view-blog
```

### 2. Configure Your Blog

Edit `_config.yml` with your information:

```yaml
# Site settings
title: "Your Blog Title"
description: "Your blog description"
url: "https://yourusername.github.io"
baseurl: "/your-repo-name"
author: "Your Name"
email: "your.email@example.com"

# Telegram Channel Configuration
telegram_channel: "https://t.me/yourchannel"
telegram_channel_name: "@yourchannel"
```

### 3. Local Development (Optional)

To run the blog locally for testing:

```bash
# Install dependencies
bundle install

# Serve the site locally
bundle exec jekyll serve

# Visit http://localhost:4000 in your browser
```

### 4. Deploy to GitHub Pages

1. **Push your changes** to the main branch
2. **Go to repository Settings** → Pages
3. **Select source**: Deploy from a branch
4. **Choose branch**: main
5. **Choose folder**: / (root)
6. **Save** and wait for deployment

Your blog will be available at: `https://yourusername.github.io/repo-name`

## 📝 Creating Content

### Writing Blog Posts

Create new posts in the `_posts` directory with this naming convention:
`YYYY-MM-DD-title-with-hyphens.md`

```markdown
---
layout: post
title: "Your Amazing Blog Post"
date: 2025-06-30 12:00:00 +0000
categories: [web-development, tutorials]
tags: [javascript, react, tutorial]
author: "Your Name"
excerpt: "A brief description of your post for social sharing and previews."
---

# Your Content Here

Write your blog post content using Markdown syntax.

## Subheadings Work Great

- Bullet points are supported
- Multiple list items
- Keep it organized

### Code Examples

```javascript
function greetReader() {
    console.log("Hello, Instant View reader!");
}
```

Your content will be automatically optimized for Telegram's Instant View!
```

### Content Best Practices

#### For Optimal Instant View Experience:

1. **Use semantic headings** (H1 → H2 → H3 hierarchy)
2. **Keep paragraphs short** (2-4 sentences)
3. **Include meaningful alt text** for images
4. **Use bullet points and lists** for scannability
5. **Add relevant tags and categories** for organization

#### Image Optimization:

- **Maximum width**: 1200px
- **File size**: Under 500KB recommended
- **Formats**: WebP preferred, JPEG/PNG acceptable
- **Alt text**: Always include descriptive alt attributes

## 🎨 Customization

### Styling

The main stylesheet is located at `assets/css/style.css`. Key customization areas:

```css
/* Colors and Branding */
:root {
  --primary-color: #2196F3;
  --secondary-color: #0088cc;
  --text-color: #333;
  --background-color: #fff;
}

/* Typography */
body {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
}

/* Custom styling for your brand */
.site-title a {
  color: var(--primary-color);
}
```

### Navigation

Update the navigation menu in `_layouts/default.html`:

```html
<nav class="site-nav">
    <ul class="nav-links">
        <li><a href="{{ '/' | relative_url }}">Home</a></li>
        <li><a href="{{ '/about/' | relative_url }}">About</a></li>
        <li><a href="{{ '/archive/' | relative_url }}">Archive</a></li>
        <li><a href="/custom-page/">Custom Page</a></li>
    </ul>
</nav>
```

### Adding Custom Pages

Create new pages in the root directory:

```markdown
---
layout: default
title: "Custom Page"
permalink: /custom-page/
---

# Custom Page Content

Your page content here.
```

## 📱 Telegram Instant View Setup

### Creating Templates

1. **Visit** [instantview.telegram.org](https://instantview.telegram.org/)
2. **Go to** "My Templates"
3. **Enter** a URL from your blog
4. **Create** your template using this basic structure:

```
# Only create IV for blog posts
?exists: $("article.post")

# Extract content
title: $("h1.post-title")
author: $(".post-author span[itemprop=name]")
published_date: $("time.post-date")
@datetime: $published_date

# Cover image (if available)
@if(exists(".post-cover img")): cover: $(".post-cover img")

# Main content
body: $(".post-content")

# Remove unwanted elements
@remove: $("header.site-header")
@remove: $("footer.site-footer")
@remove: $(".post-sharing")
@remove: $(".related-posts")

# Add your channel
channel: "@yourchannel"
```

### Testing Your Template

1. **Save your template** (Ctrl+S / Cmd+S)
2. **Test with multiple blog posts** to ensure consistency
3. **Use "Track Changes"** to monitor template effects
4. **Refine and iterate** based on results

### Publishing Templates

**For immediate use:**
- Share links like: `https://t.me/iv?url=YOUR_POST_URL&rhash=YOUR_TEMPLATE_HASH`

**For all Telegram users:**
- Submit your template for review by Telegram team
- Wait for approval process (can take several weeks)

## 🔧 Advanced Configuration

### Adding Analytics

Add Google Analytics to `_layouts/default.html`:

```html
<!-- Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id=GA_MEASUREMENT_ID"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'GA_MEASUREMENT_ID');
</script>
```

### Custom Domain

1. **Add a CNAME file** to your repository root:
   
   ```
   yourdomain.com
   ```

2. **Configure DNS** with your domain provider:
   - Add CNAME record pointing to `yourusername.github.io`

3. **Update _config.yml**:
   
   ```yaml
   url: "https://yourdomain.com"
   baseurl: ""
   ```

### Comments Integration

Add comments using Utterances (GitHub-based):

```html
<!-- Add to _layouts/post.html -->
<script src="https://utteranc.es/client.js"
        repo="yourusername/your-repo"
        issue-term="pathname"
        theme="github-light"
        crossorigin="anonymous"
        async>
</script>
```

## 📊 Performance Optimization

### Lighthouse Scores

This blog is optimized for:
- **Performance**: 95+ score
- **Accessibility**: 100 score
- **Best Practices**: 95+ score
- **SEO**: 100 score

### Image Optimization

Use tools like:
- [ImageOptim](https://imageoptim.com/) for Mac
- [Squoosh](https://squoosh.app/) for web-based compression
- [Sharp](https://sharp.pixelplumbing.com/) for automated optimization

### Content Delivery

GitHub Pages provides:
- **Global CDN** for fast worldwide access
- **HTTPS** by default for security
- **Caching** for improved performance
- **99.9% uptime** reliability

## 🤝 Contributing

We welcome contributions! Here's how you can help:

### Bug Reports

1. **Check existing issues** to avoid duplicates
2. **Provide detailed information** about the bug
3. **Include steps to reproduce** the issue
4. **Add screenshots** if relevant

### Feature Requests

1. **Describe the feature** and its benefits
2. **Explain the use case** and motivation
3. **Consider implementation complexity**
4. **Discuss alternatives** you've considered

### Code Contributions

1. **Fork the repository** and create a feature branch
2. **Make your changes** with clear, descriptive commits
3. **Test thoroughly** across different devices/browsers
4. **Update documentation** as needed
5. **Submit a pull request** with detailed description

### Development Setup

```bash
# Clone your fork
git clone https://github.com/YOUR_USERNAME/telegram-instant-view-blog.git
cd telegram-instant-view-blog

# Install dependencies
bundle install

# Create a feature branch
git checkout -b feature/your-feature-name

# Make your changes and test
bundle exec jekyll serve

# Commit and push
git add .
git commit -m "Add your feature description"
git push origin feature/your-feature-name
```

## 📚 Documentation

### Folder Structure

```
telegram-instant-view-blog/
├── _config.yml              # Jekyll configuration
├── _layouts/                # Page layouts
│   ├── default.html         # Base layout
│   └── post.html           # Blog post layout
├── _posts/                  # Blog posts
├── _sass/                   # Sass partials (optional)
├── assets/                  # Static assets
│   ├── css/
│   │   └── style.css       # Main stylesheet
│   ├── images/             # Image files
│   └── js/                 # JavaScript files (optional)
├── about.md                # About page
├── archive.html            # Archive page
├── index.html              # Homepage
├── Gemfile                 # Ruby dependencies
└── README.md               # This file
```

### Key Files Explained

- **_config.yml**: Main configuration file for Jekyll and site settings
- **_layouts/default.html**: Base HTML template used by all pages
- **_layouts/post.html**: Template specifically for blog posts
- **assets/css/style.css**: Main stylesheet with responsive design
- **index.html**: Homepage with recent posts and hero section
- **about.md**: About page explaining the blog and features
- **archive.html**: Chronological listing of all posts

## 🚨 Troubleshooting

### Common Issues

**Blog not loading after deployment:**
- Check `_config.yml` baseurl setting
- Ensure GitHub Pages is enabled in repository settings
- Verify repository is public (required for free GitHub Pages)

**Instant View not working:**
- Verify template syntax in Telegram's editor
- Check Open Graph meta tags in page source
- Test with Telegram's template debugger

**Images not displaying:**
- Check file paths and names (case-sensitive)
- Ensure images are in `assets/images/` directory
- Verify image file sizes (under 100MB for GitHub)

**Local development issues:**
```bash
# Update Ruby gems
bundle update

# Clear Jekyll cache
bundle exec jekyll clean

# Reinstall dependencies
rm -rf _site .sass-cache
bundle install
bundle exec jekyll serve
```

### Getting Help

- **Documentation**: [Jekyll Docs](https://jekyllrb.com/docs/)
- **GitHub Pages**: [GitHub Pages Docs](https://docs.github.com/en/pages)
- **Telegram IV**: [Instant View Documentation](https://instantview.telegram.org/docs)
- **Issues**: [Create an issue](https://github.com/otabekoff/telegram-instant-view-blog/issues)

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **Telegram Team** - For creating the amazing Instant View feature
- **Jekyll Community** - For the excellent static site generator
- **GitHub** - For providing free hosting through GitHub Pages
- **Open Source Community** - For inspiration and contributions

## 📞 Support

If you find this project helpful:

- ⭐ **Star the repository** to show your support
- 🐛 **Report bugs** via GitHub Issues
- 💡 **Suggest features** and improvements
- 📱 **Follow** [@yourchannel](https://t.me/yourchannel) on Telegram
- 🤝 **Contribute** to make it even better

---

**Built with ❤️ for the developer community. Happy blogging!** 🚀

*For questions, suggestions, or collaboration opportunities, feel free to reach out via [Telegram](https://t.me/yourchannel) or [create an issue](https://github.com/otabekoff/telegram-instant-view-blog/issues).*
