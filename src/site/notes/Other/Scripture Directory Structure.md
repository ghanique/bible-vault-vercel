---
{"dg-publish":true,"permalink":"/other/scripture-directory-structure/"}
---

# Scripture Directory Structure

Created: 2022-04-24 14:57  
#documentation

The directory that contains the verses from the [[Concepts/Bible\|Bible]] is called `Scripture`.

The `Scripture` directory can have one or more `translations`. I.e.: it has a subdirectory called `KJV`. That subdirectory also has an `article` with the same name, which lists all the bible books of that translations, in order. That article matches the `template` "Translation".

The directory that contains one specific `translation` has one subdirectory for each of the `bible books`. The names of the `bible books` are extended with the name of the `translation`. I.e. "Genesis KJV". The reason for adding the name of the `tanslation` to the name of the `book`, is to make sure that the `article names` remain unique. I.e.: "Genesis" in the KJV is something different than "Genesis" from AMP, so if both were named "Genesis", the `article name` "Genesis" would not be unique, but ambiguous.

The directory that contains one specific `bible book`, like "Genesis KJV", also contains an `article` with the same name, which matches the `template` "Book". That `article` references the `translation`, and mentions whether it belongs to the `old testament` or `new testament`. It also contains a bullet-pointed list of references to the chapters in the book: i.e. "- (double square brackets)Genesis 1 KJV(double square brackets)". (Again, the name of the `translation` is included to make the `article names` for each of the `chapters` unique).

The directory that contains one specific `bible book`, like "Genesis KJV", also contains a subdirectory for each of the `chapters` of that book (see the previous paragraph).

The directory that contains one specific `chapter`, like "Genesis 1 KJV", also contains an `article` with the same name. That `article` matches the template "Chapter", and references its `translation` and the `book` it belongs to (i.e. "Genesis KJV"). That article also has a list of `placeholders` (not bulleted) for each of the `verses` in that `chapter`. The `verse name` is composed of the name of the `book` (i.e. "Genesis"), followed by the name of the `chapter` and `verse` separated with a period (i.e. "1.1"), followed by the name of the `transation` (i.e. "KJV", again, to make the `verse article name` unique). I.e. "(exclamation mark)(double square brackets)Genesis 1.1 KVJ(double square bracket)". The exclamation mark will display the `verse's content` instead of a link to the `verse article`. This allows one to read the `chapter` if all the `verse articles` are created. The `chapter` ends with a heading "References", which must contain a link to `chapter` on [bible.com](https://my.bible.com/). The easiest way is to copy a `verse` (see below), take the url from that one, and then remove the last "." and everything after it.

The directory that contains one specific `chapter`, like "Genesis 1 KJV", also contains one `article` for each `verse`, i.e. "Genesis 1.1 KJV" and "Genesis 1.2 KJV".

Every `verse article` does not match a template and has a very clean content. Go to [bible.com](https://my.bible.com/), browse to the `chapter`, select the `verse`, and click "Copy". Paste that content in the `verse article`. Then remove the first quotation mark, and the last quotation mark and everything after it.

https://docs.google.com/spreadsheets/d/19esALXAnDfHNgiImNMu3JscLrWarFkhRdHdsZxiqzx0/edit#gid=1970001951 can help generate the lists for the `chapters` of a `book` and the list with the `placeholders` for the `verses` of the `chapter`.
