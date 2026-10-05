# Fashion Recommendation System

A deep learning based fashion recommender. Upload a photo of a clothing item and the app shows the 5 most visually similar products from a catalog of about 44,000 fashion images.

## How It Works

1. **Feature extraction:** Each image is resized to 224x224 pixel and passed through a pre-trained **ResNet50** (ImageNet weights, without the top classification layer). A Global Max Pooling layer turns the output into a 2048-number feature vector (embedding).
2. **Normalization:** Each vector is normalized so images can be compared fairly.
3. **Similarity search:** When you upload an image, its features are extracted the same way. **K-Nearest Neighbors** (scikit-learn, Euclidean distance) finds the closest vectors in the catalog.
4. **Output:** The Streamlit app displays the 5 most similar products.

## Tech Stack

Python, TensorFlow / Keras (ResNet50), scikit-learn, NumPy, Streamlit, Pillow, OpenCV

## Project Structure

| File | What it does |
|------|--------------|
| `app.py` | Reads all images from the `images/` folder, extracts features and saves `embeddings.pkl` and `filenames.pkl` |
| `main.py` | Streamlit web app: upload an image and get recommendations |
| `test.py` | Quick test script: runs one sample image and shows results with OpenCV |
| `styles.csv` | Product details (category, colour, season, name) for each image |
| `requirements.txt` | Python libraries needed |

## Dataset

Uses a fashion product image dataset of about 44,000 items (`styles.csv` has the product details). Images are not included in this repo because of size. Download the dataset (for example, the *Fashion Product Images* dataset on Kaggle) and place the images in a folder named `images/`.

## How to Run

1. Clone the repo and install the libraries:
   ```
   pip install -r requirements.txt
   ```
2. Put the dataset images inside an `images/` folder.
3. Generate the embeddings (this takes a while for 44,000 images):
   ```
   python extract-features.py
   ```
4. Start the web app:
   ```
   streamlit run main.py
   ```
5. Open the link shown in the terminal, upload an image and view the recommendations.

> `embeddings.pkl` is about 365 MB, so it is not stored on GitHub. Step 3 creates it on your own computer.

## Author

Bhavika 
[LinkedIn](https://linkedin.com/in/Bhavika-khubani-a069a5265) | [GitHub](https://github.com/lbhavi2315-hub)
