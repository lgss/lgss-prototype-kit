# LGSS Prototype kit

## About this project

This project is a copy of the [Verify Local Patterns prototype kit]() stripped back for continued use on other projects. Thank you GDS, you are wonderful.

## Creating a new prototype

To create a new service prototype, you will need to;

 1. Some steps go here <todo>

### 1. Forking this repository and running it locally

 - First, [fork the repository](https://help.github.com/articles/fork-a-repo/).
 - You'll need to run `npm install` from the command line to install the node modules that the project requires.
 - To start your local server, run `npm start` from the command line.
 - The project will now be accessible in your browser at `http://localhost:3000`.

### 2. Adding your council options

 - If you navigate to `http://localhost:3000/council-picker`, you should see the councils that have been added so far as options.
 - To add your council as an option, first open `app/councils.json`.
 - Copy one of the other council objects. This will look something like this:

 ```
 {
   "name" : "Argleton County Council",
   "shortName": "Argleton",
   "parkingBoundary": "Argleton City Centre",
   "permitMax": "four",
   "permitsCosts": [51, 81, 153, 153],
   "permitWait": 0,
   "string" : "argleton"
 },
 ```
 *(Every object needs the comma at the end except for the last object. [Read more about valid JSON](https://en.wikipedia.org/wiki/JSON#Example).)*

 - Fill in the options relevant to your council.
 - The `string` option should be lowercase.
 - If you want to see where any option is used, do a project search for the option name in your text editor.

Once you've added your council into `app/councils.json`, your council will show up as an option in `http://localhost:3000/council-picker`. You can select it, but the page will look pretty broken until you do the next step.

If you need to add new options for further localisations, either talk to us on Slack, or raise an issue on Github.

### 3. Adding a council stylesheet and template

To make the prototype look like a council's website, you'll need to add CSS and a template HTML file.

It's best to start by copying the Argleton files for both.

 - The council stylesheets are in `app/assets/sass/`. You should name your file with your `string` option set in step 2. For example if your `string` option is `exampleland`, your stylesheet should be `exampleland.scss`
   - The project uses [Sass](http://sass-lang.com/) for writing CSS. You don't need to use this though, you can just write normal CSS - But either way, you should save your CSS or SCSS file with a `.scss` file extension.

 - The layout templates are in `lib/`. The file should be called `lib/[string]_template.html`. (eg `lib/exampleland_template.html`). You should use this file to make the prototype look more like your council website. For example, you can add the HTML for your website's header bar in here.
   - The HTML template language is [Nunjucks](https://mozilla.github.io/nunjucks/). (This allows to use variables and a few other features in HTML.)

Once you've added the above, you should be able to step through your prototype. Do what you can with those two files to make the prototype look like the live service will look on your council's website.

### Optional: Un-govuk-ing your local version

By default, your localised prototype will follow an unbranded version of [GOV.UK elements](http://govuk-elements.herokuapp.com/). This means form elements, text spacing etc, will look like GOV.UK, but the font will be Helvetica instead of New Transport.

You can turn this of if you want your prototype to look more like your website. To get rid of all GOV.UK-ish styling, do the following:

 1. Remove the `govukish` class from the `<html>` tag in your `lib/[string]_template.html` file.
 2. Remove the lines between the `<!-- start govukish styles -->` and `<!-- end govukish styles -->` also in your `lib/[string]_template.html` file.
 3. Remove the line `@import 'patterns/_govukish.scss';` from your `app/assets/sass/[string].scss` file.

This should leave your version completely unstyled, and you can drop all your council's styling in `app/assets/sass/[string].scss` as you would anyway.

### 4. Making a pull request

Once you're happy with your changes, [make a pull request from your fork](https://help.github.com/articles/creating-a-pull-request-from-a-fork/) to merge into the master branch of this repository.

Any questions, ask on Slack!

---

## Contributing issues

If you spot an issue, [add it to this project](https://github.com/lgss/lgss-prototype-kit/issues/new). But first, read the [contributing to this project guide](https://github.com/lgss/lgss-prototype-kit/blob/master/CONTRIBUTING.md).

## Using this project

Feel free to fork or use this project for testing government services.

If you fix a bug, or want your changes to be hosted on our Heroku instance for some other reason, feel free to make a pull request.

## Argleton styles

CSS for the Argleton prototype are found in `app/assets/sass/unbranded.scss`.

HTML for the services are found in `app/views/service-patterns/`[service-name]`/example-service`.

## Routes

To change where a user goes when they click options such as radio buttons, you'll need to edit `app/routes.js`. Read more about that in [the prototype kit docs](https://govuk-prototype-kit.herokuapp.com/docs/creating-routes).

---


Here follows the docs ported over from the prototype kit.

## GOV.UK Prototype kit

### About the prototype kit

The prototype kit provides a simple way to make interactive prototypes that look like pages on GOV.UK. These prototypes can be used to show ideas to people you work with, and to do user research.

Read the [project principles](https://govuk-prototype-kit.herokuapp.com/docs/principles).

### Security

If you publish your prototypes online, they **must** be protected by a [username and password](https://govuk-prototype-kit.herokuapp.com/docs/publishing-on-heroku). This is to prevent members of the public finding prototypes and thinking they are real services.

You must protect user privacy at all times, even when using prototypes. Prototypes made with the kit look like GOV.UK, but do not have the same security provisions. Always make sure you are handling user data appropriately.

### Installation instructions

- [Installation guide for new users (non technical)](https://govuk-prototype-kit.herokuapp.com/docs/install/introduction)
- [Installation guide for developers (technical)](https://govuk-prototype-kit.herokuapp.com/docs/install/developer-install-instructions)

### Guides

1. [Setting up git](https://govuk-prototype-kit.herokuapp.com/docs/setting-up-git)
2. [Publishing on the web (Heroku)](https://govuk-prototype-kit.herokuapp.com/docs/publishing-on-heroku)
3. [Using GOV.UK Verify](https://govuk-prototype-kit.herokuapp.com/docs/using-verify)

### Other documentation

- [Prototype kit principles](https://govuk-prototype-kit.herokuapp.com/docs/principles)
- [Making pages](https://govuk-prototype-kit.herokuapp.com/docs/making-pages)
- [Writing CSS](https://govuk-prototype-kit.herokuapp.com/docs/writing-css)
- [Updating the kit to the latest version](https://govuk-prototype-kit.herokuapp.com/docs/updating-the-kit)
- [Tips and tricks](https://govuk-prototype-kit.herokuapp.com/docs/tips-and-tricks)
- [Creating routes (server-side programming)](https://govuk-prototype-kit.herokuapp.com/docs/creating-routes)
