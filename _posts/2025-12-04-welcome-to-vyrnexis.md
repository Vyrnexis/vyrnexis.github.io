---
layout: default
title: "Welcome to Vyrnexis"
date: 2025-12-04 18:00:00 +0800
author: "Vyrnexis"
---

Welcome to my corner of the internet. This site is a simple Jekyll build on GitHub Pages where I share notes on Linux setups, Nim experiments, and whatever else I’m tinkering with.

What to expect:

- Code snippets and small tools (often in Nim or Python).
- Reverse-engineering notes and the occasional overlay/graphics experiment.
- Walkthroughs of Linux workflows and desktop customizations.

```bash
# If you’re forking this site, basic post flow looks like:
# 1) Add a post
cat > _posts/YYYY-MM-DD-your-post.md <<'EOF'
---
layout: default
title: "Your Post"
date: YYYY-MM-DD HH:MM:SS +0800
author: "Your Name"
---
Your content here.
EOF

# 2) Commit and push
git add _posts/YYYY-MM-DD-your-post.md
git commit -m "Add new post"
git push
```

No build servers needed—GitHub Pages does the rebuild when you push. This setup is hand-rolled for Pages (not a downloaded theme), so feel free to fork and adapt it. Cheers for dropping by.
