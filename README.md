# Adoption Agent Assets

Public image host for Copilot Studio Adaptive Card banners. Use the `raw.githubusercontent.com` URLs.

Why this repo is public: Teams fetches card images anonymously. A OneDrive or SharePoint link that needs sign-in renders as a blank banner. A public GitHub raw URL works.

**Only artwork belongs here.** No customer names, internal data, prompts, config or logs. Everything in this repo is world-readable.

## Agents that use this repo

| Agent | Folder | Images |
|---|---|---|
| Customer Copilot Adoption Coach | `branding/sales/` | `sales-hero.png` |
| Frontier Sales Home Cards | `branding/frontier-sales-home/` | one banner per function, see below |

## URL pattern

```
https://raw.githubusercontent.com/adamroche-assets/adoption-agent-assets/main/<folder>/<file>
```

Example:

```
https://raw.githubusercontent.com/adamroche-assets/adoption-agent-assets/main/branding/sales/sales-hero.png
```

## Frontier Sales Home Cards

Six role images, one per card function. Published in `branding/frontier-sales-home/`.

| Function | File (version 1) |
|---|---|
| General | `img_general_v1.jpg` |
| AE | `img_ae_v1.jpg` |
| AI Workforce | `img_ai-workforce_v1.jpg` |
| AIBP | `img_aibp_v1.jpg` |
| CPAI | `img_cpai_v1.jpg` |
| Security | `img_security_v1.jpg` |

Spec: square JPEG, 800 x 800, under 1 MB (about 100 KB each), no text inside the image. The card shows it as a 112 px thumbnail beside the title.

## How to use the repo from an agent

1. Add the image under the agent's folder. Use a versioned filename.
2. Build the raw URL from the pattern above.
3. Set it as the card's hero image variable (for example `hero_image_url`) in the agent's config or card template.
4. Open the raw URL in a private browser window. It must load without signing in.
5. Send a test card to a test chat and confirm the banner shows before any live send.

Adaptive Card image element:

```json
{ "type": "Image", "url": "https://raw.githubusercontent.com/adamroche-assets/adoption-agent-assets/main/branding/frontier-sales-home/img_ae_v1.jpg", "size": "Stretch", "altText": "Role mascot" }
```

## Rules

- **Never overwrite a published file.** Teams caches images. To change a banner, add a new version (`_v2`) and update the card to point to it.
- Keep each file under 1 MB. Large banners slow card rendering in Teams.
- One folder per agent under `branding/`. Do not mix agents in a folder.
- Do not rename or delete a file that a live card still points to.
- Do not put screenshots of internal tools or any customer content in an image.