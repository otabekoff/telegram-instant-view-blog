# TELEGRAM INSTANT VIEW SETUP GUIDE
## Based on Official Documentation Analysis

### CRITICAL ISSUE IDENTIFIED

Your current template is **overly complex** and contains several elements that could prevent Instant View generation. According to Telegram's official documentation, templates should be **simple and reliable**.

### THE PROBLEM

1. **Complex Widget Processing**: Your template has extensive widget transformation code that may fail
2. **Advanced XPath**: Complex selectors that might not match consistently
3. **Over-Engineering**: Many optional features that can cause the template to fail entirely
4. **Non-Standard Functions**: Using functions that may not work as expected

### THE SOLUTION

**Start with the ultra-minimal template** (`telegram-instant-view-minimal-test.iv`) and test it first. This follows Telegram's recommendation to start simple.

### STEP-BY-STEP INSTRUCTIONS

#### Step 1: Test the Minimal Template
1. Open [Telegram Instant View Editor](https://instantview.telegram.org/my/)
2. Enter your blog post URL: `https://otabekoff.github.io/telegram-instant-view-blog/2025/06/28/creating-telegram-instant-view-templates.html`
3. Copy the **ultra-minimal template** content
4. Paste it in the middle section
5. Press `Ctrl+S` (or `Cmd+S`) to apply
6. Check the right panel for the generated IV
7. Look at the status bar at the bottom for any errors

#### Step 2: Debug and Check
- Use `@debug: $("article.post")` to verify the selector works
- Use `@debug: $("h1.post-title")` to verify title extraction
- Use `@debug: $("div.post-content")` to verify body extraction
- Check the status bar for debug output

#### Step 3: Verify in Telegram
1. If the IV generates successfully, click "View in Telegram"
2. This will give you a special link like `t.me/iv?url=...&rhash=...`
3. Test this link in Telegram to see the actual IV

#### Step 4: Gradually Add Features
Only after the minimal template works:
1. Add basic cleanup (remove scripts, styles)
2. Add image processing
3. Add simple embed support
4. Test each addition individually

### COMMON ISSUES FROM DOCUMENTATION

According to Telegram's checklist, these are the most common reasons IV fails:

1. **Wrong Targeting**: Template applies to wrong pages
2. **Missing Required Properties**: Title or body not extracted correctly
3. **Unsupported Content**: Template tries to process unsupported elements
4. **Over-complexity**: Template is too complex and fails internally

### REQUIRED VS OPTIONAL

**REQUIRED (must work)**:
- `title`: Must extract the post title correctly
- `body`: Must extract the post content correctly
- **Correct targeting**: Must only apply to blog posts, not listing pages

**OPTIONAL (can be added later)**:
- `author`: Nice to have but not critical
- `published_date`: Helpful but not required for IV to work
- `site_name`: For link previews
- `channel`: For promotion

### VALIDATION CHECKLIST

✅ **Template uploads without errors**
✅ **IV generates in the editor**  
✅ **Title appears correctly**
✅ **Body content appears correctly**
✅ **"View in Telegram" button appears**
✅ **IV works when opened in Telegram app**

### NEXT STEPS

1. **Test the minimal template first**
2. **Only add complexity after basics work**
3. **Use @debug function extensively**
4. **Check status bar for all errors**
5. **Test multiple blog posts**
6. **Save and publish the working template**

### IMPORTANT NOTES

- **Templates must be uploaded and saved** in the IV Editor to take effect
- **The IV button only appears** when the template is properly working
- **Start simple** and add complexity gradually
- **Test every change** before adding more features

### OFFICIAL TELEGRAM REQUIREMENTS

Based on the official documentation:
1. **IV 2.1 version required**: Use `~version: "2.1"`
2. **Proper targeting**: Only generate IV for article pages
3. **Essential content preservation**: All article content must be included
4. **Unnecessary element removal**: Remove navigation, ads, etc.
5. **Template reliability**: Must work for all targeted pages

### DEBUGGING TIPS

If the minimal template doesn't work:
1. Check if selectors match your HTML structure
2. Use browser inspector to verify CSS selectors
3. Test with different blog post URLs
4. Check for JavaScript-generated content that might not be accessible
5. Verify the page structure matches your selectors

Remember: **The Instant View button will only appear after you successfully save a working template in the Telegram IV Editor.**
