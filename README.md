# oxbow_solutions_consulting

Website for Oxbow Solutions LLC, an agricultural data science and computer vision consulting business. It's plain HTML/CSS/JS with no build step, deployed on Netlify.

## Structure

```
site/
  index.html        # Landing page: services, process, work, about, contact form
  thanks/index.html # Shown after a successful form submission
  404.html          # Netlify serves this for missing pages automatically
  css/styles.css
  js/main.js
  img/              # oxbow-logo.png (header), oxbow-icon.png (footer, thanks, 404)
  favicon-32.png, apple-touch-icon.png
netlify.toml        # Publish dir = site/
```

## Local preview

```bash
python -m http.server 8000 -d site
# open http://localhost:8000
```

The form won't submit locally because Netlify handles submissions. To test the form locally, use `npx netlify-cli dev`.

## Deploying to Netlify

1. In Netlify, choose **Add new site → Import an existing project** and pick this GitHub repo.
2. Netlify reads `netlify.toml`, so leave the build command empty and set the publish directory to `site`.
3. Go to **Site configuration → Forms** and enable form detection, then redeploy once. The `contact` form will then show up.
4. Under **Forms → Form notifications**, add an email notification so submissions get forwarded to your inbox.
5. (Optional) Add your custom domain under **Domain management**.

## Contact form

The form uses [Netlify Forms](https://docs.netlify.com/forms/setup/): `data-netlify="true"` plus a hidden `form-name` field. Spam is filtered by a honeypot field (`bot-field`) and Netlify's built-in Akismet filtering. After a successful submission, the visitor is redirected to `/thanks/`.
