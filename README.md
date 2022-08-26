# Impactful Weather
Coordinating repo for ESGF + Climate in Society + AI Foundry (ANL, UC, NIU) 

## References
One can find important notes/references which we used throughout the project in [`/references`](/references)

## Updates
Porgress Updates can be found in [`/updates`](/updates)

## Notebooks
Jupyter notebooks containing experimentation and results can be found in [`/notebooks`](/notebooks)
The notebooks are listed below:
1. [`low-resolution-images-to-high-resolution.ipynb`](/notebooks/low-resolution-images-to-high-resolution.ipynb)
    1. Contains our initial experimentation with a basic UNet Model.
    2. We also tested this out with an SRCNN model and found the UNet Model to work better.
    3. Running the notebook with the proper data outputs relatively good, but not great, results.
2. [`16-to-32-model.ipynb`](/notebooks/16-to-32-model.ipynb)
    1. This notebook contains the final training and evaluation of a model which goes from 16x16 resolution to 32x32 resolution (pixels)
    2. This was one of the 3 models in our stacking experimentation, where we stepped up resolution scales, similar to the DeepSD paper.
3. [`8-to-16-model.ipynb`](/notebooks/8-to-16-model.ipynb)
    1. This notebook contains the final training and evaluation of a model which goes from 8x8 resolution to 16x16 resolution (pixels)
    2. This was one of the 3 models in our stacking experimentation, where we stepped up resolution scales, similar to the DeepSD paper.
4. [`5-to-8-model.ipynb`](/notebooks/5-to-8-model.ipynb)
    1. This notebook contains the final training and evaluation of a model which goes from 5x5 resolution to 8x8 resolution (pixels)
    2. This was one of the 3 models in our stacking experimentation, where we stepped up resolution scales, similar to the DeepSD paper.
5. [`combining-models.ipynb`](/notebooks/combining-models.ipynb)
    1. This notebook combines all the models from the previous 3 notebooks into one model, and runs evaluation on the dataset
    2. We find this to give very good results (much better than going straight from 5 to 32)

## Papers used

1. https://arxiv.org/pdf/1703.03126.pdf
    1. Used for the basic structure of the stacking model
2. https://arxiv.org/pdf/1501.00092.pdf
    1. Used for benchmarking our results
3. https://openaccess.thecvf.com/content_ICCV_2017/papers/Tong_Image_Super-Resolution_Using_ICCV_2017_paper.pdf
    1. Used for benchmarking our results
