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

!IMPORTANT: Close the tab, and in a new tab go to the Demo again. Simply refreshing the tab does not fully reset the issue.

#### Show the issue does not occur without RadzenIcon
- Visit the demo link above.
- Click the `Without RadzenIcon` in the nav bar
- Click the `Toggle Fullscreen` button
- Observe the issue does not occur

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

I have reported this issue here where I was told they were incapable of following my directions to reproduce the issue, and that I should find a better component library if I wanted issues to be fixed.
[radzenhq/radzen-blazor/issues/2010](https://github.com/radzenhq/radzen-blazor/issues/2010)

After @akorchev refused to follow the simple instructions I gave him to reproduce the issue, and I even recorded video proof with the steps to reproduce on browserstack.com, he closed the issue and told me to find a different component library.

@akorchev wrote:
`I have spent 30 minutes of my weekend to troubleshot this issue. Even suggested a workaround despite being unable to reproduce what is obviously a browser bug. If this is not enough for you please move on to a different component library.`

I spent hours trying to figure out what was causing the issue, and I was able to reproduce it consistently. I even provided a video, a repo, and instructions to show the issue. I also did this on MY weekend. 

I have since moved on to a better component library, and I am sharing this issue here to help others who may encounter the same issue. I hope this helps someone else who may encounter this issue.

Issue on macOS Sequoia on browserstack.com:
<video src="https://github.com/LostBeard/RadzenIconFullscreenIssue/raw/refs/heads/main/RadzenIconFullscreenIssue/Media/screenRecording-1-3-2025-9-11.mp4">

Issue on Windows 10 on browserstack.com:
<video src="https://github.com/LostBeard/RadzenIconFullscreenIssue/raw/refs/heads/main/RadzenIconFullscreenIssue/Media/screenRecording-1-3-2025-9-15.mp4">
