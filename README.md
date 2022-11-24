# parklife


Usage: parkLife [options] <filelist> 

Positional arguments:

* files ( list of files )

Optional arguments:
* -h --help                               shows help message and exits [default: false]
* -v --version                            prints version information and exits [default: false]
* -low                                    low for canny [default: 10]
* -high                                   high for canny [default: 100]
* -V --verbose                            [default: false]
* -N --normalizedGraylevelVariance        run normalizedGraylevelVariance [default: false]
* -T --tenengrad                          run tenengrad [default: false]
* -M --modifiedLaplacian                  run modifiedLaplacian [default: false]
* -C --cannyLad                           run cannyLad , high and low options are used to set range [default: false]
* -S --sharpness                          run sharpness [default: false]


parklife will try to load a file, either via libraw or imread and then run different 'sharpness' algorithms, whichever one is selected the score is retval*1000.0 if more than one is run then its the last to run that is the exit code

if more than one file is given on the command line it'll run thru each of the files if it can and print the results, the last one ran is the exit code ( useful for stdout capture and parsing later)


needs libraw.dll

functions here

https://stackoverflow.com/questions/7765810/is-there-a-way-to-detect-if-an-image-is-blurry


# Sample run

[O:\code\libRaw]q:\tools\parklife  --cannyLad C:\Users\charlie\Pictures\17663298.jpg q:\bora\01-06-2022\DSC05199.ARW   q:\bora\01-06-2022\DSC05201.ARW
* 3 files to process
* Processing file C:\Users\charlie\Pictures\17663298.jpg : cannyLad = 103.256250
* Processing file q:\bora\01-06-2022\DSC05199.ARW : cannyLad = 167.008887
* Processing file q:\bora\01-06-2022\DSC05201.ARW : cannyLad = 73.846440


[O:\code\libRaw]q:\tools\parklife  --cannyLad  --modifiedLaplacian   --tenengrad  --normalizedGraylevelVariance  --sharpness C:\Users\charlie\Pictures\17663298.jpg q:\bora\01-06-2022\DSC05199.ARW   q:\bora\01-06-2022\DSC05201.ARW
* 3 files to process
* Processing file C:\Users\charlie\Pictures\17663298.jpg : nsharpness = 27.124303
* tsharpness = 911.313863
* msharpness = 10.445341
* sharpness = 882.232473
* cannyLad = 103.256250
* Processing file q:\bora\01-06-2022\DSC05199.ARW : nsharpness = 13.005994
* tsharpness = 85.402249
* msharpness = 7.112541
* sharpness = 111.160065
* cannyLad = 167.008887
* Processing file q:\bora\01-06-2022\DSC05201.ARW : nsharpness = 14.255082
* tsharpness = 57.029885
* msharpness = 6.001723
* sharpness = 78.826591
* cannyLad = 73.846440
