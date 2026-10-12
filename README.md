# VRPLAY project website

Static website for the VRPLAY honours project (UCT Computer Science, 2026).

## Rules this site has to follow

The department's brief requires the site to be completely static (HTML and CSS only), self-contained, and built with relative links only. That means:

- No JavaScript frameworks, no server-side code.
- No external fonts, stylesheets or scripts. Everything the site needs lives in this folder.
- Links to files inside the site are relative (`docs/paper.pdf`, not `/docs/paper.pdf`). Root-absolute links break on GitHub Pages.
- Documents go in `docs/` as PDF. Code archives go in `code/` as ZIP.
- Every page must pass the W3C validator: https://validator.w3.org/

## Folder layout

```
index.html                  Project (group) page. Entry point.
apple-interaction.html      Zenande's environment page
water-balloon-fight.html    Devin's environment page
bunny-rally.html            Karla's environment page
method.html                 Shared study design, instruments, hypotheses and analysis rules
resources.html              Index of every document and code archive
contact.html                Team and supervisor
css/style.css               The only stylesheet
img/                        Screenshots, logo, placeholder image
docs/                       PDFs
code/                       Zipped source code
```

## Editing your environment page

Open your page in any text editor. Every block that still needs content is marked with `class="todo"` and shows up on the live site as muted italic text. Replace the placeholder text and remove `class="todo"` from that element. For screenshots, drop the image into `img/`, point the `<img src="...">` at it, and write a proper `alt` description.

To add a document: put the PDF in `docs/`, then change the table row from

```html
<tr><td>Final paper <span class="todo">file to be added</span></td><td>PDF</td></tr>
```

to

```html
<tr><td><a href="docs/your_file.pdf">Final paper</a></td><td>PDF</td></tr>
```

Also add the same link on `resources.html` under your name.

## Adding your source code

Make a zip of your C# scripts, the `ProjectSettings` folder and `Packages/manifest.json`, with a short `README.txt` at the top level (what is included, which Unity version and packages, and that assets are excluded for size). Leave out `Library`, `Temp`, `Logs`, `obj`, `Builds` and everything else under `Assets`. On a Mac, zip from Terminal so no `__MACOSX` folder is added. `code/WaterBalloonFight_source.zip` is an example to copy.

1. Put the zip in the `code/` folder of the repo.

2. On your environment page, under the "Source code" heading, replace

   ```html
   <p class="todo">Link to the compressed source archive for this environment: file to be added.</p>
   ```

   with (change the filename, size and script count to yours)

   ```html
   <p><a href="code/BunnyRally_source.zip">BunnyRally_source.zip</a> (80 KB): 22 C# scripts, the Unity project settings, the package manifest and a README.</p>
   ```

   Leave the note underneath it in place.

3. On `resources.html`, in the table under your name, replace

   ```html
   <tr><td>Source code <span class="todo">file to be added</span></td><td>ZIP</td></tr>
   ```

   with

   ```html
   <tr><td><a href="code/BunnyRally_source.zip">Source code</a></td><td>ZIP</td></tr>
   ```

Then push, hard-refresh the live site, click both links to confirm the zip downloads, and run your page through https://validator.w3.org/.

## Publishing on GitHub Pages

1. Push this folder to the `main` branch of the `vrplay-website` repository (the files must sit at the repository root, not inside a subfolder).
2. In the repository settings, open Pages, set the source to "Deploy from a branch", pick `main` and `/ (root)`, and save.
3. The site appears at `https://<username>.github.io/vrplay-website/` within a minute or two. Every push to `main` redeploys.

The `.nojekyll` file tells GitHub to serve the files exactly as they are.

## Submitting

Zip the contents of this folder (not the folder itself, so `index.html` is at the top level of the zip), name it `vrplay_mdludlu_alaro_marais.zip`, and upload at http://projects.cs.uct.ac.za/honsproj/ under 2026. Delete `README.md` and `.nojekyll` from the copy you submit; they are harmless but unnecessary.
