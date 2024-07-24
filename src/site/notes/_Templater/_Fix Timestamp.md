<%*
// Test Data:
/*
Created: 2022-05-02 16:10  
Author: Guillaume Hanique  
#product
*/

// Get Content
const editor = app.workspace.activeLeaf.view.editor;
let content = editor.getValue();

// Find the correct fields
const created = /[cC]reated::? "?(\d\d\d\d-\d\d-\d\d).(\d\d:\d\d)/gm.exec(content);
const author = /[aA]uthor::? \[*([^\]\n]+)?/gm.exec(content);
const hashtag = /#([^ \n]+)/gm.exec(content);

if (created === null) return;
if (author === null) return;
if (hashtag === null) return;

console.log(created);
console.log(author);
console.log(hashtag);

// Determine the corrected timestamp block
// From https://stackoverflow.com/questions/23593052/format-javascript-date-as-yyyy-mm-dd
const offset = (new Date()).getTimezoneOffset() * 60 * 1000;
const now = new Date((new Date()).getTime() - offset);
const lastModified = now.toISOString().substring(0, '2023-01-31T22:33'.length);

const newTimestamp = `created:: ${created[1]}T${created[2]}  
modified:: ${lastModified}  
author:: ${author[1].trim()}

#${hashtag[1]}`;

// Find the old timestamp block
// (It would probably also have been possible to get the timestamp block
// and 'created' and 'author' and the hashtag, all with one expression,
// but then it would become too complex for my taste, risking not finding one
// because there is yet another variation that I did not account for).
const timestampBlock = /Created: \d\d\d\d[^#]+#[^\n]+/gm;
const match = timestampBlock.exec(content);
if (match === null) return;

// Replace it
editor.replaceRange(newTimestamp, {line: 0, ch: match.index}, {line: 0, ch: match.index + match[0].length});

// Find and delete created and author from frontmatter.
const frontmatterTime = /created:.+?author:[^\n]+\n/gms.exec(content);
if (frontmatterTime !== null) {
  editor.replaceRange('', {line: 0, ch: frontmatterTime.index}, {line: 0, ch: frontmatterTime.index + frontmatterTime[0].length});
}

// Find and delete the frontmatter block if it is now empty.
content = editor.getValue();
const emptyFrontmatterBlock = /---\n---\n\n?/gms.exec(content);
if (emptyFrontmatterBlock !== null) {
  editor.replaceRange('', {line: 0, ch: emptyFrontmatterBlock.index}, {line: 0, ch: emptyFrontmatterBlock.index + emptyFrontmatterBlock[0].length});
}
%>