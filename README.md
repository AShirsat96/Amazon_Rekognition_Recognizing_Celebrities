# AWS Rekognition Celebrity Recognition

A Python implementation that uses AWS Rekognition to identify celebrities in images with detailed information about each recognized face, including identity, gender, facial expressions, and relevant web links.

## Prerequisites

- Python 3.8.8
- AWS Account with Rekognition access
- AWS Access Key and Secret Key
- boto3 library

## Installation

```bash
pip install boto3
```

## Configuration

```python
aws_accesskey = "Your Access Key"
aws_secretaccess = "Your Secret Access Key"
myregion = "your-region"
```

## Main Function

```python
def Recognise_Celebrity(aws_access, aws_secret, aws_region, photo_name):
    """
    Analyzes an image for celebrity faces.
    
    Args:
        aws_access: AWS access key
        aws_secret: AWS secret key
        aws_region: AWS region name
        photo_name: Local path to image file
        
    Returns:
        int: Number of celebrities detected
    
    Output:
        Prints detailed information about each detected celebrity
    """
```

## Features

### Detection Information
For each detected celebrity, the function returns:
- Name
- Unique ID
- Known gender
- Smile detection (True/False)
- Face position (bounding box coordinates)
- Reference URLs (Wikipedia, IMDB)

## Usage Example

```python
celebrity_count = Recognise_Celebrity(
    aws_accesskey,
    aws_secretaccess,
    "us-west-2",
    "path/to/image.jpg"
)
```

## Output Format Example
```
Detected faces for celebrity_image.jpg
Name: Brad Pitt
Id: 1q4IR5
KnownGender: Male
Smile: True
Position:
   Left: 0.23
   Top: 0.00
Info
   www.wikidata.org/wiki/Q35332
   www.imdb.com/name/nm0000093
```

## Known Limitations and Observations

1. Regional Recognition:
   - Better recognition rate for Western celebrities
   - May misidentify or fail to recognize celebrities from other regions

2. Image Quality Dependencies:
   - Clear facial visibility required
   - Recognition affected by facial expressions
   - Lighting conditions impact accuracy

3. Specific Challenges:
   - May confuse character names with actor names (e.g., "Mastani" vs "Deepika Padukone")
   - Facial hair can affect recognition accuracy
   - Multiple faces in single image may affect accuracy

## Best Practices

1. Image Selection:
   - Use clear, high-quality images
   - Ensure good lighting
   - Front-facing poses preferred
   - Minimal occlusion of face

2. Error Handling:
   - Implement checks for failed recognitions
   - Validate image format and size
   - Handle API limits appropriately

3. Performance:
   - Consider image size optimization
   - Implement batch processing for multiple images
   - Monitor API usage limits

## API Response Handling

The implementation processes:
- Successfully recognized celebrities
- Face position coordinates
- Biographical information
- Reference links
- Confidence scores
