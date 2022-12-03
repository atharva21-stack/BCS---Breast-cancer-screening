
# Breast Cancer Screening 🎗

![Stargazers](https://img.shields.io/github/stars/atharva21-stack/BCS-Breast-cancer-screening)
![Issues](https://img.shields.io/github/issues/atharva21-stack/BCS-Breast-cancer-screening)
![Forks](https://img.shields.io/github/forks/atharva21-stack/BCS-Breast-cancer-screening)

## Introduction 👋
This is an implementation of the breast cancer categorization model. 
The implementation allows users to receive breast cancer predictions by using one of two pretrained models: an image-only model (*image-only*) and an image-and-heatmaps model (*image-and-heatmaps*).


## Features 🚀

- Uses two models 
        
        1) Model which takes images as input
        2) Model which takes images and heatmaps as input
- Gives four standard views

        1) L-CC
        2) R-CC
        3) L-MLO
        4) R-MLO
- Both models act on screening mammography exams 
- Automatically run the entire pipeline and save the prediction results in csv. 

## Process 🔀
* Input images: 2 CC view mammography images of 2677x1942 and 2 MLO view mammography images of 2974x1748 were used as input images. Before being supplied to the models, each image is saved as a 16-bit png file and standardised independently.
* Input heatmaps: The patch classifier output is designed to have the same size as the related mammography. For each mammogram, two heatmaps are created, one for the benign category and one for the malignant category. Each pixel in both of them has a value between 0 and 1.
* Output: There are two forecasts for each breast, based on the probability of benign and malignant findings: `left_benign`, `right_benign`, `left_malignant`, and `right_malignant`.

With four conventional views, both versions provide screening mammography exams (L-CC, R-CC, L-MLO, R-MLO). We supply four sample tests as part of this repository (in the'sample data/images' directory, with the exam list recorded in 'exam list before cropping.pkl'). PyTorch includes heatmap generation and cancer classification methods.

## Installation ⏬

* Python (3.11.0)
* pandas (1.5.2)
* PyTorch (1.13.0)
* opencv-python (4.6.0)
* NumPy (1.23.5)
* SciPy (1.6.0)
* H5py (3.7.0)
* torchvision (0.14.0)
* tqdm (4.64.1)
* imageio (2.22.4)
## Pipeline 🗜
The pipeline has four stages.

- Crop mammograms
- Calculate optimal centers
- Generate Heatmaps
- Run classifiers

## Running Tests 🏃‍♀️💨

### Exam 🤖

Here we describe how to get predictions from *view-wise* model, which is our best-performing model. This model takes 4 images from each view as input and outputs predictions for each exam.

```bash
bash run.sh
``` 
will automatically run the entire pipeline and save the prediction results in csv. 

We recommend running the code with a gpu (set by default). To run the code with cpu only, please change `DEVICE_TYPE` in `run.sh` to 'cpu'.  

If running the individual Python scripts, please include the path to this repository in your `PYTHONPATH` . 


### Single Image 🖼

Here, we have also upload *image-wise* model, which is different from and performs worse than the *view-wise* model described above. In this part, the csv output from the *view-wise* model will differ from that of the *image-wise* model. We offer this model available to assist transfer learning because it has the advantage of creating predictions for each image separately.

To use the *image-wise* model, run a command such as the following:

```bash
bash run_single.sh "sample_data/images/0_L_CC.png" "L-CC"
``` 

where the first argument is path to a mammogram image, and the second argument is the view corresponding to that image.

### Image-level Notebook ⚒

We have provided a [sample notebook](https://github.com/atharva21-stack/BCS-Breast-cancer-screening/blob/main/sample_notebook.ipynb) that have code for running the classifiers with and without heatmaps (excludes preprocessing).

## Data ℹ

In order to use one of the pretrained models, the input must include at least four photos, one for each view (L-CC, L-MLO, R-CC, R-MLO).

To keep the granularity of the pixel intensities while still displaying correctly in image viewers, the original 12-bit mammograms are saved as rescaled 16-bit images.
`sample_notebook.ipynb` contains a list of exam information before preprocessing.



## License 📜
[![MIT License](https://img.shields.io/badge/License-MIT-green.svg)](https://choosealicense.com/licenses/mit/)


## Contributing ✨

Contributions are always welcome!

See [CONTRIBUTING.md](https://github.com/atharva21-stack/BCS-Breast-cancer-screening/blob/main/CONTRIBUTING.md) for ways to get started.

Please adhere to this project's [CODE-OF-CONDUCT.md](https://github.com/atharva21-stack/BCS-Breast-cancer-screening/blob/main/CODE-OF-CONDUCT.md).




## Contributors 🤝

  <a name = "contributors"></a>
<table align="center">
<tr>
<td>
<a href="https://github.com/atharva21-stack/BCS-Breast-cancer-screening/graphs/contributors" align="center">
  <img src="https://contrib.rocks/image?repo=atharva21-stack/BCS-Breast-cancer-screening" /> 
</a>
</td>
</tr>
</table>


## Authors 👨‍💻

- [@atharva21-stack](https://www.github.com/atharva21-stack)

## Links 🔗
[![linkedin](https://img.shields.io/badge/linkedin-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/atharva21/)
[![twitter](https://img.shields.io/badge/twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white)](https://twitter.com/Atharva_2100)


## Feedback 🙋‍
If you have any feedback, please reach out to me at <a src="mailto:chandwadkar28@gmail.com">chandwadkar28@gmail.com</a>