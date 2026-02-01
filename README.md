# FastAPI OCR

A FastAPI-based web service that performs Optical Character Recognition (OCR) on uploaded images using Tesseract OCR.

## Features

- Upload images via REST API
- Extract text from images using Tesseract OCR
- Support for multiple image formats
- Fast and efficient processing with FastAPI
- Simple and clean API endpoint

## Prerequisites

Before running this project, ensure you have the following installed:

- Python 3.7+
- Tesseract OCR
- pip (Python package manager)

### Installing Tesseract OCR

#### Windows
Download and install Tesseract from [GitHub](https://github.com/UB-Mannheim/tesseract/wiki).

Update the path in `main.py` to match your installation:
```python
pytesseract.pytesseract.tesseract_cmd = r"C:\Program Files\Tesseract-OCR\tesseract.exe"
```

#### macOS
```bash
brew install tesseract
```

#### Linux
```bash
sudo apt-get update
sudo apt-get install tesseract-ocr
```

## Installation

1. Clone the repository:
```bash
git clone <your-repo-url>
cd fastapi-ocr
```

2. Create a virtual environment:
```bash
python -m venv env
```

3. Activate the virtual environment:
   - **Windows:**
     ```bash
     env\Scripts\activate
     ```
   - **macOS/Linux:**
     ```bash
     source env/bin/activate
     ```

4. Install dependencies:
```bash
pip install -r requirements.txt
```

## Usage

1. Start the FastAPI server:
```bash
uvicorn main:app --reload
```

2. The API will be available at `http://127.0.0.1:8000`

3. Access the interactive API documentation at `http://127.0.0.1:8000/docs`

### API Endpoint

#### POST `/ocr`

Upload an image file to extract text.

**Request:**
- Method: `POST`
- Content-Type: `multipart/form-data`
- Body: Form data with file upload (key: `image`)

**Response:**
```json
{
  "text": "Extracted text from the image"
}
```

**Example using cURL:**
```bash
curl -X POST "http://127.0.0.1:8000/ocr" \
  -H "accept: application/json" \
  -H "Content-Type: multipart/form-data" \
  -F "image=@/path/to/your/image.png"
```

**Example using Python:**
```python
import requests

url = "http://127.0.0.1:8000/ocr"
files = {"image": open("image.png", "rb")}
response = requests.post(url, files=files)
print(response.json())
```

## Project Structure

```
fastapi-ocr/
│
├── main.py              # Main FastAPI application
├── requirements.txt     # Python dependencies
├── README.md           # Project documentation
├── .gitignore          # Git ignore file
└── env/                # Virtual environment (not tracked)
```

## Dependencies

- FastAPI - Modern web framework for building APIs
- pytesseract - Python wrapper for Tesseract OCR
- shutil - File operations
- uvicorn - ASGI server for FastAPI

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## Troubleshooting

### Tesseract not found
If you get an error that Tesseract is not found, make sure:
1. Tesseract is installed on your system
2. The path in `main.py` is correctly set to your Tesseract installation
3. The Tesseract binary is in your system PATH

### File upload errors
Ensure the uploaded file is a valid image format (PNG, JPG, JPEG, etc.)

## Future Enhancements

- [ ] Support for multiple languages
- [ ] PDF text extraction
- [ ] Batch image processing
- [ ] Image preprocessing options
- [ ] Docker containerization
- [ ] Rate limiting
- [ ] Authentication

## Contact

For questions or support, please open an issue on GitHub.
