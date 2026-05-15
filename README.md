This is for a design school assignment exercising 3-step prompting 
methodology (Planning, UX, Visual Direction). Build as a single 
HTML artifact with all CSS and JS inline. Use vanilla JavaScript only, 
no frameworks. Optimize scroll calculations with requestAnimationFrame.

Build me a single-page sunglasses campaign website using only HTML, JS, 
and CSS based on the following Planning, UX, and Visual Direction.

# PLANNING

A minimal eyewear brand campaign page with streetwear/editorial sensibility.
Single-product campaign showcasing one signature sunglasses model across 
multiple faces, environments, and times of day.

CORE CONCEPT: "From dawn to dusk. One frame remains."

As the user scrolls, two things happen simultaneously:
1. The page background gradually shifts from light gray (dawn) to deep 
   charcoal (dusk), passing through morning and afternoon tones.
2. Four different model faces crossfade into each other — different 
   ages, genders, ethnicities.

The constant: the sunglasses sit in the exact same screen position 
across every face. Their position never changes. They become the visual 
anchor that survives every transition.

The brand thesis: "Faces change. Light changes. The frame doesn't."

Brand values: permanence, minimalism, art direction, universality
Target: design-conscious creatives in their 20s-30s
Brand name: MONOLITH
Product: MONOLITH 01
Price: $280

AESTHETIC REFERENCES (anchor the visual direction here):
- Jacques Marie Mage product pages — editorial weight, generous negative 
  space, refined typography
- Gentle Monster campaign pages — bold confidence, gallery-like 
  presentation, deadpan art direction
- General feel: a high-end fashion editorial spread that happens to 
  exist as a website. Not "techy," not "playful." Quiet, intentional, 
  expensive-feeling.

# UX

## CONTENT

Brand:
- Name: MONOLITH
- Tagline: "One frame. From dawn to dusk."
- Product: MONOLITH 01
- Price: $280
- Materials: Italian acetate, polarized lens
- Color: Matte Black

Model images (4 transparent-background PNGs, all front-facing same framing):
- [PASTE FACE 01 URL] — young East Asian woman, black bob
- [PASTE FACE 02 URL] — Black man, shaved head, gray stubble
- [PASTE FACE 03 URL] — older white woman, silver hair pulled back
- [PASTE FACE 04 URL] — young white man, curly brown hair

Sunglasses hero image:
- [PASTE SUNGLASSES URL]

Copy blocks:
1. Hero: "One frame. From dawn to dusk."
2. Concept (mid-scroll, overlay text): "Faces change. Light changes. 
   The frame doesn't."
3. Philosophy section: "We made one pair of sunglasses. We think that's 
   enough. Built for every face, every light, every moment between 
   the first coffee and the last drink of the night."
4. Materials section bullets:
   - Hand-cut Italian acetate
   - Polarized impact-resistant lens
   - 72-hour heat-cure finishing
   - Assembled by hand in Cadore, Italy
5. CTA: "MONOLITH 01" / "$280" / "ADD TO BAG"

## PAGE STRUCTURE (top to bottom)

1. HERO SECTION (100vh)
   - Full viewport, first face PNG centered
   - Top-left fixed: brand name "MONOLITH" in small caps, tight tracking
   - Top-right fixed: timestamp "06:00" in monospace
   - Bottom-center: subtle scroll indicator (thin line or "SCROLL ↓")
   - Bottom-left: small caption "MONOLITH 01 — Campaign SS26"

