Setting up OpenSeadragon on a Mac and using it without an image server

Step 1) 
Install [XCode](https://developer.apple.com/xcode/) or [Command Line Tools for XCode](https://developer.apple.com/library/content/technotes/tn2339/_index.html#//apple_ref/doc/uid/DTS40014588-CH1-WHAT_IS_THE_COMMAND_LINE_TOOLS_PACKAGE_) so you can install Homebrew

Step 2)
Install [Homebrew](https://brew.sh/), which will also include a copy of [ImageMagick](https://www.imagemagick.org/script/index.php)

Step 3) 
Download [MagickSlicer](https://github.com/VoidVolker/MagickSlicer), which requires ImageMagick

Step 4)
To use MagickSlicer, cd to the MagickSlicer-master folder and enter the following command in Terminal

	``` ./magick-slicer.sh -i path/to/source-folder/name-of-file.jpg -o path/to/destination-folder/name-of-file ```
	

	- or, if you're keeping the output in the same directory as the MagickSlicer script
	
	``` ./magick-slicer.sh path/to/source-folder/name-of-file.jpg ```


	- or, if you want to process all of the images at once, use the following commands in Terminal to get the conversion script to loop through all of the files in the source folder

	```
	myArray=(path/to/source-folder/*)

	for ((i=0; i<${#myArray[@]}; i++)); do ./magick-slicer.sh -i "${myArray[$i]}" -o path/to/destination-folder/name-of-file"$i"; done
	```


	- Note: each image takes ~30 seconds to process

Step 5)
	In the output folder (in our case, pageView or bookView), you’ll find a filename.dzi file and a filename_files folder of image tiles for your image

Step 6)
	Install [OpenSeadragon](https://openseadragon.github.io/#download)

Step 7)
	Create a new project. For now, we reference the image tiles files and .dzi file through Github ( see [pageView.json](https://github.com/Brown-University-Library/atalanta-code/blob/master/data/json/pageView.json) and [bookView.json](https://github.com/Brown-University-Library/atalanta-code/blob/master/data/json/bookView.json) )


Additional Resources:
https://openseadragon.github.io/docs/
http://blogs.library.duke.edu/bitstreams/2015/11/20/zoomable-hi-res-images-hopping-aboard-the-openseadragon-bandwagon/

Sequence Mode for navigating through image sets
https://openseadragon.github.io/examples/tilesource-sequence/

Reference Strip for horizontal thumbnails
https://openseadragon.github.io/examples/ui-reference-strip/

Arrays and for loops in Bash/Terminal
https://stackoverflow.com/questions/21668471/bash-script-create-array-of-all-files-in-a-directory