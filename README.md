

## Responsive Design Made Easy

**Start with the big picture and with global styles**

- Typography, colours, vertical spacing and flow

**Look at the big picture of the layout**

- Look for big picture design/layout
- See if there are any repeating patterns
- Use utility classes for things that repeat a lot
  - container/wrapper for holding content
  - classes to control background colours and text colours
  - layout classes like `.split` or anything else that can be reused in different areas

## Start to narrow down

- Start adding the changes required at the smaller scale 
- Minor tweaks, exceptions in certain areas
- Focusing on individual components 



## Common Design Patterns that you can use

### Split evenly with flexbox

```css
.split {
    display: flex;
    flex-direction: row;
}

/* spacing between the children */
.split > * + * {
    margin: 1rem 0 0 0;
}

@media (min-width: Xem) {
    .split {
        flex-direction: column;
    }
    
    /* spacing between elements */
    .split > * + * {
        margin: 0 0 0 1rem;
    }
}

.split > * {
    flex-basis: 100%;
}

/* make individual columns bigger/smaller columns where needed */
.big-column { flex-basis: 300%; }
.small-column { flex-basis: 50%; }
```



#### same as above, but with grid

The above is a bit cleaner is using grid, mostly thanks to `gap` being supported in all browsers. The only thing is, there is no way to adjust individual columns, so this would only work for situations where all columns need to be equal.

```css
.split {
    display: grid;
    gap: 1rem;
}

@media (min-width: Xem) {
    .split {
        grid-auto-flow: columns;
        grid-auto-columns: 1fr;
    }
}
```



### Reactive layout with flexbox

Can lead to unbalanced layouts at certain screen sizes, so it really depends on the layout you are after. 

The `flex-basis` on the children needs to be a small number, in general, as we're relying on flex-grow to let them stretch. If it is too big, they'll just go to that size and never be columns, because of the `flex-wrap`.

Also, you'll want to set a `min-width` on the children to prevent them from becoming too small. Even with `flex-shrink`, and element cannot be smaller than it's `min-width`.

```css
.parent {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem; /* not currently supported in Safari */
}

.parent > * {
  min-width: Xrem;
  flex: 1 1 10%;
}

```



****

## Things I mentioned

- [A modern CSS reset](https://hankchizljaw.com/wrote/a-modern-css-reset/) by Andy Bell[Managing Flow and Rhythm with CSS Custom Properties](https://24ways.org/2018/managing-flow-and-rhythm-with-css-custom-properties/) by Andy Bell
- [The Holy Albatross](https://heydonworks.com/article/the-flexbox-holy-albatross/) by Heydon Pickering. This is incredibly useful! But to make a point about accessibility and the loopholes we make others jump through, for the time being you'll have to disable JavaScript to access Heydon's site. I did make [a YouTube video where I explored it](https://youtu.be/fuiEYR6Hoe0), but I didn't really show the true power of it, it just scratches the surface.
- [caniuse.com](https://caniuse.com/) - check browser support
- [PostCSS](https://postcss.org/) - Help with supporting older browsers, and a lot more. A bit like Babel for CSS
- [CSS Algorithms](https://youtu.be/panKf9hzUfQ) - A fantastic talk by Lara Schenck looking at enterprise level CSS solutions, and an approach to testing CSS
- [Why is CSS so weird?](https://youtu.be/aHUtMbJw8iA) - I didn't mention this, but it's a great video by Miriam Suzanne that looks at why CSS is so weird. Really highly recommended
- I also mentioned Static Site generators, specifically [Eleventy](https://www.11ty.dev/) and [Hugo](https://gohugo.io/). I'm a fan of Eleventy as it's build on vanilla JS.
- [All about CSS Custom Properties](https://youtube.com/playlist?list=PL4-IK0AVhVjOT2KBB5TSbD77OmfHvtqUi) - This is a bit of self-promotion with a series on them from my YT channel. The first video should be enough to get you started with them, and then each video dives in from there, most of them are pretty short.



## General resources

- [Grid by Example](https://gridbyexample.com/patterns/) by Rachel Andrew - This has a bunch of common layouts built out with Grid
- [CSS-Tricks](https://css-tricks.com/) - my go to for keeping up with CSS, and web development at large



## Where you can find me

- [My YouTube channel](https://www.youtube.com/kevinpowell) - where most of my stuff is
- [My Twitch](https://www.twitch.tv/kevinpowellcss) - Live coding Mondays and Thursdays, starting again in January
- [@KevinJPowell](https://twitter.com/KevinJPowell) on Twitter
- [My website](https://www.kevinpowell.co/) (neglected as of late)
- [My newsletter](https://www.kevinpowell.co/newsletter/) (email every Sunday with what I've been up to and general musings)