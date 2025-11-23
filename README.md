# Image-Search-Engine
A fully front-end image search engine built with plain HTML, CSS, and JavaScript that uses fetch() to query a public image API and displays results in a responsive, user-friendly gallery. The project demonstrates how to wire a search input to a remote API, handle asynchronous requests, render paginated results, and provide basic UI/UX features such as loading states, error handling, and image previews — all without any backend server.

__Features__
Search bar that accepts user queries and triggers image fetch requests.
Uses fetch() with async/await to call a public image API (Unsplash, Pexels, Pixabay, or any similar public endpoint).
Displays results in a responsive, masonry-style grid that adapts to screen size.
Each image card shows a thumbnail, author/credit, and optional link to the source.
Infinite scroll or “Load More” pagination to fetch additional pages of results.
Loading indicator while requests are in progress and graceful error messages for failed requests.
Basic client-side caching to avoid repeating identical queries within the same session.
Keyboard accessibility for searching and navigating results; images open in a lightbox or new tab for a closer view.
Minimal, clean styling with CSS for a modern look and smooth hover/transition effects.

__How it Works (Overview)__
The user types a search term and presses Enter or clicks Search.
JavaScript captures the query, builds the API request URL (including API key and pagination params if required), and calls fetch() with await.
While waiting, the UI shows a spinner/loader.
When the response arrives, the script parses JSON, extracts relevant fields (thumbnail URL, full-size URL, photographer name, credits), and renders DOM elements for each image.
If more results exist, the UI displays a “Load More” button or automatically fetches the next page when the user scrolls near the bottom.
Clicking an image opens a lightbox modal with the larger image and metadata, or navigates to the image’s source page depending on your preference.

__Technical Details__
HTML: semantic markup for header, search form, result grid, and footer.
CSS: responsive layout, grid/flexbox, simple animations, mobile-first approach.
JavaScript: ES6+ (modules optional), fetch() with async/await, DOM creation/manipulation, debouncing search input (optional), basic caching in memory (e.g., Map keyed by query+page).
API integration: designed to plug into any public image API. Most require an API key and support query + page + per_page parameters. The code sanitizes user input, URL-encodes queries, and respects API rate limits.
Accessibility: images have alt attributes derived from API descriptions/tags; keyboard focus states for interactive controls.


__Implementation Tips & Best Practices__
Use request debouncing (e.g., 300ms) to avoid firing a request on every keystroke.
Implement error handling for network failures and show helpful messages (e.g., “No results found”, “Rate limit reached — try again later”).
Respect alt text and focus management for accessibility; ensure interactive elements are reachable by keyboard.
Paginate results rather than requesting massive result sets at once to reduce bandwidth and improve performance.
Cache identical query+page responses in memory to make back/forward navigation snappier.
Lazy-load images (loading="lazy") to improve initial load speed.

__Potential Extensions / Future Improvements__
Add filters (orientation, color, size) based on API capabilities.
Replace client-side API key usage with a serverless proxy to secure credentials.
Add user favorites stored in localStorage.
Add infinite scroll with Intersection Observer for smoother UX.
Add image download and share buttons with proper attribution.
Improve UI with animations, transitions, and a more sophisticated masonry layout.

__Troubleshooting & Notes__
If you see CORS errors, verify the API supports client-side requests or use a proxy.
If results are empty, check that your API key/quota is valid and that the query string is being encoded correctly.
Rate limits: most free image APIs have strict request limits — throttle your requests and implement backoff on 429 responses.

__License__
Include an appropriate license (MIT, Apache 2.0, etc.) depending on how you want to allow reuse.
