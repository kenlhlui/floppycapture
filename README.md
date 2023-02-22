<!-- Improved compatibility of back to top link: See: https://github.com/othneildrew/Best-README-Template/pull/73 -->
<a name="readme-top"></a>
<!--
*** Thanks for checking out the Best-README-Template. If you have a suggestion
*** that would make this better, please fork the repo and create a pull request
*** or simply open an issue with the tag "enhancement".
*** Don't forget to give the project a star!
*** Thanks again! Now go create something AMAZING! :D
-->



<!-- PROJECT SHIELDS -->
<!--
*** I'm using markdown "reference style" links for readability.
*** Reference links are enclosed in brackets [ ] instead of parentheses ( ).
*** See the bottom of this document for the declaration of the reference variables
*** for contributors-url, forks-url, etc. This is an optional, concise syntax you may use.
*** https://www.markdownguide.org/basic-syntax/#reference-style-links
-->
[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![MIT License][license-shield]][license-url]


<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
      <ul>
        <li><a href="#built-with">Built With</a></li>
      </ul>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#installation">Installation</a></li>
      </ul>
    </li>
    <li><a href="#usage">Usage</a></li>
    <li><a href="#roadmap">Roadmap</a></li>
    <li><a href="#contributing">Contributing</a></li>
    <li><a href="#license">License</a></li>
    <li><a href="#contact">Contact</a></li>
    <li><a href="#acknowledgments">Acknowledgments</a></li>
  </ol>
</details>



<!-- ABOUT THE PROJECT -->
# About The Project

