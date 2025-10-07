# My GSAP Learning Journey

This repository contains all the code, examples, and mini-projects I'm creating while learning the GreenSock Animation Platform (GSAP).

## About This Project

The goal of this repo is to practice GSAP concepts in isolation, from simple tweens to complex timelines and ScrollTrigger animations. Each file or folder will demonstrate a specific feature.

---

## What I'm Learning

- [x] **Core Concepts:** Understanding `gsap.to()`, `gsap.from()`, and `gsap.fromTo()`.
- [x] **Timelines:** Creating sequenced animations with `gsap.timeline()`.
- [x] **Staggering:** Animating multiple elements in a sequence.
- [x] **Easing:** Applying different animation "feels" like bounce, elastic, etc.
- [x] **ScrollTrigger:** Triggering animations based on scroll position.
- [x] **SVG Animation:** Animating SVG graphics.
- [x] **Performance:** Best practices for smooth, performant animations.

---

## Demos & Examples

Here are the examples I've built so far. Click on the file name to see the code.

- **`01-core-concepts.html`**: A simple animation using `gsap.to()`, `gsap.from()`, and `gsap.fromTo()` to move and rotate an object.
- **`02-timelines.html:`** Shows how to use `gsap.timeline()` to create sequenced animations and control their timing.
- **`03-staggering.html:`** Demonstrates the `stagger` property to create sequential animations for a group of elements.
- **`04-easing.html:`** Compares different `ease` types side-by-side to show how they give animations personality and character.
- **`05-scrolltrigger.html:`** Introduces the `ScrollTrigger` plugin for creating scroll-based animations. Covers basic triggers, `toggleActions`, and the powerful `scrub` feature.
- **`06-svg-animation.html:`** Demonstrates the classic SVG line-drawing effect by animating `stroke-dashoffset` on SVG paths.

---

## Mini-Projects

Here are the practical projects built by combining the concepts learned above.

- **`07-mini-project-marquee.html`**: An infinite-scrolling marquee of cards, built by cloning elements and creating a seamless GSAP loop.
- **`08-mini-project-floating-card.html`**: Creates a natural 'floating' effect by combining several out-of-sync, looping animations. Includes a bonus for interactive mouse-based tilting.

---

## Key Performance Principles

These are the most important best practices to ensure your animations are always fast and smooth.

### 1. Animate Transforms and Opacity

This is the most important rule. Animating properties like `transform` (`x`, `y`, `scale`, `rotation`) and `opacity` is incredibly fast because they don't affect the layout of other elements and can be processed by the GPU. Avoid animating layout properties like `width`, `height`, `top`, or `left`.

- **BAD (slow):** `gsap.to(".box", { left: 200, top: 50 });`
- **GOOD (fast):** `gsap.to(".box", { x: 200, y: 50 });`

### 2. Use `gsap.set()` for Initial States

Instead of setting starting styles in your CSS (like `opacity: 0;`) that you plan to animate with GSAP, use `gsap.set()`. This keeps all your animation logic in your JavaScript and can be more efficient.

- **Example:** `gsap.set(".box", { opacity: 0, y: 50 });` followed by `gsap.to(".box", { opacity: 1, y: 0 });`

### 3. Cache Your Selectors

If you plan to animate the same element multiple times, select it once and store it in a variable. This prevents the browser from having to search the page for the element over and over.

- **BETTER:**
  ```javascript
  const myBox = document.querySelector(".box");
  gsap.to(myBox, { x: 100 });
  gsap.to(myBox, { y: 100, delay: 1 });
  ```

### 4. Use `will-change` (Sparingly)

The CSS `will-change` property hints to the browser that an element is about to be animated, allowing it to optimize ahead of time. However, it uses memory, so you should only apply it right before an animation and remove it after. A simple way is to add a class with this property just before your animation starts.

- **CSS:** `.animating { will-change: transform, opacity; }`

---

## How to Use

1.  Clone this repository: `git clone https://github.com/amar-ti2021/gsap-playground.git`
2.  Navigate to the project folder.
3.  Open any of the `.html` files in your web browser to see the animation in action.
