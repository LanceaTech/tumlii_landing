# Tumlii landing page

The public landing page for Tumlii, a gentle tummy diary: `index.html` (waitlist, app showcase, FAQ) and
`signup.html` (early access). Plain static HTML and CSS with no build step; `netlify.toml` holds the hosting settings.

## Forms (Netlify Forms)

- `waitlist` (home page): email, and optionally Android or iPhone.
- `early-access` (signup.html): name, email, phone, and the four agreements ticked.
- No password is ever collected on the web: accounts live in the app, where the password is set.
- Both forms carry a honeypot field (`bot-field`) against spam, and post with JavaScript to `/`.

## Hosting on Netlify

1. Add new project > Import from GitHub > `tumlii_landing`. Leave Base directory, Build command and Publish
   directory empty (`netlify.toml` sets publish to the repo root). Deploy.
2. Project configuration > Forms: Enable form detection, then redeploy (Deploys > Trigger deploy). The two forms
   appear under Forms after that deploy.
3. Forms > Form notifications: add an email notification for each form if you want an email per sign-up.
4. Domain management > Add a domain > `tumlii.com`. Either let Netlify run the DNS (change the nameservers at your
   registrar to the four Netlify gives you), or keep your registrar's DNS and add:
   - `A` record for `tumlii.com` pointing to Netlify's load balancer IP shown in the domain panel
   - `CNAME` for `www` pointing to `<your-project>.netlify.app`
5. HTTPS: Netlify issues the certificate automatically once DNS resolves (Domain management > HTTPS).
   `www.tumlii.com` redirects to `tumlii.com` (see `netlify.toml`).

The page is maintained in the app repository (`apps/landing`) and copied here for hosting.
