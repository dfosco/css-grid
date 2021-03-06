### CSS Grid: grid-auto-flow explained – 6 of 25

```css
  grid-auto-flow: column;
  grid-auto-flow: row;
```

- These two options will define where extra items will be added on the implicit grid: as a new row or new column

- It's kind of like 'flex-direction' on flexbox 

```css
  grid-auto-flow: dense;
```

- Will add them whenever they fit better!


### CSS Grid: Sizing tracks in CSS Grid – 7 of 25

The `fr` unit takes a `fraction` of the space remaining on the page after all other hard units have been calculated. So, for a container of `1000px` width:

- This will lead to grid items overflowing the width, because the 20px grid gap will be added on top of the 250px item size:

```css
    .container {
      display: grid;
      width: 1000px;
      grid-gap: 20px;
      grid-template-columns: 250px 250px 250px 250px;
    }
```

 - This option, even though it allows for a flexible container size, would also overflow the grid items: 

```css
    .container {
      display: grid;
      grid-gap: 20px;
      grid-template-columns: 25% 25% 25% 25%;
    }
```
 - `fr` units however, are calculated after all the remaining units on the page have been applied:

```css
    
    .container {
      display: grid;
      grid-gap: 20px;
      grid-template-columns: 1fr 1fr 1fr 1fr;
      /* 
      If you use 'auto' unit, it will snap to the size of the content inside the biggest grid item
      */
    }
```

 - The only way to do this without CSS grid (purely with css) would be to do:

```css
    /* Not exactly neat */
    .container {
      display: grid;
      grid-gap: 20px;
      grid-template-columns: calc(25% - 20px) calc(25% - 20px) calc(25% - 20px) calc(25%);
    }
```

### CSS Grid: Grid Repeat Function – 8 of 25

```css
    /* This: */
    .grid { grid-template-columns: 1fr 1fr 1fr 1fr }
    
    /* Will be the same as this: */
    .grid { grid-template-columns: repeat(4, 1fr) }

    /* Just as this: */
    .grid { grid-template-columns: 1fr 2fr 1fr 2fr } 

    /* Will be the same as this: */
    .grid { grid-template-columns: repeat(2, 1fr 2fr) }
```

### CSS GRID: Sizing Grid Items — 9 of 25

```css
    .container {
      display: grid;
      grid-gap: 20px;
      grid-template-columns: repeat(5, 1fr);
    }

    .item9 {
      /* Item 9 on the grid container will take 2 columns... */
      grid-column: span 2;
      /* ... and 2 rows */
      grid-row: span 2;
    }
```

### CSS GRID: Placing Grid Items — 10 of 25


```css
    /* Item will start on the track (line) 2 and end at 5 */
    .item {
      grid-column-start: 2;
      grid-column-end: 5;
    }

    /* There's a shorthand form available too */
    .item { 
      grid-column: 2 / 5; 
    }

    /* You can also define how many col/rows it will span, instead of giving definite numbers: */

    /* start at track 1 / span 6 tracks */ 
    .item { 
      grid-column: 1 / span 6;
    }

    /* span 4 tracks / end at track 6 */ 
    .item { 
      grid-column: span 4 / 6;
    }

    /* start at track 1 / end at track... last 😱 */ 
    .item { 
      grid-column: 1 / -1;
    }

    /* this only works for rows if you define rows explicitly */ 
    .item { 
      grid-row: 1 / -1;
    }

    /* start at track 1 / end at track second last */ 
    .item { 
      grid-column: 1 / -2;
    }
```