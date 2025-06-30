# Quick Setup Guide for This Blog's IV Template v2.1

## 🚀 Installation Instructions

### 1. Copy the Template
The updated template is available in: `telegram-instant-view-template-v2.1.iv`

### 2. Access Telegram IV Editor
1. Go to [instantview.telegram.org](https://instantview.telegram.org/)
2. Navigate to "My Templates"
3. Enter any blog post URL from your site
4. Click "Create Template"

### 3. Paste the Updated Template
Copy the entire content from `telegram-instant-view-template-v2.1.iv` and paste it into the editor.

### 4. Customize for Your Blog
Update these specific selectors for your Jekyll blog structure:

```
# Update the channel reference (line ~300)
channel: "@your_telegram_channel"

# Test with your specific post structure
# The template should work out-of-the-box for most Jekyll blogs
```

### 5. Test with Your Posts
Test the template with these URLs from your blog:
- A recent blog post (should work)
- The home page (should NOT generate IV)
- Archive page (should NOT generate IV)
- About page (should NOT generate IV)

## ✅ Verification Checklist

- [ ] Template loads without errors
- [ ] Blog posts generate clean Instant Views
- [ ] Home page doesn't trigger IV
- [ ] Archive pages don't trigger IV
- [ ] Images load correctly
- [ ] Author and date appear properly
- [ ] Social media embeds work (if any)
- [ ] Your Telegram channel is promoted

## 🐛 Common Jekyll-Specific Issues

### Issue: Date Format
If dates don't appear correctly:
```
published_date: $("time[datetime], .post-date").first()
@datetime: $published_date
```

### Issue: Author Name
If author doesn't show:
```
author: $(".post-author, [itemprop='author']").first()
```

### Issue: Categories/Tags
If you want to show categories:
```
kicker: $(".post-categories a, .post-category").first()
```

## 📱 Testing Your IV Template

1. **Save the template** (Ctrl+S or Cmd+S)
2. **Test with multiple posts** to ensure consistency
3. **Use "Track Changes"** to monitor template effects
4. **Share a test link** like: `https://t.me/iv?url=YOUR_POST_URL&rhash=YOUR_TEMPLATE_HASH`

## 🎉 You're Ready!

Your Telegram Instant View template is now updated to v2.1 with all the latest features and optimizations. Your blog posts will now load instantly in Telegram with perfect formatting across all devices!

For detailed technical information, see `IV_TEMPLATE_V2.1_GUIDE.md`.
