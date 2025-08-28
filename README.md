# Modern Website Template

A production-ready, modern website template built with **React + TypeScript** featuring rapid rebranding, reusable sections, and great defaults.

## ✨ Features

- **🚀 Rapid Rebranding** - Centralize all brand controls in `src/site.config.ts`
- **🧩 Reusable Sections** - Composable blocks with props for quick rearrange
- **🎨 Great Defaults** - Clean, airy layout with tasteful motion and accessible colors
- **🎭 Dual Styling Tracks** - Choose between Tailwind CSS or CSS Modules
- **📱 Responsive Design** - Mobile-first approach with modern breakpoints
- **♿ Accessibility First** - WCAG compliant with proper focus states and ARIA labels
- **🔒 Type Safety** - Strict TypeScript with no `any` or non-null assertions
- **🧪 Testing Ready** - Vitest setup with component testing examples

## 🚀 Quick Start

### Prerequisites

- Node.js 18+ 
- npm or yarn
- Windows 11 + PowerShell (recommended)

### Installation

1. **Clone the repository**
   ```bash
   git clone <your-repo-url>
   cd modern-website-template
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Start development server**
   ```bash
   npm run dev
   ```

4. **Open your browser**
   Navigate to `http://localhost:3000`

## 🎨 How to Rebrand

Everything is controlled from **one file**: `src/site.config.ts`

### Brand Configuration
```typescript
brand: {
  name: 'Your Company Name',
  tagline: 'Your company tagline',
  logo: {
    light: '/brand/logo-light.svg',
    dark: '/brand/logo-dark.svg',
  },
  favicon: '/brand/favicon.svg',
  domain: 'https://yoursite.com',
}
```

### Theme Colors
```typescript
theme: {
  colors: {
    primary: {
      500: '210 40% 50%', // HSL values
      600: '210 40% 40%',
    },
    // ... more colors
  }
}
```

### Feature Toggles
```typescript
features: {
  heroVideo: true,      // Enable/disable hero video
  testimonials: true,   // Show/hide testimonials
  pricing: true,        // Show/hide pricing table
  ctaRibbon: true,      // Show/hide CTA section
  blogStub: false,      // Enable/disable blog stub
}
```

## 🔄 How to Reorder/Remove Sections

Edit `src/pages/HomePage.tsx` to rearrange or remove sections:

```typescript
const HomePage: React.FC = () => {
  return (
    <div className="min-h-screen">
      {/* Reorder these sections as needed */}
      <Hero />
      <FeatureGrid />
      <Stats />
      <Steps />
      
      {/* Conditionally show sections */}
      {siteConfig.features.testimonials && <TestimonialMarquee />}
      {siteConfig.features.pricing && <PricingTable />}
      
      <FAQ />
      {siteConfig.features.ctaRibbon && <CTA />}
    </div>
  )
}
```

## 📄 How to Add a New Page

1. **Create the page component** in `src/pages/`
2. **Add the route** in `src/App.tsx`
3. **Update navigation** in `src/components/layout/Header.tsx`
4. **Add route meta** in `src/pages/routes.tsx`

### Example: Adding a Blog Page

```typescript
// src/pages/BlogPage.tsx
const BlogPage: React.FC = () => {
  return (
    <div className="min-h-screen">
      {/* Your blog content */}
    </div>
  )
}

export default BlogPage

// src/App.tsx
const BlogPage = lazy(() => import('./pages/BlogPage'))

// Add to routes
<Route path="/blog" element={<BlogPage />} />
```

## 🎨 How to Switch Styling Track

Toggle between Tailwind and CSS Modules in `src/site.config.ts`:

```typescript
export const siteConfig: SiteConfig = {
  // ... other config
  useTailwind: true, // Set to false for CSS Modules
}
```

### Track A: Tailwind CSS (Default)
- Uses `src/styles/tailwind.css`
- Utility-first approach
- Design tokens via CSS variables

### Track B: CSS Modules
- Uses `src/styles/tokens.css` + `src/styles/globals.css`
- Component-scoped styles
- Same design tokens, different implementation

## 📧 How to Wire Real Email

The contact form includes examples for multiple email services:

### Option 1: Resend (Recommended)
```bash
npm install resend
```

