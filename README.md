Live Demo :


Github Pages usage summary : 
Conclusion of the below summary is this :
    1. If any file is referred for the base directory use the URL without leading / just like "script.js" will do --> "./script.js" won't work.
    2. While for the path that are inside the application have to give url as ./folder/fileName will do like "./models/filename"
    3. if this <base href="/"> is used then, all the current directory have to give the repoName like I have used in DemoForStaticSite:
            "DemoForStaticSite/polyfills-es2015.js" so basically routing will start from .github.io --> (start from here)-->repoName--> fileName
     4. if <base href="/DemoForStaticSite"> : will never work -- have to change the href in base url
	these will work :
		<script src="/DemoForStaticSite/polyfills-es5.js" nomodule></script>
	these won't work :
        <script src="/main-es5.js" nomodule></script>  -- will go to the route-folder as the leading / means root folder		
		<script src="styles-es2015.js" type="module"></script> --> will go to this -->  https://imhimanshoe.github.io/styles-es2015.js  
		<script src="./polyfills-es2015.js" type="module"></script>  because now the folder will go to https://imhimanshoe.github.io/polyfills-es2015.js n
        5. if <base href="/DemoForStaticSite/"> :
        will work :
            <script src="main-es5.js" nomodule></script>  --> best case scenario
        
Some Intution :
1. leading "/" means will go to the root folder.
2. root starting without any thing will take relative path from <base href="/DemoForStaticSite/">
    so src="main-es5.js" this will work


For Git hubPages to work in this : DO this 
The exact problem with github pages in including the sub folder is this 
1. if the content is in the current directory as is the case with script.js and face-api.js then relative linking only will work like this 
    ./script.js and ./face-api.js it will refer to the content in the
      https://imhimanshoe.github.io/Face-Detection-Javascript/script.js and face-api.js folder
   while if you use /script.js or onlt script.js, it start searching from the root folder of the site i.e. 
    https://imhimanshoe.github.io/script.js and  https://imhimanshoe.github.io/face-api.js 
2. this behaviour is unpredictable for the subfolder because it always shows them from the root folder sp the subpath have to include the 
  repoName by themselves in the path.... like 
    Face-Detection-JavaScript/models/...content
    
    
  
  
  using the description from this 
  https://github.com/mojombo/jekyll/issues/332#issuecomment-18952908
  
  the complete thread of problem is given here 
  https://stackoverflow.com/questions/16316311/github-pages-and-relative-paths
  
  
  Final solution is do a ./Subfolder-here 
  above answer are from older version of github now it has been updated so it should work fine with our
  ./subfolder structure ---> make sure there is no leading / in the structure like ./model/filename.js/ -- wrong
    
    
    
    
    
    
    
    
    
    
    older one :
    # IMPORTANT: Bug Fixes

## `navigator.getUserMedia`

`navigator.getUserMedia` is now deprecated and is replaced by `navigator.mediaDevices.getUserMedia`. To fix this bug replace all versions of `navigator.getUserMedia` with `navigator.mediaDevices.getUserMedia`

## Low-end Devices Bug

The video eventListener for `play` fires up too early on low-end machines, before the video is fully loaded, which causes errors to pop up from the Face API and terminates the script (tested on Debian [Firefox] and Windows [Chrome, Firefox]). Replaced by `playing` event, which fires up when the media has enough data to start playing.


