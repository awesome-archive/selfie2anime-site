
![Selfie2Anime](s2a.png) 

[![Selfie2Anime](https://img.shields.io/badge/app-selfie2anime-f06292.svg?style=for-the-badge)](https://selfie2anime.com)&nbsp;
[![Version](https://img.shields.io/badge/version-1.0-05A5CC.svg?style=for-the-badge)](https://selfie2anime.com)&nbsp;
[![Status](https://img.shields.io/badge/status-live-00B20E.svg?style=for-the-badge)](https://selfie2anime.com)

# Selfie2Anime

*What do YOU look like in ANIME?*

This repository contains the source code for the [selfie2anime.com](https://selfie2anime.com) website. Upload a selfie and find out what you look like as an anime character!


# How Does it Work?

Using machine learning techniques combined with a [Generative Adversarial Network (GAN)](https://en.wikipedia.org/wiki/Generative_adversarial_network) makes it possible to generate anime-style characters based on real people. With this website, you can generate your own anime alter ego!

The GAN we are using is based on original work by *Junho Kim*, *Minjae Kim*, *Hyeonwoo Kang*, and *Kwanghee Lee*. More information can be found in their awesome repository, which is [available here](https://github.com/taki0112/UGATIT), or in [their research paper](https://arxiv.org/abs/1907.10830).


# Sample Photos

Recent anime selfies are being published on Twitter [@RicoBeti](https://twitter.com/RicoBeti).

### Here is a bunch of images that have been generated...

![Preview](wall.jpg)


### ...and here are some of Australia's Prime Ministers

![Preview](pms.png)


# Development
![AWS BAdge](https://codebuild.us-east-1.amazonaws.com/badges?uuid=eyJlbmNyeXB0ZWREYXRhIjoiZWJIeXI2TzlGWmx1eEc3dzJicFFEZ0FnZVpUK2U4LzZDeVQ2V0JhZE84bkZKK1BpQiswbG93OXlWUE96dnI1UVJzL3hucCtham43bHQrT3VDN3lmVHdnPSIsIml2UGFyYW1ldGVyU3BlYyI6IlkwbTJscTNWUlBiMEsrWTkiLCJtYXRlcmlhbFNldFNlcmlhbCI6MX0%3D&branch=master)

*(More detailed instructions will follow later)*

*   Install dependencies:
    ```bash
    npm install
    ```
    
*   Pull submodules (the blog):
    ```bash
    git submodule update --init --recursive
    ```

*   Set correct values for environment variables in the `.env` files.

*   Run a quick build to generate all assets needed for development:
    ```bash
    DISABLE_IMAGE_OPTIMIZATION=1 npm run build
    ```

*   Run development server:
    ```bash
    npm run serve
    ```
    
*   Alternatively, build the release version:
    ```bash
    npm run build
    ```
    
    Building a release version may take a long time due to generation of the portfolio and due to image optimizations being performed. In case the portfolio has not changed, set `DISABLE_PORTFOLIO_BUILD=1` to suppress regeneration of the images.
    
    For development and testing, set `DISABLE_IMAGE_OPTIMIZATION=1` to avoid wasting time on image compression.


# License

MIT, see [LICENSE.txt](LICENSE.txt).
