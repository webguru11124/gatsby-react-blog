# Blog

Have a peek »»» [https://blog.baobab.fi](https://blog.baobab.fi)

## Features

- **Responsive** and streamlined design.
- GatsbyJS compiles the blog into HTML+CSS+JS so **hosting the blog costs nothing** at providers like Netlify.
- **Blazing fast** UX: The website is visible and functional after only 1 round trip and ~20kB of data. That first round trip can be super fast to anywhere in the world, because the blog is only static assets which can be delivered by CDN. Subsequent pageloads render ~instantly thanks to link prefetching.
- Autogenerated **tracedSVG image placeholders** are stylized to create a smooth look and transition as the image loads without the page jumping around.
- Write blog posts into **Markdown** files (easy to format and content will not be married to any platform).
- **Expandable**: possible to embed custom React components into Markdown.
- Posts organized by **tags**.
- **Teasers** of posts are generated to front page with **infinite scroll** which gracefully degrades into **pagination**.
- Allow readers to be notified of updates with **RSS feed** and email newsletter.

## Feel free to fork

- If you see something to fix, please send me a pull request (or at least a message)
- Want to create your own blog with this repo? You are free to do so (within license terms).
- Want to reuse my content? Please ask for permission first (license in this repo does not apply to content).

#### How to create your own blog with this repo

- Prerequisites: learn about ReactJS and GatsbyJS.
- Fork and `npm install`.
- Run in development mode with `gatsby develop`.
- Run in production mode with `gatsby build && gatsby serve` (or `./fastbuild.sh`). If you want to delete `cache` and `public` before building, use `./slowbuild.sh` (recommended for releases to avoid leaking development data). You may have to make the scripts executable before you are able to run them (`chmod +x filename`).
- When you create content in `posts`, a folder with a name like `2020-03-05--my-book-review` will be published, whereas a name like `my-book-review` will be considered a draft and will not be published.
- Blog posts are in `mock_posts` and `posts` folders. By default only mock posts are used (to help you tweak the website before you have a lot of content). You can switch to real posts by creating a `.env` file with `POSTS_FOLDER=posts`.
- It's good practice to not add the `.env` file to repo. When you publish your blog, find out how you can add environment variables to your host.
- Go through everything in `content/meta/config.js` and `content/pages` and `content/parts`
- Search all files for "baobab" and "greg".
- When you publish, make sure caching and redirects work reasonably. I recommend Netlify, in which case cache configuration in `static/_headers` is fine and you just need to edit 1 line in `static/_redirects`.
- Move your own icons into `src/images/app-icons`, run `npm run generate-app-icons`, then replace `static/favicon.ico`.
- [OPTIONAL] If you want Google Analytics: add `GOOGLE_ANALYTICS_ID=123456` to environment variables.
- [OPTIONAL] If you want a Contact page: [Setup Contact Form submission via Google Script](https://github.com/dwyl/learn-to-send-email-via-google-script-html-no-server)
- [OPTIONAL] If you want a Search page with Algolia: mostly follow instructions from [here](https://dev.greglobinski.com/setup-algolia-account/). Search for commented out code with 'algolia'.
- [OPTIONAL] If you want an email newsletter, set one up. Otherwise remove the link from the `Follow` page.


## Attribution

Hi, I'm Baobab. I didn't start this from scratch.
- I started building on top of [Greg Lobinski's](https://github.com/greglobinski) excellent [hero-blog-starter](https://github.com/greglobinski/gatsby-starter-hero-blog/)
- For infinite scroll and pagination I used some code from [Joan Mira](https://github.com/gazpachu) and [react-simple-infinite-scroll](https://github.com/jaredpalmer/react-simple-infinite-scroll)
- Photos are mostly from [Unsplash](https://www.unsplash.com/), hover over to see photographer attribution.
- Icons are mostly from [FontAwesome](https://origin.fontawesome.com/).

Main changes from Greg's version:
- Fixed draft posts (used to leak draft posts into production)
- Fixed RSS feed (used to not have dates so RSS readers were unable to tell which content is new + used to have non-post-articles in feed) 
- Fixed 404 page (text used to be hidden under header)
- Improved usability for users who have JS disabled (Font loading and contact form submission)
- Contact Form submission used to require entire web site to be hosted on Netlify. Now the Contact Form submission uses Google Scripts and web site hosting / form handling can be changed independently.
- Allow multiple tags (used to be just 1 category per post)
- Allow custom React components inside Markdown files
- Added 'Follow' page, so users know that RSS feed exists (also link to email newsletter)
- Added infinite scroll, which gracefully degrades into pagination.
- Many design changes. Spent a lot of time tweaking image placeholders :tired_face: Removed and simplified a lot of features to create a less cluttered look (matter of preference, eye of the beholder and so forth...)
