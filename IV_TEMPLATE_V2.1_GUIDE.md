# Telegram Instant View Template v2.1 - Update Guide 🚀

## Overview

This document outlines the major improvements and updates in the new **Telegram Instant View Template v2.1** compared to the previous v1.0 template. The new template incorporates the latest syntax, best practices, and features available in Telegram's Instant View platform.

## 🆕 What's New in v2.1

### 1. Enhanced Widget Support

#### New Social Media Platforms
- **TikTok embeds** - Full support for TikTok videos and content
- **X (formerly Twitter)** - Updated to support both twitter.com and x.com domains
- **Instagram Reels** - Added support for Instagram Reels alongside regular posts
- **Spotify embeds** - Native support for Spotify tracks, playlists, and podcasts
- **SoundCloud embeds** - Audio content embedding support

#### Improved Existing Widgets
- **Enhanced Facebook integration** - Better handling of Facebook posts and videos
- **Improved YouTube support** - More reliable YouTube video embedding
- **Advanced Telegram posts** - Better formatting for embedded Telegram content

### 2. Better Content Processing

#### Image Handling
```
# Lazy loading support
@set_attr(src, @data-src): $body//img[@data-src]
@set_attr(src, @data-original): $body//img[@data-original]

# Responsive image optimization
@set_attr(loading, "lazy"): $body//img
@remove_attr(width): $body//img
@remove_attr(height): $body//img
```

#### Advanced Table Support
```
# Preserve table formatting while avoiding nested tables
@preserve_formatting: $body//table[not(.//table)]
@wrap(<figure>): $body//table[not(.//table)]
```

#### Code Block Enhancement
```
# Better code formatting
@preserve_formatting: $body//pre
@preserve_formatting: $body//code
@wrap(<figure>): $body//pre[has-class("highlight") or has-class("code")]
```

### 3. Improved Meta Information Extraction

#### Enhanced Author Support
- Multiple author handling
- Structured data compatibility
- Better fallback mechanisms

#### Extended Meta Tag Support
```
# Publication and modification dates
published_date: $meta[@name="article:published_time"]/@content
modified_date: $meta[@name="article:modified_time"]/@content

# Tags and categories
kicker: $meta[@name="article:section"]/@content
$tags_meta: $meta[@name="article:tag" or @property="article:tag"]
```

#### Language and Localization
```
# Language detection
lang: /html/@lang
lang: $meta[@name="language"]/@content
```

### 4. Advanced Content Targeting

#### Smarter Page Detection
```
# More specific content targeting
?exists: $("article, .post, .entry, .blog-post, main .content")

# Better exclusion rules
?not_exists: $(".archive, .category, .tag-page, .search-results")
?not_exists: $(".home, .front-page, .listing")
```

#### Enhanced Anchor Support
```
# Better anchor handling
@before(<anchor>, name, @name): $body//a[@name]
@before(<anchor>, name, @id): $body//*[@id]
```

### 5. Comprehensive Cleanup Rules

#### Modern Element Removal
```
# Remove modern unsupported elements
@unsupported: $body//video[not(@src) and not(.//source[@src])]
@unsupported: $body//audio[not(@src) and not(.//source[@src])]
@unsupported: $body//form
@unsupported: $body//input
```

#### Better Navigation Cleanup
```
# Smarter header/footer removal
@remove: $body//header[not(has-class("post-header"))]
@remove: $body//footer[not(has-class("post-footer"))]
```

## 🔄 Migration from v1.0 to v2.1

### Breaking Changes
1. **Widget syntax updates** - Some widget embedding syntax has been modernized
2. **Meta tag handling** - Enhanced meta tag processing may extract different information
3. **Cleanup rules** - More aggressive cleanup may remove elements that were previously preserved

### Compatibility Notes
- ✅ **Backward compatible** with most v1.0 templates
- ✅ **Enhanced features** improve content extraction
- ⚠️ **Test thoroughly** with your specific website structure

### Migration Steps

1. **Backup your current template**
2. **Copy the new v2.1 template**
3. **Customize targeting rules** for your specific website
4. **Test with multiple pages** from your site
5. **Adjust selectors** if needed for your HTML structure
6. **Use the debug function** to troubleshoot any issues

## 🛠️ Customization Guide

### For Blog Sites
```
# Customize these selectors for your blog structure
title: $("h1.your-title-class, .post-title").first()
body: $(".your-content-class, .post-body").first()
author: $(".your-author-class, .byline").first()
published_date: $("time.your-date-class, .post-date").first()
```

### For News Sites
```
# Add news-specific elements
subtitle: $(".article-subtitle, .deck, .subheadline").first()
kicker: $(".section, .category, .topic").first()
```

### For Documentation Sites
```
# Focus on structured content
?exists: $(".documentation, .docs, .guide")
body: $(".doc-content, .guide-content, .documentation-body")
```

## 🐛 Common Issues and Solutions

### Template Not Triggering
**Problem**: Template doesn't activate for your pages
**Solution**: 
```
# Check your targeting conditions
?exists: $("article, .post, .content")
@debug: $("article")  # Use debug to test
```

### Missing Content
**Problem**: Important content not appearing
**Solution**:
```
# Use broader selectors with fallbacks
title: $("h1, .title, .headline, .post-title").first()
body: $(".content, .post-content, .article-body, main").first()
```

### Widget Issues
**Problem**: Social media embeds not working
**Solution**:
```
# Check the specific widget code in your HTML
@debug: $("blockquote.twitter-tweet")
# Ensure the widget containers exist
```

## 📊 Performance Improvements

### Faster Processing
- **Optimized selectors** for better performance
- **Reduced redundancy** in processing rules
- **Smarter conditional logic** to avoid unnecessary operations

### Better Caching
- **Enhanced meta extraction** improves caching efficiency
- **Consistent output** reduces cache misses
- **Optimized image handling** for faster loading

## 🔧 Testing Your Updated Template

### Use the Debug Function
```
@debug: $("h1")  # Test title selection
@debug: $body    # Check body content
@debug: exists(".author")  # Verify conditions
```

### Test Multiple Page Types
1. **Article pages** - Main content
2. **Home page** - Should not generate IV
3. **Category pages** - Should be excluded
4. **Archive pages** - Should be excluded

### Validate Widget Support
- Share posts with different social media embeds
- Test video content embedding
- Verify image galleries work correctly

## 📚 Additional Resources

- [Official Telegram IV Documentation](https://instantview.telegram.org/docs)
- [Template Contest Examples](https://instantview.telegram.org/contest)
- [Community Templates](https://instantview.telegram.org/samples)

## 🎯 Best Practices for v2.1

1. **Start with targeting** - Get your conditions right first
2. **Test incrementally** - Add features one at a time
3. **Use debug frequently** - Debug function is your friend
4. **Preserve important formatting** - Use @preserve_formatting wisely
5. **Clean up aggressively** - Remove all non-essential elements
6. **Think mobile-first** - Optimize for mobile reading experience

## ✨ What's Coming Next

The Telegram team continues to evolve Instant View. Future updates may include:
- Enhanced video support
- Better interactive content handling
- Improved accessibility features
- Advanced customization options

---

**Ready to implement?** Copy the `telegram-instant-view-template-v2.1.iv` file and customize it for your website structure. Remember to test thoroughly before deploying to production!
