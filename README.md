# ImageSearch

ImageSearch is a repository designed for fetching and organizing image datasets from the Open Images v7 dataset. It allows users to easily download a specified number of image samples for multiple classes and organizes the data in a structured format.

## Features
- Fetch images for specified classes from the Open Images v7 dataset.
- Automatically organizes images into class-specific folders.
- Generate embeddings for images using state-of-the-art models.
- Store embeddings efficiently using FAISS for further use.

---

## Directory Structure
The repository is organized as follows:
```
ImageSearch/
├── 1) Data_Collection/
|   ├── csv_folder/
|   ├── Dataset/
|       ├── train/
|           ├── Class_Name_1/
|               ├── Label/
|                   ├── image1.jpg
|                   ├── image2.jpg
|                   ...
|           ├── Class_Name_2/
|               ├── Label/
|                   ├── image1.jpg
|                   ├── image2.jpg
|                   ...
├── 2) Images_to_Embeddings/
    ├── CLIP/
        ├── clip_embeddings.ipynb
    ├── DINOV2/
        ├── dinov2_embeddings.ipynb
    ├── ImageGPT/
        ├── imagegpt_embeddings.ipynb
```

---

## Prerequisites
- Python 3.8+
- pip (Python package manager)

Ensure that the necessary libraries are installed before running the commands.

---

## How to Use

### 1) Data Collection

#### Step 1: Install Dependencies
Navigate to the `1) Data_Collection` directory and install the required dependencies by running:
```bash
pip install -r requirements.txt
```

#### Step 2: Download Images
Run the following command in the terminal:
```bash
python main.py downloader -y --classes classes.txt --type_csv train --limit 600
```

- `--classes`: Specifies the file containing the list of classes to download.
- `--type_csv`: Defines the dataset type (e.g., train, test).
- `--limit`: Limits the number of samples per class (default is 600 in this example).

This command will fetch all the classes specified in `classes.txt` and download 600 samples for each class. The output will be organized as shown above.

### 2) Generate Embeddings

#### Step 1: Choose an Embedding Model
Navigate to the `2) Images_to_Embeddings` directory. Choose one of the available models:
- `CLIP/clip_embeddings.ipynb`
- `DINOV2/dinov2_embeddings.ipynb`
- `ImageGPT/imagegpt_embeddings.ipynb`

#### Step 2: Set Image Folder Path
Inside the selected notebook, specify the path to the image folder. For example:
```python
images_folder_path = "../../1) Data_Collection/OID/Dataset/train"
```

#### Step 3: Run the Notebook
Execute the cells in the notebook to generate embeddings. The embeddings will be stored in a binary file using the FAISS library. For instance:
- For `CLIP`, embeddings are stored in the `clip_embeddings` folder.
- For `DINOV2`, embeddings are stored in the `dinov2_embeddings` folder.
- For `ImageGPT`, embeddings are stored in the `imagegpt_embeddings` folder.

---

## Example
If your `classes.txt` contains the following:
```
Bed
Chair
Sofa
```
Running the command in `1) Data_Collection` will create folders like `Dataset/train/Bed`, `Dataset/train/Chair`, and `Dataset/train/Sofa` with 600 images in each folder. Then, running a notebook in `2) Images_to_Embeddings` will generate embeddings for these images and save them in the respective embeddings folder.

---

## Notes
- Ensure you have a stable internet connection while running the downloader.
- You can modify the number of samples fetched by changing the `--limit` value.
- The embedding notebooks are designed to work with various models. Ensure the required libraries are installed for the selected model.

---

## License
This project is licensed under the MIT License. See the `LICENSE` file for details.

---

## Contributions
Contributions, issues, and feature requests are welcome! Feel free to submit a pull request or open an issue on the repository.

---

## Author
This repository is maintained by Hamza Khan, Sana Fatima Ammad and Sofia Shafiq.