```typescript
// Uncomment in src/api/contact.ts
import { Resend } from 'resend'
const resend = new Resend(import.meta.env.VITE_RESEND_API_KEY)
```

### Option 2: EmailJS
```bash
npm install @emailjs/browser
```

### Option 3: Netlify Functions
Create `netlify/functions/contact.js`

### Option 4: Vercel Edge Functions
Create `api/contact.ts`

## 🧪 Testing

### Run Tests
```bash
npm test
```

### Run Tests in Watch Mode
```bash
npm test -- --watch
```

### Run Tests with Coverage
```bash
npm test -- --coverage
```

## 📦 Build & Deploy

### Build for Production
```bash
npm run build
```

### Preview Production Build
```bash
npm run preview
```

### Deploy
The built files are in the `dist/` folder. Deploy to your preferred hosting service:

- **Vercel**: `vercel --prod`
- **Netlify**: Drag `dist/` folder to Netlify
- **AWS S3**: Upload `dist/` contents to S3 bucket
- **GitHub Pages**: Push to `gh-pages` branch

## 🛠️ Available Scripts

```bash
npm run dev          # Start development server
npm run build        # Build for production
npm run preview      # Preview production build
npm run lint         # Run ESLint
npm run format       # Run Prettier
npm test             # Run tests
```

## 📁 Project Structure

```
src/
├── components/          # Reusable UI components
│   ├── common/         # Shared components (Button, ErrorBoundary)
│   ├── layout/         # Layout components (Header, Footer)
│   └── sections/       # Page sections (Hero, FeatureGrid, etc.)
├── contexts/           # React contexts (ThemeContext)
├── lib/                # Utility functions
├── pages/              # Page components
├── styles/             # CSS files
├── test/               # Test setup
├── App.tsx             # Main app component
├── main.tsx            # Entry point
└── site.config.ts      # Central configuration
```

## 🎯 Key Components

- **Header** - Sticky navigation with theme switch
- **Hero** - Compelling headline with optional video background
- **FeatureGrid** - 3-6 feature items with icons
- **Stats** - Animated counters with intersection observer
- **Steps** - How-it-works with numbered progression
- **TestimonialMarquee** - Auto-scrolling testimonials
- **PricingTable** - 3-tier pricing with monthly/annual toggle
- **FAQ** - Radix Accordion for questions
- **CTA** - Full-bleed gradient call-to-action
- **ContactForm** - React Hook Form + Zod validation
- **Footer** - Links, social icons, copyright

## 🔧 Customization

### Adding New Sections
1. Create section component in `src/components/sections/`
2. Add to `src/pages/HomePage.tsx`
3. Optionally add feature toggle in `site.config.ts`

### Modifying Design Tokens
Edit CSS variables in:
- `src/styles/tailwind.css` (Track A)
- `src/styles/tokens.css` (Track B)

### Adding New Routes
1. Create page component
2. Add to `src/App.tsx` routes
3. Update navigation in Header
4. Add route meta in `routes.tsx`

## 🚀 Performance Features

- **Lazy Loading** - All pages are lazy-loaded
- **Code Splitting** - Vendor chunks for better caching
- **Image Optimization** - Responsive images with proper alt text
- **Reduced Motion** - Respects user preferences
- **Intersection Observer** - Efficient scroll animations

## 🔒 Security Features

- **Type Safety** - No `any` types or unsafe assertions
- **Input Validation** - Zod schemas for form validation
- **Error Boundaries** - Graceful error handling
- **XSS Prevention** - Proper content sanitization

## 📱 Browser Support

- Chrome 90+
- Firefox 88+
- Safari 14+
- Edge 90+

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests for new functionality
5. Ensure all tests pass
6. Submit a pull request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🆘 Support

- **Documentation**: Check this README and code comments
- **Issues**: Create a GitHub issue for bugs or feature requests
- **Discussions**: Use GitHub Discussions for questions

## 🙏 Acknowledgments

- **React** - UI library
- **TypeScript** - Type safety
- **Vite** - Build tool
- **Tailwind CSS** - Utility-first CSS
- **Radix UI** - Accessible components
- **Framer Motion** - Animations
- **React Hook Form** - Form handling
- **Zod** - Schema validation

---

Built with ❤️ using modern web technologies
