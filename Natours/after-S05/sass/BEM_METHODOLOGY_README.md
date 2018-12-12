### In the following markup:

```html
<div class="row">
                    <div class="col-1-of-3">
                        <div class="card">
                            <div class="card__side card__side--front">
                                <div class="card__picture"></div>
                                <div class="card__heading"></div>
                                <div class="card__details"></div>
```

One might think to name what here is the class `.card__picture` along the lines of:

`.card__side__picture`

This is an anti-parent in BEM; class names ought not be nested.