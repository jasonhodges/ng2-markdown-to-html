# ng2-markdown-to-html [![CircleCI](https://circleci.com/gh/jfcere/ng2-markdown-to-html/tree/master.svg?style=shield&)](https://circleci.com/gh/jfcere/ng2-markdown-to-html/tree/master) [![version](https://img.shields.io/npm/v/ng2-markdown-to-html.svg?style=flat)](https://www.npmjs.com/package/ng2-markdown-to-html) [![npm](https://img.shields.io/npm/l/ng2-markdown-to-html.svg)](https://opensource.org/licenses/MIT) [![npm](https://david-dm.org/jfcere/ng2-markdown-to-html/status.svg)](https://david-dm.org/jfcere/ng2-markdown-to-html)

ng2-markdown-to-html is an [Angular 2](https://angular.io/) library that uses [marked](https://github.com/chjj/marked) to parse markdown to html combined with [Prism.js](http://prismjs.com/) for synthax highlights.

Demo available @ [jfcere.github.io/ng2-markdown-to-html](https://jfcere.github.io/ng2-markdown-to-html)

## Installation

Use the following command to add ng2-markdown-to-html library to your `package.json` file.

```bash
npm install ng2-markdown-to-html --save
```

## Configuration

You must import `MarkdownToHtmlModule` inside your module to be able to use `markdown-to-html` component and/or directive.

```diff
import { NgModule } from '@angular/core';
import { CommonModule } from '@angular/common';
+ import { MarkdownToHtmlModule } from 'ng2-markdown-to-html';

import { HomeComponent } from './home.component';

@NgModule({
  imports: [
    CommonModule,
+    MarkdownToHtmlModule.forRoot(),
  ],
  declarations: [HomeComponent],
})
```

To activate [Prism.js](http://prismjs.com/) synthax highlight you will need to choose a css theme file from `node_modules/prismjs/themes` directory and add it to your application.

> Note that you can also find additional themes by browsing the web such as [Prism-Themes](https://github.com/PrismJS/prism-themes) or [Mokokai](https://github.com/Ahrengot/Monokai-theme-for-Prism.js) for example.

If you are using [Angular CLI](https://cli.angular.io/) you can follow the example below...

#### .angular-cli.json

```diff
"styles": [
  "styles.css",
+ "../node_modules/prismjs/themes/prism-okaidia.css"
],
```

#### tsconfig.app.json (for Angular-CLI >= 1.0.0-rc.0)

```diff
"compilerOptions": {
  "types": [
+   "prismjs"
  ]
},
```

## Usage

ng2-markdown-to-html provides one component and one directive to parse your markdown to your web application.

### Component

You can use `markdown-to-html` component to either parse static markdown directly from your html markup or load the content from a remote url using `src` property.

```html
<!-- static markdown -->
<markdown-to-html>
  # Markdown
</markdown-to-html>

<!-- loaded from remote url -->
<markdown-to-html [src]="'path/to/file.md'"></markdown-to-html>
```

### Directive

The same way the component works, you can use `markdown-to-html` directive to accomplish the same thing.

```html
<!-- static markdown -->
<div markdown-to-html>
  # Markdown
</div>

<!-- loaded from remote url -->
<div markdown-to-html [src]="'path/to/file.md'"></div>
```

## Synthax highlight

When using static markdown you are responsible to provide the code block with related language.

```diff
<markdown-to-html>
+  ```typescript
    const myProp: string = 'value';
+  ```
</markdown-to-html>
```

When using remote url ng2-markdown-to-html will use file extension to automatically resolve the code language.

```html
<!-- will use html highlights -->
<markdown-to-html [src]="'path/to/file.html'"></markdown-to-html>

<!-- will use php highlights -->
<markdown-to-html [src]="'path/to/file.php'"></markdown-to-html>
```

## Demo application

A demo is available @ [https://jfcere.github.io/ng2-markdown-to-html](https://jfcere.github.io/ng2-markdown-to-html) and it source code can be found inside the `src/app/markdown-demo` directory.

The following commands will clone the repository, install npm dependencies and serve the application @ [http://localhost:4200](http://localhost:4200)

```bash
git clone https://github.com/jfcere/ng2-markdown-to-html.git
npm install
ng serve
```

## AoT compilation

Building with AoT is part of the CI and is tested every time a commit occurs so you don't have to worry at all.

## Road map

Here is the list of tasks that will be done on this library in a near future ...

- ~~Add CircleCI integration~~
- ~~Publish demo on github pages~~
- Make Prism highlight optional
- Support Prism.js customizing options (line-numbers, line-height, ...)
- Transpile library to Javascript

## Contribution

Contributions are always welcome, just make sure that ...

- Your code style matches with the rest of the project
- Unit tests pass
- Linter passes

## License

Licensed under [MIT](https://opensource.org/licenses/MIT).