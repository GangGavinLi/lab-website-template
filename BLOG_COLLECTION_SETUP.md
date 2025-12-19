# Setting Up the `_blog` Collection for Learning Materials

## Summary

I've successfully created a custom `_blog` collection for your website to display learning materials, tutorials, and educational resources - separate from your news posts.

## What Was Created

### 1. **_blog/ Folder** (Collection)
Location: `_blog/`

This folder contains learning materials and tutorials. Each file is a separate tutorial/guide.

**Created Files:**
- `2025-01-10-intro-federated-learning.md` - Comprehensive tutorial on federated learning for energy systems
- `2025-01-05-lstm-energy-forecasting.md` - Deep dive into LSTM networks for time-series forecasting
- `README.md` - Documentation on how to use the collection

### 2. **learning/ Folder** (Display Page)
Location: `learning/index.md`

This is the page that displays all learning materials from the `_blog` collection. It will appear in your site navigation.

### 3. **Updated Configuration**
Location: `_config.yaml`

Added the `blog` collection configuration so Jekyll recognizes and processes the learning materials.

## How It Works

### Collections in Jekyll

Your website now has **three collections**:

1. **`_members/`** → Team member profiles → Displays on `/team/`
2. **`_posts/`** → News and announcements → Displays on `/blog/`
3. **`_blog/`** → Learning materials/tutorials → Displays on `/learning/`

### Key Differences

| Feature | `_posts/` (News) | `_blog/` (Learning) |
|---------|------------------|---------------------|
| **Purpose** | Lab news, announcements | Tutorials, educational content |
| **Display Page** | `/blog/` | `/learning/` |
| **Content Type** | Short updates | Long-form tutorials |
| **Author** | Lab members | Usually grad students/PI |
| **Tags** | lab news, awards | machine learning, tutorials |

## File Structure

```
your-website/
├── _config.yaml                 ← Updated with blog collection
├── _posts/                      ← News/announcements
│   └── 2025-01-15-triple-double-milestone.md
├── _blog/                       ← NEW: Learning materials
│   ├── README.md
│   ├── 2025-01-10-intro-federated-learning.md
│   └── 2025-01-05-lstm-energy-forecasting.md
├── blog/                        ← News page
│   └── index.md
└── learning/                    ← NEW: Learning materials page
    └── index.md
```

## How to Add New Learning Materials

### Step 1: Create the File

Create a new file in `_blog/` with this naming format:
```
_blog/YYYY-MM-DD-title-with-dashes.md
```

### Step 2: Add Front Matter

```yaml
---
title: "Your Tutorial Title"
author: gang-li  # or william-mayfield, doha-bounaim, etc.
date: 2025-01-20
tags:
  - machine learning
  - tutorial
  - python
---
```

### Step 3: Write Content

```markdown
Brief introduction to what this tutorial covers.

<!-- excerpt start -->
This is the preview text that appears on the listing page.
<!-- excerpt end -->

## Section 1: Introduction

Your detailed content here...

## Section 2: Implementation

```python
# Code examples
def example():
    return "Hello"
```

## Further Reading

Links to papers, documentation, etc.
```

### Step 4: Test Locally

```bash
bundle exec jekyll serve
```

Visit `http://localhost:4000/learning/` to see your new material.

## Navigation

The learning materials page will appear in your site navigation with:
- **Order**: 6 (after Contact)
- **Title**: "Learning Materials"
- **Tooltip**: "Educational resources and tutorials"

You can change these in `learning/index.md`:

```yaml
---
title: Learning Materials
nav:
  order: 6
  tooltip: Educational resources and tutorials
---
```

## Features

### Search and Filter
Users can:
- Search by keywords
- Filter by tags
- Browse chronologically

### Responsive Design
- Mobile-friendly
- Automatic syntax highlighting for code
- Math equation rendering with LaTeX

### Author Attribution
Each tutorial shows:
- Author name (linked to their profile)
- Publication date
- Tags

## Tutorial Content Guidelines

### What to Include

**Good Topics:**
- ✅ AI/ML techniques used in lab research
- ✅ Step-by-step implementation guides
- ✅ Research methodology explanations
- ✅ Tool and framework tutorials
- ✅ Data analysis techniques

**Structure:**
- Clear learning objectives
- Background/motivation
- Detailed explanation with examples
- Working code snippets
- Practical applications
- Further reading/resources

### Code Examples

Always include:
- Complete, runnable examples
- Comments explaining key steps
- Error handling
- Expected output

