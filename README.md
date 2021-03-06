# 🚀 Application Deployment Preflight Checklist

Use this list to track completion of important tasks prior to launching a new project. 

## 1. Front-end

### Assets
- [ ] Search sources for `http://`. Replace by `https://`
- [ ] Lint (s)css sources
- [ ] Webfonts: is the live domain configured in services like Typekit, Fonts.com etc.?
- [ ] Is the browserlist properly configured for autoprefixer and babel-preset-env?
- [ ] When using PurgeCSS: check if layout is preserved.

### Meta
- [ ] Check page titles / descriptions.
- [ ] Facebook / Twitter Card tags are present.
- [ ] Favicons are present. *Pin the tab in Chrome to check pinned icon*.
- [ ] Is the `viewport` tag present and configured

### Scripts
- [ ] Is `package-lock.json` present?
- [ ] Check JS lint errors. Remove all `console.log` lines in scripts
- [ ] Check for console errors

### Performance Audit
- [ ] Evaluate total size of at least homepage
- [ ] Open Inspector network/timeline tab to identify heavy assets 
- [ ] Check if heavy assets are cached 
- [ ] Use the Chrome DevTools and perform a mobile audit (with throttling) to fix common problems.
- [ ] Repeat with a desktop audit.

### Check content (with an open console)
- [ ] Are all strings / images present (and translated)?
- [ ] Does menu/submenu have a correct active state on every page?
- [ ] Are 404, 500 and 503 pages provided? Do they provide useful content like 'back to home', search or a navigation tree?
- [ ] Check all pages for n+1 problems


### Components
- [ ] Google Maps
    - [ ] API key needed/configured?
    - [ ] Check info windows
    - [ ] Prevent zoom out beyond 1x world
    - [ ] Try clicking on markers
- [ ] Forms: fill out with wrong/right values
- [ ] Video: check with sound on
- [ ] Try subscribing to a newsletter with incorrect & correct email (use correct mail twice to get 'already subscribed' message)
- [ ] Check layout of emails
- [ ] Check structured data for news, events, products,... https://search.google.com/structured-data/testing-tool/

### Server, DNS & Services
- [ ] Add redirects from old to new pages if necessary.
- [ ] Install Let's Encrypt certificate
- [ ] Check SSL certificate health https://www.ssllabs.com/ssltest/
- [ ] Try visiting `www` domain, should redirect to `non-www`
- [ ] Try out visiting `http`, should redirect to `https`
- [ ] Verify that all http status codes are ok with https://github.com/spatie/http-status-check
- [ ] Scan for mixed content with https://github.com/spatie/mixed-content-scanner-cli
- [ ] Verify that the content of robots header is current with `curl-I https://url` on `x-robots-tag`
- [ ] Remove development DNS record
- [ ] Check dns propagation with https://www.whatsmydns.net/
- [ ] Verify Tag Manager / Analytics have been correctly set up

### Google Search Console
- [ ] Submit all www/non-www http/https variations
- [ ] Set up non-www https as the preferred domain 
- [ ] Crawl > Fetch as Google > Submit to index to kickstart index

### Server
- [ ] Are DigitalOcean backups enabled?
- [ ] Are Amazon backups enabled?
- [ ] Is the output of artisan task `backup:run` ok?
- [ ] Is artisan scheduled on Forge?
- [ ] Is Horizon configured in Supervisor on Forge? Command should be `php artisan horizon`. Path should be `/home/forge/my-new-site.com/current`
- [ ] Is the url being monitored by [Oh Dear!](https://ohdearapp.com/)?
- [ ] Is the server being monitored by our server-monitor?

### Github
- [ ] Remove `develop` branch or other stale branches 
