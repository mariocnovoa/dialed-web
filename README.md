# Dialed on the web

Static pages with no server code, published with GitHub Pages from the public repo
[mariocnovoa/dialed-web](https://github.com/mariocnovoa/dialed-web) at
https://mariocnovoa.github.io/dialed-web/. Only this folder is public; the app's repo stays private.

- `index.html`: a short page about Dialed (the App Store's marketing URL).
- `privacy/`: the privacy policy in English and Spanish (the App Store's privacy policy URL).
  Update it whenever Dialed starts sending or keeping anything new.
- `support/`: help and contact in English and Spanish (the App Store's support URL).
- `r/`: shared recipes, for people who don't have Dialed yet. The app doesn't link here yet (below).

The pages share `page.css` and serve Montserrat from `fonts/` (SIL Open Font License,
`fonts/OFL.txt`), so they make no requests to anyone else. `.nojekyll` makes Pages serve the
folder as it is, `.well-known` included.

To publish a change, run `tools/publish-web.sh "What changed"`. It copies this folder into the
public repo and pushes; Pages updates within a minute or two.

## Recipe links (not turned on)

The recipe travels in the link after `#`, which browsers never send to a server, and
`r/index.html` decodes it in the browser. To have links open Dialed when it's installed and
this page otherwise:

1. Give the site a domain of its own (a custom domain in the repo's Pages settings). Apple reads
   `/.well-known/apple-app-site-association` from the root of a domain, which a project page
   (`…github.io/dialed-web/`) can't serve.
2. Check the app ID in `apple-app-site-association` (`9LUDCHQ74X.com.mariocanas.dialed`) still matches the team and bundle ID.
3. Add the Associated Domains entitlement `applinks:<domain>` to the Dialed app target.
4. Set `SharedRecipe.webLinkBase` to `https://<domain>/r` in DialedCore.

Links already shared as `dialed://r#…` keep working.
