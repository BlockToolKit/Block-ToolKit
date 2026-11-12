# BlockToolKit

> A Minecraft Bedrock-focused website for mods, add-ons, installation guides, tools, memberships, and community resources.

BlockToolKit is built as a responsive web experience for the Minecraft Bedrock community. The current site includes a mod catalog, mod detail/download flow, Bedrock-focused tools, installation guides, account/profile functionality, membership pages, community information, reporting/contact forms, and responsive navigation.

## ✨ Features

- 🧱 **Minecraft Bedrock mod/add-on catalog**
  - Mod cards with authors, descriptions, tags, ratings, download counts, and update dates.
  - Search and category filtering.
  - Featured add-on carousel with navigation, dots, autoplay, keyboard support, and swipe interaction.
- 🛠️ **Bedrock tools**
  - UUID generator.
  - `manifest.json` generator.
  - JSON formatter/minifier with Bedrock-friendly comment stripping.
- 📦 **Mod download system**
  - Mod-specific download pages.
  - Secure download-link retrieval through Supabase RPC.
  - Support for different download/pass tiers.
- 📖 **Installation guides**
  - Device/type-based installation flow.
  - Video-based guides.
- 👤 **Accounts and profiles**
  - Sign in/out.
  - User profiles.
  - Profile avatar, banner, bio, rank, and social links.
- 🎨 **Interface settings**
  - Dark mode.
  - Light mode.
  - System theme.
  - PC/mobile card display modes.
  - Saved preferences using `localStorage`.
- 📱 **Responsive design**
  - Desktop navigation.
  - Mobile bottom navigation.
  - Compact mobile mod cards.
  - Responsive layouts for different screen sizes.
- 🌐 **Community**
  - Partners.
  - Community helpers and contributors.
  - Social links for the BlockToolKit brand.
- 🛡️ **Safety and validation**
  - HTTP/HTTPS URL validation for profile links.
  - Authentication state synchronization.
  - Report/contact cooldown handling.
  - Custom 404 page with page suggestions.

The homepage identifies BlockToolKit as an independent Minecraft Bedrock project and states that it is **not an official Minecraft product and is not approved by or associated with Mojang or Microsoft**.

## 🖥️ Pages

The current project contains pages for:

| Page | Purpose |
|---|---|
| `index.html` | Homepage |
| `addons.html` | Mods/add-ons catalog |
| `mod.html` | Individual mod details |
| `download.html` | Mod download flow |
| `install.html` | Installation guides |
| `tools.html` | Bedrock tools |
| `membership.html` | Membership/ranks |
| `about.html` | About BlockToolKit |
| `contact.html` | Contact |
| `report.html` | Bug/report form |
| `changelog.html` | Changelog |
| `login.html` | Authentication |
| `profile.html` | User profile |
| `terms.html` | Terms of Service |
| `policy.html` | Privacy Policy |

## 🧩 Tech Stack

BlockToolKit currently uses:

- **HTML5**
- **CSS3**
- **JavaScript**
- **Tailwind CSS**
- **Font Awesome**
- **Mojangles font**
- **Supabase**
  - Authentication
  - User profiles
  - Database-backed mod/download functionality
  - RPC functions
- **DiceBear** for fallback/generated profile avatars
- **YouTube** video embeds/links for installation content

The site is primarily a client-side web application, with Supabase providing the backend services required for authentication, profiles, and protected download-link functionality.

## 📁 Project Structure

A simplified structure looks like this:

```text
BlockToolKit/
├── index.html
├── addons.html
├── mod.html
├── download.html
├── install.html
├── tools.html
├── membership.html
├── about.html
├── contact.html
├── report.html
├── changelog.html
├── login.html
├── profile.html
├── terms.html
├── policy.html
│
├── script.js
├── pages.js
├── mods-data.js
├── style.css
│
├── images/
├── fonts/
└── README.md
```

Your deployed repository may contain additional assets and pages beyond this simplified structure.

## ⚙️ Configuration

### Supabase

The site uses Supabase for backend functionality.

The shared JavaScript initializes a Supabase client and uses it for authentication and database/RPC operations.

Before deploying your own instance, configure:

- Supabase project URL
- Supabase public anon key
- Authentication settings
- Required database tables
- Required RPC functions
- Row Level Security (RLS) policies

Do **not** put a Supabase `service_role` key or any other privileged secret in frontend JavaScript.

The browser-side Supabase anon key is designed to be public, but your database and storage security must be enforced with proper RLS/policies.

### Database

The current code expects backend functionality for areas including:

- User profiles
- Authentication
- Messages
- Reports
- Pack/download links
- Download/pass logic

The exact database schema and SQL setup should be kept with the backend/deployment configuration rather than hard-coded into this README.

## 🚀 Running Locally

