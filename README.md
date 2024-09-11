# SCSS Mixin For Import Icons

## Installation

```
npm i -D ameliance-use-icons-scss
```

## Usage

### Basic

Put the icons in the public folder

```
| - public/assets/icons/
|   | - task.svg
|   | - quote.svg
|   | - idea.svg
```

Import icons to scss file

```scss
// import mixin
@use "ameliance-use-icons-scss" as *;

// add a list of icon file names without an extension
$iconsSet: ("task", "quote", "idea");

// import icons and set your own custom styles
// by default, the color is inherited from the parent elem
@include useIcons($icons: $iconsSet) {
	width: 24px;
	height: auto;
}
```

Using the icon class in html

```html
<span class="icon--task"></span>
```

### Extended

```
| - public/svg/
|   | - feather-task.svg
|   | - feather-quote.svg
|   | - feather-idea.svg
```

```scss
@use "ameliance-use-icons-scss" as *;

$iconsSet: ("task", "quote", "idea");

%icon--hover-color {
	&:hover {
		background-color: magenta;
	}
}

@include useIcons(
	$icons: $iconsSet,
	$path: "/svg/",
	$prefix: "icon-24--",
	$filename-prefix: "feather-"
) {
	width: 24px;
	height: auto;
	background-color: red;
	@extend %icon--hover-color;
}

@include useIcons(
	$icons: $iconsSet,
	$path: "/svg/",
	$prefix: "icon-48--",
	$filename-prefix: "feather-"
) {
	width: 48px;
	height: auto;
	background-color: yellow;
	@extend %icon--hover-color;
}
```

```html
<span class="icon-24--task"></span> <span class="icon-48--task"></span>
```

## Mixin Parameters

```scss
// icons set like: $iconsSet: (arrow-left, arrow-right)
// required parameter
$icons: $iconsSet;
```

```scss
// path to svg icons in the "public" folder
// '/assets/icons/' — default value
$path: "/icons/x2/svg";
```

```scss
// prefix for use in classes
// 'icon--' — default value
$prefix: "icon-24--";
```

```scss
// file extension
// 'svg' — default value
$type: "png";
```

```scss
// prefix in the name of the icon file, for example, "feather-icon-" in the file feather-icon-like.svg
// no value by default
$filename-prefix: "material-";
```

```scss
// prefix in the name of the icon file, for example, "-x2" in the file like-x2.png
// no value by default
$filename-postfix: "-48px";
```

## History

```
1.0.2 [2024_09_11]:
   *: update code style

1.0.1 [2023-08-10]:
   *: update readme

1.0.0 [2023-08-10]:
   +: init package
```

---

[!["Buy Me A Coffee"](https://www.buymeacoffee.com/assets/img/custom_images/yellow_img.png)](https://www.buymeacoffee.com/ameliance)
