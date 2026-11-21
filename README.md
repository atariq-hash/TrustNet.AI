# TrustNet.AI Lab website

The public website and admin portal for TrustNet.AI Lab. It runs on GitHub Pages with no server and no build step.

| File | What it is |
| --- | --- |
| `index.html` | The public website |
| `admin.html` | The admin portal, where you edit everything |
| `data/lab.json` | All the content: lab profile, people, publications, projects, news, events, workshops, vacancies and collaborators |
| `assets/uploads/` | Photos, logos, banners, CVs and PDFs you upload from the admin portal |

## 1. Put it on GitHub

1. Create a new repository on GitHub, for example `trustnet-lab`.
2. Upload everything in this folder, including the hidden `.nojekyll` file.
3. Open **Settings → Pages**. Under **Build and deployment**, choose **Deploy from a branch**, pick `main` and `/ (root)`, then save.
4. After a minute the site is live at `https://<your-username>.github.io/trustnet-lab/`.

To use your own domain, add it under **Settings → Pages → Custom domain**.

## 2. Connect the admin portal

The admin portal saves your changes straight into the repository, so it needs a GitHub access token.

1. Go to **github.com/settings/personal-access-tokens** and choose **Generate new token** (fine-grained).
2. Under **Repository access**, choose **Only select repositories** and pick this repository.
3. Under **Permissions → Repository permissions**, set **Contents** to **Read and write**.
4. Generate the token and copy it.
5. Open `https://<your-username>.github.io/trustnet-lab/admin.html` and go to **GitHub and AI**.
6. Enter the repository as `your-username/trustnet-lab`, the branch (`main`) and the token. Then select **Save settings** and **Test connection**.

The token is stored only in that browser. Anyone can open `admin.html`, but without your token they can’t publish anything.

## 3. Edit and publish

1. Make changes in the admin portal: add people, papers, workshops, banners, logos and so on.
2. Select **Publish to GitHub** in the sidebar.
3. Uploaded files go into `assets/uploads/`, and the content goes into `data/lab.json`.
4. The live site updates about a minute later. Refresh to see it.

If you haven’t connected GitHub, use **Download lab.json** instead and upload the file into the `data` folder yourself.

## 4. Turn on AI import (optional)

Smart import reads CVs, publication lists, calls for papers, flyers and job ads, and fills in the right sections for you.

1. Get an API key at **console.anthropic.com**. Usage is billed to your Anthropic account.
2. In the admin portal, open **GitHub and AI** and paste the key.
3. Leave the model as it is unless you want a different Claude model.

The key stays in your browser and is sent only to Anthropic. On the public site, the question box works as a search across your content, so visitors never use your key.

## Moving content from the claude.ai version

In the claude.ai admin portal, select **Download data for GitHub** in the sidebar. Replace `data/lab.json` in your repository with the downloaded `lab.json`. Images in that file are embedded. The next time you select **Publish to GitHub**, they’re moved into `assets/uploads/` automatically.

## Previewing on your own computer

Browsers block pages opened straight from disk from reading `data/lab.json`. Run a small local server in this folder instead:

```
python3 -m http.server 8000
```

Then open `http://localhost:8000`.