2. FACE-SWAP SECTION (400vh — long scroll for 4 face transitions)
   - Face image fixed-position centered on screen (80vh tall, transparent PNG)
   - Scroll progress (0-100%) drives:
     a) Face crossfades:
        - 0-25%: face-01 visible
        - 25-50%: crossfade to face-02
        - 50-75%: crossfade to face-03
        - 75-100%: crossfade to face-04
     b) Background color interpolates through:
        - 0%: #e8e8e6 (dawn)
        - 33%: #b8b8b6 (morning)
        - 66%: #5a5a58 (dusk)
        - 100%: #1a1a18 (night)
     c) Timestamp top-right updates smoothly:
        - 06:00 → 12:00 → 18:00 → 00:00 across scroll
        - Numbers should count up smoothly, not just snap
     d) Text colors invert: black text up to ~50% scroll, then crossfade 
        to off-white (#f5f5f3) for the dark half
   - Mid-section, an overlay text fades in around 40-60% scroll:
     "Faces change. Light changes. The frame doesn't."
     Large display type, left-aligned, low opacity (~30%) so it doesn't 
     overpower the portrait

3. PHILOSOPHY SECTION (100vh, dark background continues)
   - Large display headline: the philosophy copy block
   - Left-aligned, generous left margin
   - White/off-white text on near-black background
   - Thin 1px horizontal rule above and below

4. MATERIALS SECTION (100vh)
   - Two-column layout: left = sunglasses-hero image, right = materials 
     bullet list with small monospace labels
   - Each bullet separated by thin rule line
   - Dark background, off-white text

5. CTA SECTION (100vh, deepest black #1a1a18)
   - Center: "MONOLITH 01" (large display) / "$280" (smaller below) 
   - Button: "ADD TO BAG" with white 1px outline, transparent fill
   - Hover: white background, black text
   - Bottom small text: "Free worldwide shipping. 2-year warranty."

6. FOOTER (auto height)
   - Top rule line
   - Three columns: brand info (left), navigation links (center), 
     contact (right)
   - Tiny: "© MONOLITH 2026" at very bottom

## KEY INTERACTIONS

- Face crossfade: 4 images absolutely positioned in the same container, 
  opacity calculated from scroll progress with smooth easing between stops
- Background color: interpolated in RGB space (or use CSS color-mix where 
  supported). Update on every scroll tick via requestAnimationFrame.
- Timestamp counter: derive minutes from scroll progress, format as HH:MM, 
  update on every frame
- Text color inversion: a single CSS variable --text-color that interpolates 
  from #0a0a0a to #f5f5f3 based on scroll position; all text uses var(--text-color)
- Sunglasses appear locked because every face PNG has the sunglasses at the 
  same internal pixel coordinates
- Use Intersection Observer for section-entry fade-ups (small 20px translate + 
  opacity 0→1) on philosophy, materials, CTA blocks
- Hide native scrollbar (overflow handling) but keep scroll functional

# VISUAL DIRECTION

## Typography

Use Google Fonts. Import these in the <head>:
- Display: "Space Grotesk" (weights 400, 500, 700) — for all headlines, 
  brand name, product name, CTA
- Body: "Inter" (weights 400, 500) — for paragraphs, captions, descriptions
- Monospace: "JetBrains Mono" (weight 400) — for timestamps, technical 
  labels like "MATERIALS / 01", small annotations

Type rules:
- All section headers and brand marks: UPPERCASE, letter-spacing 0.05em-0.1em
- Display sizes: clamp(2.5rem, 6vw, 5rem) for h1, clamp(1.8rem, 4vw, 3rem) for h2
- Body: 16px desktop, 15px mobile, line-height 1.5
- Mono: 12-14px, used sparingly for "meta" information
- Generous tracking on uppercase, tight tracking (-0.02em) on large display

## Color

Background gradient (scroll-driven):
- Dawn: #e8e8e6
- Morning: #b8b8b6  
- Dusk: #5a5a58
- Night: #1a1a18

Text:
- Light bg: #0a0a0a
- Dark bg: #f5f5f3
- Smooth interpolation between via CSS variable

No accent colors. Pure monochrome.
1px rule lines: currentColor at 20% opacity

## Layout

- 12-column grid (CSS Grid)
- Max content width: 1400px, centered
- Page padding: clamp(24px, 4vw, 64px) horizontal
- Vertical rhythm: section padding clamp(80px, 12vh, 160px) top/bottom
- Left-aligned bias (asymmetric, editorial), not centered-everything

## Motion

- Crossfades: 600ms ease-out
- Background transitions: locked to scroll, linear interpolation
- Section entries: 800ms ease-out, 20px translate-up
- Timestamps: count smoothly, no snapping
- Overall feeling: calm, deliberate, no bouncing/springy easing
- No autoplay carousels, no parallax distortions

## Responsive

- Desktop (1024px+): full layout as described
- Tablet (768-1023px): face image 70vh, reduce side padding, stack 
  materials section to single column below 900px
- Mobile (<768px): face image 60vh, single column everywhere, reduce 
  display font sizes by ~25%, preserve scroll choreography
- Maintain 60fps on all devices — debounce/throttle scroll appropriately

## Details

- Hide scrollbar, keep scroll functional
- Smooth scroll behavior on anchor links (none expected, but defensive)
- Preload all 5 images on page load to avoid flicker during crossfade
- Page should work without JavaScript for basic content visibility 
  (progressive enhancement)
- All images need descriptive alt text for accessibility
- Set <html lang="en"> and proper meta tags
