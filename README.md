# Translate Obsidian

## Deployment Tier
**Tier:** 1 (Static Translations / JSON files - CDN or GitHub Pages hosting)

Help translate Obsidian into your language.

## Add a new language

To add a new language, follow these steps:

1. Copy all of the content of the raw `en.json`: https://raw.githubusercontent.com/obsidianmd/obsidian-translations/master/en.json
2. Paste into here: https://github.com/obsidianmd/obsidian-translations/new/master
3. Translate some strings to your language
4. Find the language code of the language you're contributing: https://www.wikiwand.com/en/List_of_ISO_639-1_codes
5. Name the new file "[language code].json" and submit

## Staying up-to-date

Merge conflicts are nasty. They happen when you're translating an outdated version of the template, part of which might have been translated by someone else. To prevent this, try to fork our repository right before you translate.

If you want to do multiple translation pull requests, before doing work each time, use the "Compare" UI on your own fork to pull in all the newest changes from `obsidianmd:master` first by creating a pull request on your own repository and merge it in yourself, so that your own copy is up-to-update.

## Submit changes

To translate, [fork this repo](https://guides.github.com/activities/forking/) and edit the JSON file of your language. After that, [submit a pull request](https://guides.github.com/activities/forking/).

Note that you don't have to clone your fork to make the edits; you can do everything on GitHub's web UI. Simply open a file in your own forked repo and click on the pencil icon to start editing.

## Translating

The translation JSON file consists of key-value pairs. The key should give you a good idea of where the text is in the app.
