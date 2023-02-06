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

📝Note: This is an environment-specific, institution-specific (e.g. calls the UTL catalog) script, but could be modified. For a more generalized version, see [floppy-nocall.py](##floppy-nocall.py).

### Usage

  ```floppy.py
  python3 floppy.py [-h LIB] -l -d DIR -m 3.5,5.25 -c CALL [-k KEY] [-i]
  ```

## floppy-nocall.py
floppy-nocall.py is a generalized version of floppy.py (it doesn't attempt to call the UTL catalog or take a photo). 
It's a workflow script to image floppy disks (3.5" and 5.25") using a kryoflux two-drive setup. 

### Usage

  ```floppy-nocall.py
  python3 floppy-nocall.py -c COLLECTION -d DIR -m MEDIATYPE -t "TRANSCRIPT" -k KEY [-i]
  ```

#### Required arguement
| Parameters 	|  Name 	|Argument| Description 	|Example|
|:---------:	|:-----------:	|:------------------------------:	|:----------------------------------------------------------------------------------------------------------------------:	|:----------------------:	|
| -c        	| COLLECTION  	| {directory-name-of-collection} 	| The collection name. This will be the second level of the files directory.                                             	| -c testing01-floppy    	|
| -d        	| DIR         	| {top-directory-name}           	| The top directory name. Usually, it should be placed under /mnt/data.                                                  	| -d /mnt/data/testing01 	|
| -m        	| MEDIATYPE   	| 3.5 / 5.25                       	| The size of the disk. Put the corresponding number after -m.                                                           	| -m 3.5                 	|
| -t        	| TRANSCRIPT  	| {transcript-of-disk-label}     	| Transcript (note) of the disk label. Input the written notes on the disks with quotes here. No comma is allowed in this argument 	| -t "information ABC"   	|
| -k        	| KEY         	| {disk-id}                      	| The Disk ID. This is also the name of the base directory of the disk image file (& photo of the disk).                 	| -k testing01-01        	|

#### Optional arguement
| Parameters 	| Name 	| Argument 	| Description 	| Example 	|
|:---:	|:---:	|:---:	|:---:	|:---:	|
| -i 	|  /	| 0 / 2 / 4 / 9  	| The orginal disk type. For MFM, it is 4. For Apple DOS 400K/800K, it is 9. See [Kyroflux manual](https://www.kryoflux.com/download/kryoflux_manual.pdf) (P.14-15) for more reference. 	| -i4 	|

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CONTRIBUTING -->
## Contributing

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

* Authors: [Jess Whyte](https://github.com/jesswhyte) [Andy Foster](https://github.com/fozboz)
* README update: [Ken Lui, TALint Intern, UTL Digital Preservation Unit](https://github.com/kenlhlui)
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
