# RadzenIconFullscreenIssue
`<RadzenIcon Icon="fullscreen">` can cause `element.requestFullscreen()` to misbehave in Chrome.

This repository demonstrates a possible issue related to RadzenIcon, element.requestFullscreen, and the Chrome web browser.

## Steps to reproduce
- Start a new Blazor WASM Standalone project
- Add Radzen to the project
- Add a `<RadzenIcon Icon="fullscreen">` to a page
- Add code to the page to call `element.requestFullscreen()` on a div when a button is clicked
- Run the project in Chrome
- Click the button to request fullscreen
- Observe that the entire document goes fullscreen and not the element that called `requestFullscreen()`

## Expected behavior
The element that called `requestFullscreen()` should go fullscreen and not the entire document.

## Actual behavior
The entire document goes fullscreen and not the element that called `requestFullscreen()`

## Additional information
This issue does not occur in Firefox or Edge. It has been observed in Chrome 133 on Windows 10, and macOS Sequoia.

## Workaround
The issue seems to not appear if you do not use a `<RadzenIcon>` with a `fullscreen` icon. If you use a different icon, the issue does not occur.

## Demo
[Demo](https://lostbeard.github.io/RadzenIconFullscreenIssue/)

There are are 3 pages.  
- `Home` Explains the issue.
- `With RadzenIcon` Demonstrates the issue with a RadzenIcon.
- `Without RadzenIcon` If done first, usually works as expected.

The only difference between the `With RadzenIcon` and `Without RadzenIcon` pages is the use of a RadzenIcon.

If you go to the page without the RadzenIcon and click the fullscreen button, the issue does not occur.

If you go to the page with the RadzenIcon and click the fullscreen button, the issue usually occurs.

The issue may start just by visiting the page with the RadzenIcon before going to the page without. Going fullscreen using the page without the RadzenIcon first may cause the page with the RadzenIcon to work as correctly. 

## Version
- Radzen 6.0.19
- Windows 10 64 bit
- macOS Sequoia (tested on browserstack.com)
- Chrome 133

## TL;DR
- `<RadzenIcon Icon="fullscreen">` can cause `element.requestFullscreen()` to misbehave in Chrome.
- The issue is inconsistent and does not occur reliably even with the steps stated above.  
- `<RadzenIcon>` with icons other than `fullscreen` have shown to not trigger the issue.


