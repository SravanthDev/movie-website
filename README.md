# 🎬 MovieFinder

A modern movie discovery app built with React 19, featuring real-time search with debouncing and search analytics tracking via Appwrite.

![React](https://img.shields.io/badge/React-19.1.0-61DAFB?logo=react)
![Vite](https://img.shields.io/badge/Vite-6.3.5-646CFF?logo=vite)
![TailwindCSS](https://img.shields.io/badge/Tailwind-4.1.11-06B6D4?logo=tailwindcss)
![Appwrite](https://img.shields.io/badge/Appwrite-18.1.1-F02E65?logo=appwrite)

## ✨ Features

- **Real-time Search** — Search through TMDB's extensive movie database with instant results
- **Debounced API Calls** — Optimized network requests using `react-use` hooks (500ms debounce)
- **Search Analytics** — Tracks popular search terms in Appwrite database
- **Responsive Grid** — Adaptive layout: 1 → 2 → 3 → 4 columns based on viewport
- **Movie Cards** — Displays poster, rating, language, and release year
- **Error Handling** — Graceful fallbacks for missing posters and API failures

## 🛠 Tech Stack

| Layer | Technology |
|-------|------------|
| Framework | React 19 with Vite |
| Styling | Tailwind CSS 4 (custom theme with @theme) |
| API | TMDB (The Movie Database) |
| Backend | Appwrite Cloud (search count tracking) |
| Utilities | react-use (useDebounce) |

## 📁 Project Structure

```
src/
├── App.jsx           # Main app with search & movie fetching logic
├── appwrite.js       # Appwrite client & search analytics
├── index.css         # Tailwind config with custom design tokens
├── main.jsx          # React DOM entry point
└── components/
    ├── MovieCard.jsx # Individual movie display component
    ├── Search.jsx    # Controlled search input
    └── Spinner.jsx   # Loading state indicator
```

## 🚀 Quick Start

```bash
# Clone the repository
git clone <repo-url>
cd movie-website

# Install dependencies
npm install

# Set up environment variables
cp .env.local.example .env.local
# Add your TMDB API key and Appwrite credentials

# Start development server
npm run dev
```

## 🔐 Environment Variables

```env
VITE_TMDB_API_KEY=your_tmdb_bearer_token
VITE_APPWRITE_PROJECT_ID=your_appwrite_project_id
VITE_APPWRITE_DATABASE_ID=your_database_id
VITE_APPWRITE_COLLECTION_ID=your_collection_id
```

## 🔑 Key Implementation Details

### Debounced Search
```jsx
const [debouncedSearchTerm, setDebouncedSearchTerm] = useState('')
useDebounce(() => setDebouncedSearchTerm(searchTerm), 500, [searchTerm])
```
Prevents excessive API calls while user is typing.

### TMDB API Integration
- Uses Bearer token authentication
- Fetches popular movies on initial load
- Switches to search endpoint when query is provided

### Search Analytics (Appwrite)
Tracks which movies are being searched:
- If search term exists → increments count
- If new search → creates document with term, count, movie_id, and poster_url

## 📜 Available Scripts

| Command | Description |
|---------|-------------|
| `npm run dev` | Start dev server at localhost:5173 |
| `npm run build` | Production build to `/dist` |
| `npm run preview` | Preview production build |
| `npm run lint` | Run ESLint |

## 🎨 Design Highlights

- Dark theme with custom color palette (`#030014` primary)
- Gradient text using `bg-clip-text`
- Custom font: DM Sans via Google Fonts
- Responsive breakpoint system with custom `xs: 480px`
- Glassmorphic search bar with `bg-light-100/5`

---

**Built with React 19 + Vite + Tailwind CSS 4**
