# Project 7 - WordPress Pentesting

Time spent: **5** hours spent in total

> Objective: Find, analyze, recreate, and document **vulnerabilities** affecting an old version of WordPress

## Pentesting Report

1. (Required) Large File Upload Error XSS - Image Files
  - [X] Summary:
    - Vulnerability types: XSS
    - Tested in version: 4.2
    - Fixed in version:
  - [X] GIF Walkthrough:
  ![]xss-file-too-big-audio.gif
  - [X] Steps to recreate:
  ```
  a. ```dd if=/dev/zero of='something<img src=a onerror=(alert('pwned'))>.png' count=1024 bs=10000``` to create a large file with the script exploit.
  b. Open WordPress > Media > Add new Image
  c. Add the newly created file.
  ```
1. (Required) Authenticated Cross-Site Scripting (XSS) via Media File Metadata
  - [X] Summary:
    - Vulnerability types: XSS, Metadata
    - Tested in version: 4.2.13
    - Fixed in version: 4.2.0
  - [X] GIF Walkthrough:
  ![]xss-mp3-metadata.gif
  - [X] Steps to recreate:
  ```
  The following MP3 file can be used to reproduce this issue:

  https://www.securify.nl/advisory/SFY20160742/xss.mp3

  1) upload MP3 file to the Media Library (as Editor or Administrator).
  2) Insert an Audio Playlist in a Post containing this MP3 (Create Audio
  Playlist).
  ```
  - [X] Affected source code:
    - [Link 1](https://github.com/WordPress/WordPress/commit/28f838ca3ee205b6f39cd2bf23eb4e5f52796bd7)
1. (Required) Malformed HTML Tags
  - [X] Summary:
    - Vulnerability types: XSS, Embedded Tags
    - Tested in version: 4.2.0
    - Fixed in version: N/A
  - [X] GIF Walkthrough:
  ![]xss-caption-code-exploit.gif
  - [X] Steps to recreate:
  ```
    1) Create a new post
    2) Add the script on the text of the body: ```<a href="[caption code"]> </a> <a title=" onclick=alert("hi!")> something</a>```
    3) Publish
  ```

## Assets

N/A

## Resources

- [WordPress Source Browser](https://core.trac.wordpress.org/browser/)
- [WordPress Developer Reference](https://developer.wordpress.org/reference/)

## Notes

What took the most time out of this experience is setting up the environment. Other than that, the exploits were easy to implement once a blog post has a good overview and a proof of concept of the exploits.

## License

    Copyright [2018] [Excel Espina]

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
