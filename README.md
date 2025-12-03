# Makinde Transition - Policy for Progress

A presidential campaign website showcasing policy suggestions for Education and Healthcare reform.

## Features

- Hero section with candidate photo and campaign branding
- Statistics section highlighting health disparities
- Policy areas with expandable dropdown sections
- Clean, modern design inspired by transition2025.com
- Responsive layout for all devices
- GitHub Pages ready

## Adding Your Photo

1. Add your photo to the `public/` folder
2. Name it `candidate-photo.jpg` (or update the filename in `src/App.vue`)
3. Recommended: Use a portrait-oriented photo (4:5 aspect ratio works best)

## Development

### Install Dependencies

```bash
npm install
```

### Run Development Server

```bash
npm run dev
```

### Build for Production

```bash
npm run build
```

## Deployment to GitHub Pages

1. Update the `base` path in `vite.config.js` to match your repository name (currently set to `/makinde-transition/`)

2. Build the project:
   ```bash
   npm run build
   ```

3. Push the `dist` folder contents to the `gh-pages` branch, or use GitHub Actions:

   Create `.github/workflows/deploy.yml`:
   ```yaml
   name: Deploy to GitHub Pages
   
   on:
     push:
       branches: [ main ]
   
   jobs:
     deploy:
       runs-on: ubuntu-latest
       steps:
         - uses: actions/checkout@v3
         - uses: actions/setup-node@v3
           with:
             node-version: '18'
         - run: npm install
         - run: npm run build
         - uses: peaceiris/actions-gh-pages@v3
           with:
             github_token: ${{ secrets.GITHUB_TOKEN }}
             publish_dir: ./dist
   ```

4. Enable GitHub Pages in your repository settings:
   - Go to Settings → Pages
   - Source: Deploy from a branch
   - Branch: `gh-pages` / `root`

## Policy Areas

### Education
Decoupling school funding from property taxes to ensure equitable distribution of resources and better education for all children.

### Healthcare
Ensuring access to life-saving care regardless of employment status, addressing health disparities that disproportionately affect Black communities.

### Community & Housing
Investing in community infrastructure, including sidewalks and public spaces, to support healthy development in all neighborhoods.

## Sources

- [Structural Racism Research](https://pmc.ncbi.nlm.nih.gov/articles/PMC11393777/)
- [CDC Health Disparities Report](https://www.cdc.gov/nchs/data/nvsr/nvsr72/nvsr72-10.pdf)

