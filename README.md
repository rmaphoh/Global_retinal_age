## Global Retinal Age
Docker instruction for the project predicting retinal age, mainly investigating its generalisability and fairness.

### Hardware requirements

- A consumer-grade GPU (~16GB) is essential for model training. 


### Data requirements

- To develop local retinal age model, please include ~100k-200k images. The docker running will take around 3-5 days. 

- To support only cross validation, please include ~10k-50k images. The docker running will take around 1-2 days. 


### Data preparation

1. Put the images into `Images` folder (both png and jpg formats are fine).

```
├──Images
    ├──1.jpg
    ├──2.jpg
    ├──3.jpg
``` 

2. Generate a `metadata.csv` file including the metadata.

- The columns of "Patient_id", "Image", and "Age" should be available.

- If some other variables are missing / not known, then leave them BLANK.

- Save the metadata.csv in the same path as `Images` folder

```
├──Images
    ├──1.jpg
    ├──2.jpg
    ├──3.jpg
├──metadata.csv   
``` 

An example can be found [here](https://drive.google.com/file/d/1tDwguNTdByc7N0CNOmtU6TppRe548P1D/view?usp=sharing).



### Install Docker

If you have not installed Docker on your machine. Please follow [official instructions](https://docs.docker.com/engine/install/).
<br><br><br>



=========================================================

### 🍻🍻🍻 Run the docker - developing a local retinal age model


1. Download the docker

```
docker pull yukunzhou/retinal_age_train
``` 

2. Run it

Please substitute the `{Absolute_path}` with the path to `Images` folder.
```
docker run --gpus all -it --shm-size=8g -v {Absolute_path}:/app/Retinal_age yukunzhou/retinal_age_train
```
e.g.`docker run --gpus all -it --shm-size=8g -v /home/retinal_age:/app/Retinal_age yukunzhou/retinal_age_train`

```
├──retinal_age
    ├──Images
    ├──metadata.csv  
``` 

The process will generate a `metadata_processed.csv` and `output_dir` folder in `{Absolute_path}` path.


3. Share model weights and results

Please zip `metadata_processed.csv` and `output_dir` folder, and share them through storage platforms, e.g. Google Drive and OneDrive.
<br><br><br>



=========================================================

### 🍻🍻🍻 Run the docker - external evaluation


1. Download the docker

```
docker pull yukunzhou/retinal_age_test
``` 

2. Run it

Please substitute the `{Absolute_path}` with the path to `Images` folder.
```
docker run --gpus all -it --shm-size=8g -v {Absolute_path}:/app/Retinal_age yukunzhou/retinal_age_test
```
e.g.`docker run --gpus all -it --shm-size=8g -v /home/retinal_age:/app/Retinal_age yukunzhou/retinal_age_test`

```
├──retinal_age
    ├──Images
    ├──metadata.csv  
``` 

The process will generate a `metadata_processed.csv` and `output_dir` folder in `{Absolute_path}` path.


3. Share results

Please zip `metadata_processed.csv` and `output_dir` folder, and share them through storage platforms, e.g. Google Drive and OneDrive.




### Citation

TBC


