# IMPORTANT: Bug Fixes

## `navigator.getUserMedia`

`navigator.getUserMedia` is now deprecated and is replaced by `navigator.mediaDevices.getUserMedia`. To fix this bug replace all versions of `navigator.getUserMedia` with `navigator.mediaDevices.getUserMedia`

## Low-end Devices Bug

The video eventListener for `play` fires up too early on low-end machines, before the video is fully loaded, which causes errors to pop up from the Face API and terminates the script (tested on Debian [Firefox] and Windows [Chrome, Firefox]). Replaced by `playing` event, which fires up when the media has enough data to start playing.


The exact problem with github pages in including the sub folder is this 
1. if the content is in the current directory as is the case with script.js and face-api.js then relative linking only will work like this 
    ./script.js and ./face-api.js it will refer to the content in the
      https://imhimanshoe.github.io/Face-Detection-Javascript/script.js and face-api.js folder
   while if you use /script.js or onlt script.js, it start searching from the root folder of the site i.e. 
    https://imhimanshoe.github.io/script.js and  https://imhimanshoe.github.io/face-api.js 
2. this behaviour is unpredictable for the subfolder because it always shows them from the root folder sp the subpath have to include the 
  repoName by themselves in the path.... like 
    Face-Detection-JavaScript/models/...content
