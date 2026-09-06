# Astro template

Static Astro pages, Tailwind CSS, a React blog filter, and Pages CMS. Requires Node.js 22.12+ and npm.

## Template structure

```text
├── .pages.yml                 # CMS editors, reusable fields, uploads
├── astro.config.mjs           # React integration + Tailwind Vite plugin
├── public/
│   ├── favicon.svg            # Site icon
│   └── uploads/               # CMS images → /uploads/...
└── src/
    ├── components/            # Header, footer, intro, grids, post list
    │   └── BlogFilter.tsx     # React island; hydrated only on /blog
    ├── content/blog/          # Markdown posts; filename = URL slug
    ├── content.config.ts      # Blog collection + frontmatter schema
    ├── data/
    │   ├── home.json          # Home sections + metadata
    │   ├── about.json         # About sections + metadata
    │   ├── blog.json          # Blog intro + filter labels + metadata
    │   └── site.json          # Site name, navigation, footer, shared labels
    ├── layouts/Layout.astro   # Document head + shared page shell
    ├── lib/posts.ts           # Published posts, ordering, dates, summaries
    ├── pages/
    │   ├── index.astro        # /
    │   ├── about.astro        # /about
    │   └── blog/
    │       ├── index.astro     # /blog
    │       └── [...slug].astro # /blog/<filename>
    └── styles/global.css      # Tailwind + Markdown styles
```

## Commands

```sh
npm install                    # Install dependencies
npm run dev -- --background    # Start the background dev server
npm run astro -- dev status    # Check server status
npm run astro -- dev logs      # Read server logs
npm run astro -- dev stop      # Stop the server
npm run check                  # Astro + TypeScript diagnostics
npm run build                  # Generate the static site in dist/
npm run preview                # Preview the build locally
```

## Content editing

Push this repository to GitHub, sign in to [Pages CMS](https://app.pagescms.org), authorize the repository, and select its branch. The root `.pages.yml` defines the editors. CMS saves commit files to GitHub; pull changes locally and rebuild to update the site. A Git-connected host can rebuild automatically.

Edit page content under **Home**, **About**, and **Blog page**; edit shared content under **Site settings**. Layout and section order stay in Astro. Highlight/value items can be added, removed, or reordered within their sections.

Create posts under **Blog posts**. Use a lowercase, hyphenated `.md` filename. Titles can change without changing URLs. Drafts are excluded everywhere; publication dates sort posts, with the latest two shown on Home. The body editor saves Markdown and uploads images to `public/uploads`.

To add an editable page, for example `/contact`:

1. Copy `src/data/about.json` to `src/data/contact.json` and adjust its content.
2. Copy `src/pages/about.astro` to `src/pages/contact.astro`; import the new data and adjust its sections.
3. Copy the About entry in `.pages.yml`; set a unique `name`, label, path, and fields matching the JSON.
4. Add the link in `src/data/site.json`. Keep CMS fields and component props aligned when changing content shapes.

References: [Astro](https://docs.astro.build) · [React integration](https://docs.astro.build/en/guides/integrations-guide/react/) · [React](https://react.dev/learn/add-react-to-an-existing-project) · [Tailwind](https://tailwindcss.com/docs/installation/framework-guides/astro) · [Pages CMS](https://pagescms.org/docs/configuration/) · [Astro examples](https://github.com/withastro/astro/tree/main/examples)
