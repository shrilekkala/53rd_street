# 53rd Street: A Walk Down Memory Lane

An interactive web experience that documents 18 years of change on 53rd Street in Hyde Park, Chicago (2007–2025) through scroll-driven storytelling.

[Live Demo](https://shrilekkala.github.io/53rd_street/)

---

## About This Project

I moved to Hyde Park in 2023 for grad school. 53rd Street became my daily route: coffee runs, late-night CVS trips, meals with friends. But as people started leaving, I realized I had no idea what this place looked like before I arrived. 

This project is my attempt to see what came before, and to preserve what it looked like while I was still here.

---

## Design Constraints

### Why Google Street View Only?

I made a deliberate choice to use **only Google Street View imagery** as my source material, with no personal photos, historical archives, or supplementary images.

**Reasons for this constraint:**

1. **Conceptual consistency**: Street View is an accidental archive, Google wasn't trying to document neighborhood change, but that's exactly what happened. Using only this source acknowledges the limitations and biases of the archive itself.

2. **Democratic perspective**: Street View shows what anyone walking down the street would see: the public face of change. Personal photos would shift the project toward "my memories" rather than "our collective memory."

3. **Invitation to participate**: By showing only what's visible from the street, I wanted to leave room for readers to fill in their own memories.

4. **Honest gaps**: Some things (like the graffiti wall behind the gas station) were never captured by Street View. Rather than supplement with other photos, I chose to *describe* what was hidden. The absence becomes part of the story.

### Why Scroll-Driven Storytelling?

Walking and scrolling are similar physical gestures. Both involve forward motion, pacing, and the choice to pause or continue. By mapping scroll position to Street View frames, the experience mirrors the act of walking down the actual street.

The scroll mechanic also creates a meditative quality. You can't skip ahead; you have to move through time at the pace the project sets.

---

## Technical Implementation

### Core Technologies
- **Vanilla JavaScript**—for full control over scroll behavior
- **IntersectionObserver API**—for performant scene transitions
- **CSS Custom Properties**—for responsive viewport handling on mobile
- **HTML5 & CSS**—modern web standards with responsive layout


### Key Technical Challenges

**1. Smooth scroll-driven frame transitions**
- **Challenge**: Updating image `src` on every scroll event caused jank
- **Solution**: Used `requestAnimationFrame` to batch updates and cached src checks to avoid redundant assignments

**2. Mobile viewport height inconsistency**
- **Challenge**: iOS Safari's dynamic viewport (address bar appearing/disappearing) caused layout jumps
- **Solution**: Locked viewport height on page load using CSS custom properties (`--vh-locked`)

**3. Image preloading for 100+ Street View frames**
- **Challenge**: Need smooth transitions but don't want to block initial page load
- **Solution**: Preload all frame images on DOMContentLoaded, store sources in array, swap synchronously during scroll

**4. Scene timing and narrative pacing**
- **Challenge**: Each scene needs to feel like a distinct "moment" while maintaining flow
- **Solution**: Used IntersectionObserver with 60% threshold—scenes change when viewer is committed to the scroll, not on first pixel


---

## Project Structure
```
├── index.html          # Main HTML
├── styles.css          # All styling
├── img/
│   ├── t1-01.jpeg     # Transition walk frames
│   ├── s1-01.jpeg     # Scene images
│   └── ...
└── README.md
```

---

## Content & Research

Historical details sourced from:
- [Chicago Maroon: "Losing the 53rd Street Graffiti Wall"](https://chicagomaroon.com/18940/artsandculture/losing-the-53rd-street-graffiti-wall/) (April 2014)
- [Chicago Maroon: "Hyde Park Taco Station opens at 53rd and Dorchester"](https://chicagomaroon.com/22008/news/hyde-park-taco-station-opens-at-53rd-and-dorchester/) (October 2015)
- [New York Times: "The Obamas' First Kiss, Immortalized"](https://archive.nytimes.com/thecaucus.blogs.nytimes.com/2012/08/16/the-obamas-first-kiss-immortalized/) (August 2012)
- [UChicago's The Core: "Defunct Hyde Park Restaurants"](https://thecore.uchicago.edu/Summer2016/departments/defunct-hyde-park-restaurants.shtml) (Summer 2016)
- [Eater Chicago: "Barack Obama's Favorite Chicago Diner Is Valois"](https://chicago.eater.com/2017/1/11/14237750/barack-obama-favorite-chicago-diner-valois-hyde-park-nbc-interview-farewell-speech) (January 2017)

All captions written to balance factual history with personal perspective, acknowledging what I learned.
---

## Acknowledgments

**Historical imagery:** Google Street View (2007–2025)

**Created by:** Shri Lekkala, 2026