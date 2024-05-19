<!-- Improved compatibility of back to top link: See: https://github.com/othneildrew/Best-README-Template/pull/73 -->
<a name="readme-top"></a>


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
[![LinkedIn][linkedin-shield]][linkedin-url]


<br />
<div align="center">
  <a href="https://github.com/skyswpark/GEOL0069_Project">
  </a>

<h3 align="center">Comparison of Unsupervised and Supervised Classification Methods for Classifying Sea Ice, Lead, and Clouds</h3>

  <p align="center">
    <br />
    <a href="https://github.com/skyswpark/GEOL0069_Project"><strong>Explore the docs »</strong></a>
    <br />
    <br />
  </p>
</div>



<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
      </ul>
    </li>
    <li>
      <a href="#understanding-the-code-variables-and-functions">Understanding the Code: Variables and Functions</a>
    </li>
    <li>
      <a href="#results">Results</a>
    </li>
    <li><a href="#contributing">Contributing</a></li>
    <li><a href="#contact">Contact</a></li>
    <li><a href="#acknowledgments">Acknowledgments</a></li>
  </ol>
</details>



<!-- ABOUT THE PROJECT -->
## About The Project
This project aims to
1. Produce two different masks with IRIS for Sea Ice and Lead classification with clouds
2. Conduct supervised and unsupervised classification for a Sentinel-3 image
3. Comparison of the different classifications

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- GETTING STARTED -->
## Getting Started


### Prerequisites

* This project uses Google Colab to run the scripts. When using Google Colab, you will need a Google account for access to Colab and your Google drive.
* You may run the script on a different platform. Edit the file paths (directories) to properly locate your files.
* Sentinel-2 optical data, Sentinel-3 OLCI, and altimetry data are used in this project. You will need an account (username and password) to download the data from the Copernicus dataspace.


<p align="right">(<a href="#readme-top">back to top</a>)</p>


<!-- USAGE -->
## Understanding the Code: Variables and Functions


### Variables

* clusters_gmm: The clusters for each data point determined by the Gaussian Mixture Model (GMM). 'n_components' determines the number of components.
* flag: The initial classification flags derived from the Sentinal-3 data.
* waves: Waveform data for the observation points.
* flag_cleaned: Cleaned version of 'flag', where NaN values are removed from 'flag'.
* esa_flag_cleaned: Modified version of 'flag_cleaned' to be used for the confusion matrix. 'esa_flag_cleaned' has the true labels while 'clusters_gmm' has the predicted labels.
* waves_cleaned: Cleaned version of 'waves', where NaN values are removed from 'waves'.
* data_normalized: Standardized data containing sig_0_np (backscatter coefficient), PP_np (peakiness), and SSD_np (sum of squared differences).
* cm: Confusion matrix that compares 'esa_flag_cleaned', which has the true labels, and 'clusters_gmm', which has the predicted labels.


### Functions

In SWP_Chapter1_Unsupervised_Learning_Methods_Michel.ipynb you will find:

* **peakiness** : Calculates the peakiness of waveforms, which is a measure that compares the maximum amplitude of a waveform to its average amplitude within a specific window around the peak.

* **unpack_gpod** : Handles the unpacking and interpolation of variables from a Generic Product Output Data (GPOD) format.

* **calculate_SSD** : Calculates the Sum of Squared Differences (SSD) for a set of waveforms, which is a measure of the variance or spread of each waveform around its mean.
s
<p align="right">(<a href="#readme-top">back to top</a>)</p>


## Results

The tasks in this notebook will be mainly two:

* Discrimination of Sea ice and lead based on image classification based on Sentinel-2 optical data.
* Discrimination of Sea ice and lead based on altimetry data classification based on Sentinel-3 altimetry data.

<br />

Image classification based on Sentinel-2 optical data is done using both K-means clustering and GMM clustering.
Altimetry data classification based on Sentinel-3 altimetry data is done using GMM clustering.

After classifying ice and lead from the Sentinel-3 altimetry data we can produce an average echo shape and standard deviation echo shape for the two classes, ice and lead. Then a confusion matrix is produced to quantify your echo classification against the ESA official classification.

