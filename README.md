To build a high-end developer portfolio matching the Heron AI cinematic style using Next.js, follow this final technical specification.

1. Core Tech Stack
Framework: Next.js (App Router).
Styling: Tailwind CSS for layout and rapid dark-mode implementation.
Animation: GSAP + ScrollTrigger for scroll-linked effects.
Smooth Scroll: Lenis (Required for the premium "boutique" feel).
Components: shadcn/ui for functional UI elements (Modals, Forms).
2. Design System & Style Guidelines
Visual Theme: High-contrast dark mode.
Background: #000000 (Pure Black).
Text: #FFFFFF (Primary), rgba(255,255,255,0.6) (Secondary).
Borders: 1px solid rgba(255,255,255,0.1).
Fluid Typography: Replicate the site's scaling by using vw units or CSS clamp in your Tailwind config:
javascript

// tailwind.config.js snippet
fontSize: {
  'fluid-base': '0.57vw', // Desktop scaling
  'fluid-mobile': '2.54vw', // Mobile scaling
}
Use code snippets with caution

Layout Format: Single-page vertical scroll with a Bento Grid for project highlights.
3. Key Technical Implementations
A. The Smooth Scroll Wrapper
Wrap your application in a Lenis provider to ensure all GSAP triggers sync perfectly.

css

tsx
"use client";
import { ReactLenis } from "@studio-freight/react-lenis";

export default function Layout({ children }) {
  return <ReactLenis root>{children}</ReactLenis>;
}
Use code snippets with caution

B. The "Reveal" Animation (GSAP ScrollTrigger)
The Heron AI site uses clip-path masks. Implement this using GSAP:

Code

tsx
useGSAP(() => {
  gsap.to(".project-image", {
    clipPath: "inset(0% 0% 0% 0%)", // Fully revealed
    ease: "none",
    scrollTrigger: {
      trigger: ".project-section",
      start: "top center",
      end: "bottom center",
      scrub: true,
    },
  });
});
Use code snippets with caution

C. Custom Cursor / Interaction
Add a "blob" or "spotlight" cursor that follows the mouse using GSAP for low-latency movement, enhancing the interactive "AI" feel.

4. Summary Table for Portfolio Structure
Section	Tech/Style	Key Feature
Hero	GSAP Text Split	Large fluid typography with reveal animation.
Projects	Bento Grid (shadcn)	clip-path scroll reveals on images.
Tech Stack	Infinite Marquee	Smooth horizontal loop of icons.
Contact	shadcn/ui + Resend	Clean, minimal dark-themed form.
External Resources
Next.js Docs: https://nextjs.org/docs
GSAP + React Guide: https://gsap.com/resources/react/
Lenis Smooth Scroll: https://github.com/darkroomengineering/lenis
shadcn/ui Components: https://ui.shadcn.com/docs/components/accordion
