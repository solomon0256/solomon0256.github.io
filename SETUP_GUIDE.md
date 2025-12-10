# Academic Homepage Setup Guide

This guide will help you customize your academic homepage for Master/PhD applications.

## Quick Start

Your homepage is now configured and ready to be customized! The site will be available at:
`https://solomon0256.github.io/academic_homepage/`

## Step 1: Enable GitHub Pages

1. Go to your repository: https://github.com/solomon0256/academic_homepage
2. Click on **Settings** → **Pages** (in the left sidebar)
3. Under "Build and deployment":
   - Source: Select **Deploy from a branch**
   - Branch: Select **main** (or your default branch) and **/ (root)**
4. Click **Save**
5. Wait a few minutes for the site to build (you'll see a green checkmark when ready)
6. Visit your site at: `https://solomon0256.github.io/academic_homepage/`

## Step 2: Customize Your Profile

Edit `_data/profile.yml` to add your personal information:

### Basic Information
- **primary_name**: Your full name
- **secondary_name**: Alternative name (if any)
- **navbar_name**: Name to display in navigation bar
- **email**: Your email address
- **gscholar**: Your Google Scholar ID
- **github**: Your GitHub username
- **twitter**: Your Twitter handle (without @)

### Positions
Update the positions section with your current status:
```yaml
positions:
- name: PhD Applicant  # or MS Applicant
- name: Your Current University/Institution
  logo: /assets/images/badges/your_logo.png  # optional
```

### Short Bio
Replace the placeholder text with your own bio. You can use HTML for formatting:
```yaml
short_bio: >-
  <p>
    Write your introduction here. Highlight your research interests, 
    academic background, and career goals.
  </p>
  <p>
    Mention specific areas you want to pursue in your graduate studies.
  </p>
```

### Education
Update with your actual education history:
```yaml
education:
- name: Your University
  logo: /assets/images/badges/your_logo.png  # optional
  position: >- 
    Department/Major <br/>
    Degree (e.g., B.S. in Computer Science)
  date: Start - End dates
```

### Awards (Optional)
Add your academic achievements:
```yaml
awards:
- name: Award or Scholarship Name
  date: Year
```

### Portrait
- Replace `/assets/images/photos/portrait.jpg` with your professional photo
- Update the `portrait_caption` or comment it out if you don't want a caption

## Step 3: Add Your Publications

Create markdown files in `_publications/` organized by year:

Example: `_publications/2024/my-paper.md`
```yaml
---
title: "Your Paper Title"
date: 2024-05-12 00:01:00 +0800
selected: true  # Set to true for selected publications
pub: "Conference/Journal Name"
pub_date: "2024"
abstract: >-
  Brief description of your paper (1-2 sentences).
cover: /assets/images/covers/cover1.jpg  # optional
authors:
  - Your Name
  - Co-author Name
links:
  Paper: https://arxiv.org/...
  Code: https://github.com/...
---
```

**Tips for applicants:**
- If you don't have publications yet, you can:
  - Add research projects or class projects
  - Add technical reports or preprints
  - Remove the publications section by editing `_data/display.yml`

## Step 4: Add News/Updates

Create markdown files in `_news/` to share recent updates:

Example: `_news/2024-accepted-program.md`
```yaml
---
title: >-
    Accepted to [Program Name] Summer Research Program
date: 2024-06-01 10:00:00 -0800
---
```

**Ideas for news items:**
- Research project completions
- Presentations at conferences/seminars
- Awards and scholarships
- Course completions or certifications
- Open source contributions

## Step 5: Configure Display Settings

Edit `_data/display.yml` to control what appears on your homepage:

```yaml
homepage:
  show_experience: true      # Show work/research experience
  show_news: true            # Show news section
  show_selected_publications: true  # Show selected papers
  num_news: 10              # Number of news items to display
```

## Step 6: Add Custom Showcase Items (Optional)

The `_showcase/` directory allows you to add custom cards to your homepage.
See the examples in `_showcase/default/` for inspiration.

## Step 7: Update Navigation

Edit `_data/navigation.yml` to customize the navigation menu.

## Customization Tips for Graduate Applications

### For PhD Applicants:
1. **Highlight Research Experience**: Add detailed descriptions in the experience section
2. **Emphasize Publications**: Set `selected: true` for your best papers
3. **Research Statement**: Use the bio section to articulate your research vision
4. **Technical Skills**: Consider adding a showcase card for your technical skills

### For Master's Applicants:
1. **Academic Projects**: Add significant course projects as publications or showcase items
2. **Technical Background**: Highlight relevant coursework and skills
3. **Career Goals**: Clearly state your academic and career objectives in the bio
4. **Leadership**: Include any teaching assistant or leadership experiences

### Common Elements:
- **Professional Photo**: Use a high-quality, professional headshot
- **Contact Information**: Make it easy for professors to reach you
- **Google Scholar**: Link your profile if you have one
- **GitHub**: Showcase your code and projects
- **Clear Writing**: Keep descriptions concise and impactful

## Local Development (Optional)

To preview changes locally before deploying:

1. Install Ruby and Jekyll (see [Jekyll docs](https://jekyllrb.com/docs/installation/))
2. Install dependencies:
   ```bash
   bundle install
   ```
3. Run the local server:
   ```bash
   bundle exec jekyll serve
   ```
4. Visit `http://localhost:4000/academic_homepage/` in your browser

## Troubleshooting

### Site not displaying correctly?
- Check that GitHub Pages is enabled in repository settings
- Verify the `baseurl` in `_config.yml` matches your repository name
- The debug widgets on the homepage will show any configuration issues

### Images not loading?
- Ensure image paths start with `/assets/images/`
- Verify that image files are committed to the repository
- Check that file names are correct (case-sensitive)

### Need more help?
- Check the [original template repository](https://github.com/luost26/academic-homepage)
- Review [Jekyll documentation](https://jekyllrb.com/docs/)
- See the [demo site](https://luost.me/academic-homepage/)

## Next Steps

1. ✅ Configuration is complete - baseurl is set correctly
2. 📝 Customize `_data/profile.yml` with your information
3. 📄 Add your publications, projects, and news
4. 🖼️ Replace example images with your own
5. 🚀 Enable GitHub Pages to deploy your site
6. 🔗 Share your homepage URL in your applications!

Good luck with your graduate school applications! 🎓