<br />

* RGB Image Produced from Sentinel-3 Data

<br />
<p align="center">
  <img src="https://github.com/skyswpark/GEOL0069_Project/assets/122312438/deead6ec-3fa9-4fe0-9794-8075359768df" alt="RGB">
</p>

<br />
<br />

* Supervised Classification #1 CNN (2 Classes vs. 4 Classes)

<br />
<p align="center">
  <img src="https://github.com/skyswpark/GEOL0069_Project/assets/122312438/6509177b-341f-40c5-8cca-93bce7bf7b13" alt="CNN_2_Classes">
  <img src="https://github.com/skyswpark/GEOL0069_Project/assets/122312438/22a38527-404c-409d-81c9-981319c8c00f" alt="CNN_4_Classes">
</p>

<br />
<br />

* Supervised Classification #2 RF (2 Classes vs. 4 Classes)

<br />
<p align="center">
  <img src="https://github.com/skyswpark/GEOL0069_Project/assets/122312438/b3ec5af4-8176-4edf-badb-06ded9da949c" alt="RF_2_Classes">
  <img src="https://github.com/skyswpark/GEOL0069_Project/assets/122312438/83a457fd-8ecb-4eec-95d2-216d661ec1ab" alt="RF_4_Classes">
</p>!

<br />
<br />

* Supervised Classification #3 ViT (2 Classes vs. 4 Classes)

<br />
<p align="center">
  <img src="https://github.com/skyswpark/GEOL0069_Project/assets/122312438/9ea9051c-74d8-4290-9373-42146a1189cb" alt="ViT_2_Classes">
  <img src="https://github.com/skyswpark/GEOL0069_Project/assets/122312438/0d574bdb-e6ab-45e5-8742-ab6179110b0e" alt="ViT_4_Classes">
</p>!

<br />
<br />

* Unsupervised Classification GMM (2 Classes vs. 4 Classes)

<br />
<p align="center">
  <img src="https://github.com/skyswpark/GEOL0069_Project/assets/122312438/13d3bcc3-b68b-4211-b1eb-f52ec8eb69e0" alt="GMM_2_vs_4">
</p>!

<br />
<br />

* Unsupervised Classification GMM (4 Classes vs. Classes Combined)

<br />
<p align="center">
  <img src="https://github.com/skyswpark/GEOL0069_Project/assets/122312438/10f26100-17f6-4845-94a2-13037db1352b" alt="GMM_4_vs_Combined">
</p>!

<br />
<br />


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
## Contact

Skylar Park - sun.park.20@ucl.ac.uk

Project Link: [https://github.com/skyswpark/Week_4_Assignment](https://github.com/skyswpark/Week_4_Assignment)

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- ACKNOWLEDGMENTS -->
## Acknowledgments

* University College London (UCL) Module GEOL0069: Artificial Intelligence for Earth Observation
* Template for README file: https://github.com/othneildrew/Best-README-Template/tree/master


<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[contributors-shield]: https://img.shields.io/github/contributors/skyswpark/Week_4_Assignment.svg?style=for-the-badge
[contributors-url]: https://github.com/skyswpark/Week_4_Assignment/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/skyswpark/Week_4_Assignment.svg?style=for-the-badge
[forks-url]: https://github.com/skyswpark/Week_4_Assignment/network/members
[stars-shield]: https://img.shields.io/github/stars/skyswpark/Week_4_Assignment.svg?style=for-the-badge
[stars-url]: https://github.com/skyswpark/Week_4_Assignment/stargazers
[issues-shield]: https://img.shields.io/github/issues/skyswpark/Week_4_Assignment.svg?style=for-the-badge
[issues-url]: https://github.com/skyswpark/Week_4_Assignment/issues
[license-shield]: https://img.shields.io/github/license/skyswpark/Week_4_Assignment.svg?style=for-the-badge
[license-url]: https://github.com/skyswpark/Week_4_Assignment/blob/master/LICENSE.txt
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
