<div align="center">
  <h1>

  🖖

  Handmade Blog
  </h1>
</div>

Handmade Blog is a classic static blog generator for people who want to start a blog quickly. It supports article type document for a blog post, work type document for portfolio, code highlights, [KaTeX](https://katex.org/) syntax, footnotes, and others.

## Demo: [Here](https://handmade-blog.netlify.com/)

![Article page preview](https://user-images.githubusercontent.com/6410412/70389251-36353400-1a00-11ea-91af-42a12b06c383.png)

## Getting Started

1. Click the 'Use this template' button above the file list to create a new repository. If you want to use github.io domain, have to name the repository `{YOUR_ID}.github.io`.

2. Clone this repository, and install node modules.

    ```bash
    $ git clone https://github.com/{YOUR_ID}/{REPOSITORY_NAME}.git
    $ cd {REPOSITORY_NAME}
    $ npm install
    ```

3. Modify `config.json` file in `services` directory to set your blog title and subtitle.

    ```json
    {
      "blogTitle": "Lorem Ipsum",
      "blogSubtitle": "lorem ipsum"
    }
    ```

4. Start local server at `http://localhost:1234/`. `npm start` script opens local server based on `server` directory. 

    ```bash
    $ npm start
    ```

5. Publish the example articles and works by `npm run publish`. It converts a markdown documents in `_articles` or `_works` directory to HTML files.

    ```bash
    $ npm run publish article
    $ npm run publish work
    ```

6. Run `build` and `deploy` script if you're ready to host a live server. This script builds local files to `dist` directory and creates `gh-pages` branch that contains only the files in `dist` directory. GitHub will host live server at `https://{YOUR_ID}.github.io/` based on `gh-pages` automatically.

    ```bash
    $ npm run build
    $ npm run deploy
    ```

## Document Publishing Process

1. Write a document in `_articles` or `_works` directory.

1. Run `npm run publish article` or `npm run publish work` script to convert markdown to HTML.

1. Preview converted document on the local server using `npm start` script.

1. Run `npm run build` and `npm run deploy` to publish the document to live server.

## Project Structure

* `_articles` - Markdown files for the blog posts.
* `_works` - Markdown files for the portfolio.
* `app`
  * `assets` - Any files to be imported by HTML files such as image, font, etc.
  * `public` - HTML files generated by `publish` script. `server` and `dist` directory is based on this directory. Do not change the files under this directory directly.
    * `article` - HTML files converted from `_articles` directory.
    * `work` - HTML files converted from `_works` directory.
  * `src` - Source code to be imported by HTML files.
    * `css` - CSS files generated by `build` script.
    * `scss`
    * `ts`
  * `static` - Any static files that aren't compiled by `build` script. You can modify `build` script to copy the files under this directory to `dist` directory. 
  * `templates` - HTML files used as ejs template. `publish` script converts a markdown file to HTML based on templates under this directory.
* `dist` - Files compiled by `build` script. `deploy` script deploys a website to GitHub pages based on this directory. Do not change the files under this directory directly.
* `server` - Files compiled by `build` script. `start` script opens local server based on this directory. Do not change the files under this directory directly.
* `services` - Source code implementing `publish` script.
  * `classes`
  * `models`
* `tools` - Source code implementing various npm scripts. 

## Available Scripts

### `npm start`

Starts local development server at http://localhost:1234/.

### `npm run publish`

Converts templates to HTML files.

```bash
$ npm run publish article
```

Converts all articles.

```bash
$ npm run publish works
```

Converts all works.

```bash
$ npm run publish article 5
```

Converts an article which id is 5.

```bash
$ npm run publish work 3
```

Converts a work which id is 3.

```bash
$ npm run publish page
```

Converts all pages.

### `npm run watch`

Rebuilds template files in `templates` directory and markdown files in `_articles` directory automatically whenever the files are modified.

### `npm run build`

Builds files with parcel bundler.

### `npm run deploy`

Builds and deploys the files.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.