Because this is a static/client-side website with JavaScript modules and external services, using a local web server is recommended instead of opening `index.html` directly.

For example:

```bash
# Python
python -m http.server 8000
```

Then open:

```text
http://localhost:8000
```

You can also use VS Code Live Server or another local development server.

## 🌍 Deployment

BlockToolKit can be deployed to a static hosting provider capable of serving HTML, CSS, JavaScript, fonts, and images.

Typical deployment steps:

1. Upload/push the project files.
2. Configure the production Supabase project.
3. Configure authentication redirect URLs.
4. Configure the database/RLS/RPC functions.
5. Verify all asset paths.
6. Test authentication.
7. Test profile pages.
8. Test mod pages and downloads.
9. Test installation videos.
10. Test the site on desktop and mobile.

## 🧑‍💻 Development

The project separates most shared behavior into:

- `script.js` — shared site functionality, Supabase initialization, authentication synchronization, theme/view preferences, navigation behavior, and the featured carousel.
- `pages.js` — page-specific functionality such as tools, mods, downloads, profiles, installation flows, forms, and the 404 system.
- `style.css` — the unified visual system and responsive layouts.
- `mods-data.js` — catalog metadata used by mod/download pages.

The mod catalog data includes fields such as:

```js
{
  name: "Example Add-on",
  author: "Creator",
  description: "Example description",
  downloads: "10K",
  updated: "November 1, 2026",
  rating: "4.8",
  tags: ["Addons", "Utility"],
  image: "https://example.com/image.jpg",
  levi: false
}
```

Download URLs are intentionally handled separately from the public catalog metadata.

## 🎨 Design

BlockToolKit uses a Minecraft-inspired visual identity while keeping the interface modern and practical.

Key design characteristics include:

- Green BlockToolKit accent color.
- Dark and light themes.
- Mojangles typography for major Minecraft-styled headings.
- Responsive card layouts.
- Pixel-friendly image rendering where appropriate.
- Desktop and mobile-specific UI behavior.
- Minimal, functional controls rather than excessive decoration.

## 🔐 Security Notes

If you fork or deploy this project:

- Never expose privileged backend/service keys.
- Keep Supabase RLS enabled and correctly configured.
- Validate user-controlled URLs.
- Validate and sanitize user-generated content.
- Keep download authorization on the server/backend side.
- Do not trust client-side membership/rank information for protected resources.
- Configure authentication redirect URLs for your production domain.
- Review database policies before opening the site publicly.

## 📣 Socials

BlockToolKit has a separate social identity from the personal creator/developer identity.

### 👤 Personal

These are intended for the creator/developer behind BlockToolKit:

- YouTube: `ADD_PERSONAL_YOUTUBE_URL`
- Instagram: `ADD_PERSONAL_INSTAGRAM_URL`
- X: `ADD_PERSONAL_X_URL`
- GitHub: `ADD_PERSONAL_GITHUB_URL`
- Other: `ADD_PERSONAL_SOCIAL_URL`

> Replace the placeholders above with your actual personal accounts.

### 🟩 BlockToolKit

The current website already links to these BlockToolKit accounts:

- Discord — https://discord.gg/blocktoolkit
- WhatsApp Channel — https://whatsapp.com/channel/blocktoolkit
- YouTube — https://youtube.com/@blocktoolkit
- X — https://x.com/blocktoolkit
- Instagram — https://instagram.com/blocktoolkit
- Bluesky — https://bsky.app/profile/blocktoolkit.bsky.social
- Reddit — https://reddit.com/r/blocktoolkit
- GitHub — https://github.com/blocktoolkit
- Facebook — https://facebook.com/blocktoolkit
- Threads — https://threads.net/@blocktoolkit
- Telegram — https://t.me/blocktoolkit
- Twitch — https://twitch.tv/blocktoolkit

## 🤝 Contributing

Contributions, bug reports, testing, translations, and community feedback are welcome.

Before submitting a change:

1. Test the affected page.
2. Check desktop and mobile layouts.
3. Check both dark and light themes when relevant.
4. Make sure existing navigation still works.
5. Avoid breaking authentication or Supabase-dependent functionality.
6. Keep new UI consistent with the BlockToolKit design system.

For bugs, use the site's report functionality or open an issue in the project repository if enabled.

## 📄 License

Add the project's chosen license here before publishing the repository.

For example:

```text
Copyright © 2026 BlockToolKit.

All rights reserved.
```

If you want the source code to be reusable by others, choose and add an appropriate open-source license instead.

## ⚠️ Minecraft Disclaimer

Minecraft is a trademark of Mojang Studios and Microsoft.

BlockToolKit is an independent community project and is **not an official Minecraft product**. It is **not approved by or associated with Mojang or Microsoft**.

---

**BlockToolKit — tools, mods, and resources for Minecraft Bedrock.**
