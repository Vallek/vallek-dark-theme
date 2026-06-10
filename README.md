# Universal Dark Theme by Vallek

This is universal dark theme for any website/web app. It uses only vanilla CSS and JS and NO libraries or dependencies.   

## Features

* No white flash on page load
* Change colors in variables
* Animated switch button (with accessibility)

## How to use

1. Add `vallek-dark-theme.css` and `vallek-dark-theme.js` files to your project and link them to all pages inside `<header>`. You should use `defer` option for js. You can also choose to just add code without files however else you prefer. Make sure that dark theme css rule comes after body css.

```html
<link rel="stylesheet" href="./css/style.css">
<script defer src="./js/themes.js"></script>
```

2. Put Theme Switcher component where you want it. 

```html
<section class="themes toggle header__themes">
	<h2 class="themes__text visually-hidden">Dark/Light Theme switch</h2>
	<button class="toggle__button themes__button toggle__theme" aria-label="Dark/Light Theme switch" title="Dark/Light Theme switch">
		<span class="settings__label themes__label">Theme</span>
	</button>
</section>
```

3. Put this js code in the beginning of `<body>` element right after opening tag:

```html
<script>
	const thisPage = document.querySelector('body');
	// Check if user set dark theme before
	if (localStorage.getItem('website-theme') === 'dark') {
		thisPage.classList.add('dark');
	}
	// Check if user prefers dark theme
	if (window.matchMedia && window.matchMedia('(prefers-color-scheme: dark)').matches) {
		thisPage.classList.add('dark');
	}
</script>
```
This ensures that no white flash will occur on initial page load.

4. Change `website-theme` localStorage property to your project name. It should be unique and not generic to avoid conflicts (if you use it in multiple projects or with other websites).

## Tips

* If a component does not fit color scheme just use separate variable for it. Example: this Dark Theme switch button background color. Achieve this using `.dark .class` css selector. 

## NOTES

* Notice that I use `page` and `thisPage` consts. This is to ensure no conflict between inline js and async one. You may choose different names or approach. 
* I use `querySelector` on body element here for universal use, but in reality I prefer to add css class `page` for consistency esp if you use any coding methodology.
* I use some "magic numbers" to animate circle, because you can't animate from/to keyword like initial or auto. Depending on what you consider a "magic number" there are also some to align circle inside button.

## Known bugs and issues

* Code will not "remember" Light Theme setting if user has Dark Theme preference on OS level. I tried to make it work but as of now could not do it, maybe later. Feel free to recommend something in Issues.

## Terms of Use
Please use with attribution (link to this repository or my profile).

If something doesn't work, please create an issue. Questions and suggestions can be asked in discussions. Thanks!
