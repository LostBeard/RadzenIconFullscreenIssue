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

### How to use the demo

#### Reproduce the issue
- Visit the demo link above.
- Click the `With RadzenIcon` in the nav bar
- Click the `Toggle Fullscreen` button
- Observe the issue

!IMPORTANT: 
- Close the tab, and in a new tab go to the Demo again. (Refreshing the tab does not fully reset the issue.)

#### Show the issue does not occur without RadzenIcon
- Visit the demo link above.
- Click the `Without RadzenIcon` in the nav bar
- Click the `Toggle Fullscreen` button
- Observe the issue does not occur

## Version
- Radzen 6.0.19
- Windows 10 64 bit
- macOS Sequoia (tested on browserstack.com)
- Chrome 133

## TL;DR
- `<RadzenIcon Icon="fullscreen">` can cause `element.requestFullscreen()` to misbehave in Chrome.
- `<RadzenIcon>` with icons other than `fullscreen` have shown to not trigger the issue.

Issue on macOS Sequoia on browserstack.com:
[Sequoia](https://github.com/LostBeard/RadzenIconFullscreenIssue/raw/refs/heads/main/RadzenIconFullscreenIssue/Media/screenRecording-1-3-2025-9-11.mp4)

Issue on Windows 10 on browserstack.com:
[Windows 10](https://github.com/LostBeard/RadzenIconFullscreenIssue/raw/refs/heads/main/RadzenIconFullscreenIssue/Media/screenRecording-1-3-2025-9-15.mp4)