```python
import torch
import torch.nn as nn

class SimpleLSTM(nn.Module):
    """Simple LSTM for time series prediction"""
    def __init__(self, input_size, hidden_size):
        super().__init__()
        self.lstm = nn.LSTM(input_size, hidden_size)
        self.fc = nn.Linear(hidden_size, 1)
    
    def forward(self, x):
        lstm_out, _ = self.lstm(x)
        return self.fc(lstm_out[-1])

# Usage
model = SimpleLSTM(input_size=5, hidden_size=64)
```

## Example Tutorials Created

### 1. Federated Learning Tutorial
**File**: `_blog/2025-01-10-intro-federated-learning.md`

**Topics Covered:**
- What is federated learning
- Why use it for energy systems
- Basic workflow
- Application to wind turbine monitoring
- Code examples in PyTorch
- Challenges and solutions
- Getting started guide

**Length**: ~3000 words with code examples

### 2. LSTM Forecasting Tutorial
**File**: `_blog/2025-01-05-lstm-energy-forecasting.md`

**Topics Covered:**
- LSTM architecture basics
- Data preparation for energy forecasting
- Model implementation
- Bidirectional LSTM
- CNN-BiLSTM hybrid architecture
- Evaluation metrics
- Complete working example

**Length**: ~3500 words with extensive code

## Customization Options

### Change Page Title
Edit `learning/index.md`:
```yaml
title: Tutorials  # or "Resources", "Education", etc.
```

### Change Navigation Order
Edit `learning/index.md`:
```yaml
nav:
  order: 3  # Move it earlier in navigation
```

### Change Display Style
The page uses `post-excerpt` component. You can customize it in `_includes/post-excerpt.html`

## Maintenance

### Regular Updates
- Add new tutorials as research progresses
- Update existing tutorials with new findings
- Archive outdated content (move to subfolder)

### Student Contributions
Encourage graduate students to write tutorials on:
- Their research methods
- Tools they've learned
- Novel techniques they've implemented

## Troubleshooting

### Tutorial Not Appearing

**Check:**
1. ✅ File is in `_blog/` folder
2. ✅ Filename format: `YYYY-MM-DD-title.md`
3. ✅ Front matter is correct (title, author, date)
4. ✅ Author slug matches a file in `_members/`
5. ✅ `_config.yaml` includes blog collection

### Navigation Not Showing

**Check:**
1. ✅ `learning/index.md` has `nav:` section in front matter
2. ✅ Order number doesn't conflict with other pages

### Code Not Highlighting

**Use proper markdown:**
````markdown
```python
# Your code here
```
````

## Benefits of This Setup

### For Students
- ✅ Learn by teaching
- ✅ Build portfolio
- ✅ Share expertise

### For Lab
- ✅ Knowledge preservation
- ✅ Onboarding resources
- ✅ Public education
- ✅ Increased visibility

### For Visitors
- ✅ Learn cutting-edge techniques
- ✅ Access practical examples
- ✅ Understand lab research

## Next Steps

1. **Copy files to your repository**:
   ```bash
   cp -r /mnt/user-data/outputs/_blog /path/to/your/repo/
   cp -r /mnt/user-data/outputs/learning /path/to/your/repo/
   cp /mnt/user-data/outputs/_config.yaml /path/to/your/repo/
   ```

2. **Test locally**:
   ```bash
   cd /path/to/your/repo
   bundle exec jekyll serve
   ```

3. **Visit the learning page**:
   ```
   http://localhost:4000/learning/
   ```

4. **Push to GitHub**:
   ```bash
   git add _blog/ learning/ _config.yaml
   git commit -m "Add learning materials collection"
   git push
   ```

## Future Tutorial Ideas

Based on your research, consider tutorials on:

1. **Physics-Informed Neural Networks**
   - Theory and implementation
   - Application to cable monitoring

2. **Time-Series Forecasting**
   - Advanced LSTM architectures
   - Attention mechanisms
   - Multi-horizon prediction

3. **Gear Dynamics Modeling**
   - Mesh stiffness calculation
   - Contact analysis
   - Optimization methods

4. **IVT Control Systems**
   - Closed-loop control
   - Reinforcement learning
   - Time-delay compensation

5. **Wind Turbine Monitoring**
   - SCADA data analysis
   - Anomaly detection
   - Fault prediction

## Conclusion

You now have a complete learning materials system! The `_blog` collection provides:

- ✅ Separate space for educational content
- ✅ Professional tutorials with code examples
- ✅ Easy-to-use template for new materials
- ✅ Search and filtering capabilities
- ✅ Integration with your existing website

Start by adding the files to your repository, then encourage your students to contribute tutorials on their research topics!

---

**Questions?** The `_blog/README.md` file has detailed instructions for creating new tutorials.
