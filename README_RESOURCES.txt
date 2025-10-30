Clarke Lab — Resources collection

FILES INCLUDED
- _config.yml                 -> Includes 'resources' collection + nav entry
- resources/index.md          -> Resources landing page (grid of cards)
- _resources/buffer-recipes.md
- _resources/adhesionomics-pipeline.md
- static/resources/readme.txt -> Put your PDFs/docs here
- resources-css-snippet.css   -> CSS to append to the end of static/site.css

HOW TO INSTALL (web-only)
1) In your 'visual-custom-theme' branch, upload all files from this zip.
   - If you already have a custom _config.yml, either:
     a) Replace it with this one, or
     b) Manually add the 'resources' collection + nav entry to your existing config.
2) Open 'resources-css-snippet.css' and COPY its contents.
3) Open 'static/site.css' in GitHub, scroll to the end, and PASTE the snippet there. Commit.
4) (Optional) Upload your PDF/doc files into 'static/resources/'. Update links in each _resources/*.md.
5) Refresh your Netlify Deploy Preview. You should see 'Resources' in the navbar.

ADDING NEW RESOURCES
- Create a new file in '_resources/' with front matter like:
  ---
  title: "RA Onboarding"
  summary: "Expectations, safety, and week-1 checklist."
  link: "/static/resources/ra-onboarding.docx"
  tags: ["onboarding"]
  ---
  (Optional long description here.)

LINKING
- For internal files, put them in 'static/resources/' and link like '/static/resources/filename.pdf'
- For external links (GitHub, tools), put the full URL in 'link:'

ANCHORS & URLS
- Do not include '.html' after a URL fragment. Use '/resources/#anchor' or '/resources/item-name/'.
