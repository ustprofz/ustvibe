# VIBE Lab — ustvibe.org

A minimal, mobile-friendly VIBE Lab website with the University of St. Thomas logo, the full name Ventures in Business Engineering, and links to UST, Opus College of Business, and the Opus Way of Teaching. No installation, build process, or paid hosting is required.

## 1. Put the files on GitHub

These instructions assume your GitHub account is `ustprofz`. If you use another account, replace that username wherever it appears below.

1. Sign in at https://github.com/ and create a **new public repository** named `ustvibe`. This keeps this simple domain landing page separate from your existing detailed VIBE website.
2. Extract `USTVIBE_GitHub.zip` on your computer.
3. In the repository, choose **Add file → Upload files**. Upload the extracted files and the `assets` folder, then commit the changes to `main`.
4. Check that `index.html` is at the top level of the repository, alongside `CNAME` and `README.md`. The logo should be at `assets/ust-logo.png`. Upload the contents, not the ZIP or an enclosing folder.
5. The package also includes `.nojekyll`, which may be hidden on your computer. Include it if visible; this plain HTML page will also work without it.

## 2. Enable GitHub Pages and set the domain

1. In the **repository**, open **Settings → Pages**.
2. Under **Build and deployment**, choose **Deploy from a branch**.
3. Choose branch **main**, folder **/(root)**, then click **Save**.
4. Under **Custom domain**, enter `ustvibe.org` and click **Save**. Do this before changing your domain's DNS records. The included `CNAME` file already contains this domain, but confirm it also appears in the settings.
5. GitHub may initially report that DNS is not configured. Continue to the next section.

## 3. Connect your domain's DNS

Open the company where you registered `ustvibe.org`. Find the domain's **DNS**, **Manage DNS**, or **DNS records** screen. If you use a separate DNS provider, make these changes there instead.

Create these five records:

| Type | Host / Name | Value / Target |
| --- | --- | --- |
| A | @ | 185.199.108.153 |
| A | @ | 185.199.109.153 |
| A | @ | 185.199.110.153 |
| A | @ | 185.199.111.153 |
| CNAME | www | ustprofz.github.io |

- `@` means the root domain, `ustvibe.org`. Some providers ask you to leave the host blank instead.
- Leave TTL at the provider's default or automatic setting.
- The `www` CNAME target is your GitHub account hostname: **no `https://`, no repository name, and no slash**.
- Replace conflicting parking or old website records for `@` and `www`. Turn off registrar URL forwarding for these names if it is enabled. Keep unrelated email (MX) and verification (TXT) records.
- Do not add a wildcard record. You do not need to change nameservers or purchase website hosting.

This connects your domain directly to GitHub Pages: visitors keep `ustvibe.org` in the address bar. You do not need the registrar's URL-forwarding service.

## 4. Enable HTTPS and check the result

1. Return to the repository's **Settings → Pages** and let GitHub complete its DNS check and certificate setup.
2. Select **Enforce HTTPS** when it becomes available.
3. Test `https://ustvibe.org` and `https://www.ustvibe.org`. With the DNS records above, GitHub automatically redirects the `www` version to the root domain.

DNS changes can take up to 24 hours, and the HTTPS option can also take up to 24 hours to become available. A temporary DNS or certificate warning during setup does not necessarily mean the records are wrong.

## Recommended: verify domain ownership

GitHub recommends verification to protect your domain from being claimed by another GitHub account.

1. Open your GitHub **profile picture → Settings → Pages**. This is your account settings page, not the repository settings page.
2. Click **Add a domain**, enter `ustvibe.org`, then follow GitHub's instructions.
3. At your DNS provider, add the **TXT** record with the exact name and value GitHub shows. This is an additional record, separate from the five website records above.
4. Return to GitHub and click **Verify** when the TXT record has propagated. Keep that TXT record afterward.

## Updating the page later

Edit or replace `index.html` in this repository and commit the change to `main`. GitHub Pages republishes automatically. Check the repository's **Actions** tab for the deployment result, then refresh the page; a hard refresh can clear an older cached copy. Keep `CNAME` and `assets/ust-logo.png` in place.

## Troubleshooting

- **404:** Confirm Pages uses `main` and `/(root)`, and that `index.html` is directly at the repository root. Check the latest Pages deployment under Actions.
- **Missing logo:** Confirm `assets/ust-logo.png` was uploaded with exactly that capitalization.
- **DNS check fails:** Recheck all four A records, the `www` CNAME, and the account username. Remove conflicting old web records. If old AAAA records point to a different host, remove them or use GitHub's documented IPv6 addresses. Keep email and verification records.
- **Domain already in use:** Ensure no other repository has `ustvibe.org` configured. One custom domain can point to only one Pages site at a time. Account-level domain verification can help resolve ownership issues.
- **HTTPS unavailable:** Wait for DNS propagation and certificate issuance, then revisit Pages settings.
- **Registrar has different labels:** Host, name, and record name usually mean the same thing; value, target, and points to usually mean the destination.

## Official references

- Creating a Pages site: https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site
- Custom domain and DNS setup: https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site
- Domain verification: https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/verifying-your-custom-domain-for-github-pages

The files are ready to publish; uploading them and configuring GitHub/DNS must be done in your own accounts.