Scripts for floppy intake work at [UTL](https://onesearch.library.utoronto.ca/).
Built by Jess Whyte and Andy Foster, 2018
<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- GETTING STARTED -->
# Getting Started

## floppy.py
FloppyCapture, or floppy.py, is a workflow script to ingest floppy disks (3.5" and 5.25") using a kryoflux two-drive setup, and attached camera.

> 📝Note: This is an environment-specific, institution-specific (e.g. calls the UTL catalog) script, but could be modified. For a more generalized version, see [floppy-nocall.py](##floppy-nocall.py).

### Usage

  ```python
  python3 floppy.py -l LIB -d DIR -m MEDIATYPE -c CALL [-k KEY] [-i]
  ```

#### Required argument
| Parameters 	| Name 	| Argument 	| Description 	| Example 	|
|---	|---	|---	|---	|---	|
| -l 	| LIB 	| {LibraryID} 	| LibraryID, for a list of library IDs, visit uoft.me/libs 	| -l UTL 	|
| -d 	| DIR 	| {top-directory-name} 	| The top directory name. Usually, it should be placed under /mnt/data. 	| -d /mnt/data/testing01 	|
| -m 	| MEDIATYPE 	| 3.5 / 5.25 	| The size of the disk. Put the corresponding number after -m. 	| -m 3.5 	|
| -t 	| TRANSCRIPT 	| {transcript-of-disk-label} 	| Transcript (note) of the disk label. Input the written notes on the disks with quotes here. No comma is allowed in this argument 	| -t "information ABC" 	|
| -c 	| COLLECTION 	| {directory-name-of-collection} 	| The collection name. This will be the second level of the files directory. 	| -c testing01-floppy 	|

#### Optional argument
| Parameters 	| Name 	| Argument 	| Description 	| Example 	|
|---	|---	|---	|---	|---	|
| -h 	| HELP 	| / 	| The help manual. 	| -h 	|
| -i 	| / 	| 0 / 2 / 4 / 9 	| The orginal disk type. For MFM, it is 4. For Apple DOS 400K/800K, it is 9. See [Kyroflux manual](https://www.kryoflux.com/download/kryoflux_manual.pdf) (P.14-15) for more reference. <br /> The default (i.e. without an argument) for -i is  "-i4". 	| -i4 	|
| -k 	| KEY 	| / 	| The Catkey of the item. 	|  	|

### How floppy.py works: 
- takes some args like media type (e.g. 3.5) and call number, 
- checks projectlog.csv to see if you've already imaged a disk(s) for that call number,
- pulls and displays metadata from json returned from a catalog call, 
- asks if this is the right disk and you want to continue?
- creates disk folder (callNum) under designated library (designated by -l argument)
- prompts for optional label transcription
- prompts for "notes" 
- prompts for photo, takes picture of disk (set-up uses an ipevo doc cam + ffmpeg, we just use it for documentation, could be adapted for a different photo setup)
- runs appropriate kryoflux dtc commands (takes stream + MFM if -i argument in place, if no -i argument, it will take stream (while trying i4 and i9) and then prompts user for i-type to try), 
- updates disk metadata with info pulled from catalog and disk capture
- updates a master project log
> 📝Note: Script does not verify 'success' (i.e. if the image is mountable and files can be extracted/performed). That process is separate.

## floppy-nocall.py
floppy-nocall.py is a generalized version of floppy.py (it doesn't attempt to call the UTL catalog or take a photo). 
It's a workflow script to image floppy disks (3.5" and 5.25") using a kryoflux two-drive setup. 

### Usage

  ```python
  python3 floppy-nocall.py -c COLLECTION -d DIR -m MEDIATYPE -t "TRANSCRIPT" -k KEY [-i]
  ```

#### Required argument
| Parameters 	|  Name 	|Argument| Description 	|Example|
|:---------:	|:-----------:	|:------------------------------:	|:----------------------------------------------------------------------------------------------------------------------:	|:----------------------:	|
| -c        	| COLLECTION  	| {directory-name-of-collection} 	| The collection name. This will be the second level of the files directory.                                             	| -c testing01-floppy    	|
| -d        	| DIR         	| {top-directory-name}           	| The top directory name. Usually, it should be placed under /mnt/data.                                                  	| -d /mnt/data/testing01 	|
| -m        	| MEDIATYPE   	| 3.5 / 5.25                       	| The size of the disk. Put the corresponding number after -m.                                                           	| -m 3.5                 	|
| -t        	| TRANSCRIPT  	| {transcript-of-disk-label}     	| Transcript (note) of the disk label. Input the written notes on the disks with quotes here. No comma is allowed in this argument 	| -t "information ABC"   	|
| -k        	| KEY         	| {disk-id}                      	| The Disk ID. This is also the name of the base directory of the disk image file (& photo of the disk).                 	| -k testing01-01        	|

#### Optional argument
| Parameters 	| Name 	| Argument 	| Description 	| Example 	|
|:---:	|:---:	|:---:	|:---:	|:---:	|
| -i 	|  /	| 0 / 2 / 4 / 9  	| The orginal disk type. For MFM, it is 4. For Apple DOS 400K/800K, it is 9. See [Kyroflux manual](https://www.kryoflux.com/download/kryoflux_manual.pdf) (P.14-15) for more reference. <br /> The default (i.e. without an argument) for -i is  "-i4". 	| -i4 	|

### Example command
  ```python
python3 floppy-nocall.py -c testing01-floppy -d /share/floppies -m 3.5 -t "information ABC" -n "note: supplementary materials"  -k testing01-01 -i
  ```
#### The output:
- */share/floppies/projectlog.csv* ← **overall projectlog/list of disks (appends)** 
- */share/floppies/streams/* ← **directory for stream files**
- */share/floppies/Coll003/* ← **directory for Coll/Accession**
- */share/floppies/Coll003/001/* ← **directory for individual disk**
- */share/floppies/Coll003/001/001_capture.log* ← **kryoflux’s log of capture**
- */share/floppies/Coll003/001/001_disk.img* ← **disk.img, can be mounted/files extracted**
- */share/floppies/Coll003/001/001.jpg* ← **picture of disk, only if camera is attached and you opt-in at the prompt**


### How floppy-nocall.py works:
- takes some args like media type (e.g. 3.5), diskID (key), etc.
- checks to see if you've already imaged a disk with that ID(key)
- if exists, asks if you just want to replace the stream/img files (not update the log)
- creates disk directory (key, aka diskID) under designated collection directory
- runs kryoflux dtc commands (takes stream + MFM if -i argument in place, if no -i argument, it will take stream (while trying i4 and i9) and then prompts user for i-type to try)
- prompts if you want to update your notes
- updates a master project log.csv (in your -d directory)

> 📝Note: you may want to adjust the kryoflux functions and the dtc command parameters. For examplle, this script are set to only make 2 tries and limit the log output. 


<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CONTRIBUTING -->
# Contributing

Contributions are what make the open source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**.

If you have a suggestion that would make this better, please fork the repo and create a pull request. You can also simply open an issue with the tag "enhancement".
Don't forget to give the project a star! Thanks again!

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- CONTACT -->
# Contact

Project Link: [https://github.com/jesswhyte/floppycapture](https://github.com/jesswhyte/floppycapture)

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- ACKNOWLEDGMENTS -->
# Acknowledgments

* Contributors: [Jess Whyte](https://github.com/jesswhyte) [Andy Foster](https://github.com/fozboz) [Ken Lui](https://github.com/kenlhlui)
* README Template: [othneildrew/Best-README-Template](https://github.com/othneildrew/Best-README-Template)

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[contributors-shield]: https://img.shields.io/github/contributors/jesswhyte/floppycapture.svg?style=for-the-badge
[contributors-url]: https://github.com/jesswhyte/floppycapture/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/jesswhyte/floppycapture.svg?style=for-the-badge
[forks-url]: https://github.com/jesswhyte/floppycapture/network/members
[stars-shield]: https://img.shields.io/github/stars/jesswhyte/floppycapture.svg?style=for-the-badge
[stars-url]: https://github.com/jesswhyte/floppycapture/stargazers
[issues-shield]: https://img.shields.io/github/issues/jesswhyte/floppycapture.svg?style=for-the-badge
[issues-url]: https://github.com/jesswhyte/floppycapture/issues
[license-shield]: https://img.shields.io/github/license/jesswhyte/floppycapture.svg?style=for-the-badge
[license-url]: https://github.com/jesswhyte/floppycapture/blob/master/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://linkedin.com/in/linkedin_username
[product-screenshot]: images/screenshot.png
[Next.js]: https://img.shields.io/badge/next.js-000000?style=for-the-badge&logo=nextdotjs&logoColor=white
[Next-url]: https://nextjs.org/
[React.js]: https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB
[React-url]: https://reactjs.org/
[Vue.js]: https://img.shields.io/badge/Vue.js-35495E?style=for-the-badge&logo=vuedotjs&logoColor=4FC08D
[Vue-url]: https://vuejs.org/
[Angular.io]: https://img.shields.io/badge/Angular-DD0031?style=for-the-badge&logo=angular&logoColor=white
[Angular-url]: https://angular.io/
[Svelte.dev]: https://img.shields.io/badge/Svelte-4A4A55?style=for-the-badge&logo=svelte&logoColor=FF3E00
[Svelte-url]: https://svelte.dev/
[Laravel.com]: https://img.shields.io/badge/Laravel-FF2D20?style=for-the-badge&logo=laravel&logoColor=white
[Laravel-url]: https://laravel.com
[Bootstrap.com]: https://img.shields.io/badge/Bootstrap-563D7C?style=for-the-badge&logo=bootstrap&logoColor=white
[Bootstrap-url]: https://getbootstrap.com
[JQuery.com]: https://img.shields.io/badge/jQuery-0769AD?style=for-the-badge&logo=jquery&logoColor=white
[JQuery-url]: https://jquery.com 
