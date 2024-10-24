# Skeleton Loaders

---
A skeleton screen is a design pattern used to indicate that a page is loading 
while providing users with a wireframe-like visual that mimics the layout of the page.

Light gray boxes represent content and images while api calls are used to fetch data.

This gives the user a better overall waiting experience.

## Types
- Static
- Animated
- Framed

**Framed** is loading only the header, footer, and / or nav with a blank space in between.
This often gives a poor experience to users, leading to feel that the site is broken
and not indicative of a loading state.

**Animated**
60% of test participants in the author's skeleton screen study perceived that 
the animated skeletons represented a shorter duration. 
"Skeleton screens that leverage motion that moves from left to right 
(e.g. a wave or shimmer like animation, much like Facebook or Google uses) 
are perceived as shorter in duration than skeletons that pulse (opacity fading in and out)"

### No Data
Data and no data fetched should still load the same overall structure that
the skeleton screen portrays.
It can be a bit jarring with a large difference in change if no data is displayed(empty state)


## React Loading Skeleton ([npm package](https://www.npmjs.com/package/react-loading-skeleton))
This Skeleton component is automatically sized to the correct dimensions.

It allows for more flexible loading patterns. 
It's possible to have the title load before the body, 
while having both pieces of content show loading skeletons at the right time.


### Sources
---
[Samhita Tankala's article](https://www.nngroup.com/articles/skeleton-screens/)
[Bill Chung's Article](https://uxdesign.cc/what-you-should-know-about-skeleton-screens-a820c45a571a)