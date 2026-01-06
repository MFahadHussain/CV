# YOLO-World V2 Video Detector

Enhanced YOLO-World V2 Video Detector with Multiple Polygon ROI Cropping, Editing, and BoT-SORT Tracking.

## Features

- **Multiple Polygon ROI Selection**: Define and edit multiple polygon regions of interest
- **Web Interface**: Modern, responsive web UI with live video preview
- **BoT-SORT Tracking**: Robust object tracking with fallback to ByteTrack
- **Thread-Safe Video Processing**: Efficient video I/O with background threads
- **Real-time Preview**: Live frame streaming during processing
- **Error Handling**: Comprehensive error handling throughout the pipeline

## Project Structure

```
VISION_YOLO/
├── web/                      # Web application module
│   ├── __init__.py
│   ├── app.py               # Flask app factory
│   ├── config.py            # Configuration
│   ├── routes.py            # API routes
│   └── services.py          # Business logic
├── detection/               # Detection module
│   ├── __init__.py
│   └── detector.py          # YOLO-World detector
├── tracking/                # Tracking module
│   ├── __init__.py
│   └── tracker.py           # BoT-SORT wrapper
├── video/                   # Video I/O module
│   ├── __init__.py
│   ├── video_reader.py      # Thread-safe reader
│   └── video_writer.py      # Thread-safe writer
├── models/                  # Data models
│   ├── __init__.py
│   └── data_models.py        # PolygonROI, ROIConfig, Detection
├── utils/                   # Utilities
│   ├── __init__.py
│   ├── logger_config.py     # Logging setup
│   └── model_checker.py      # Model validation
├── static/                  # Web static files
│   ├── app.js               # Frontend JavaScript
│   └── style.css            # Stylesheet
├── templates/               # HTML templates
│   └── index.html           # Main page
├── main.py                  # CLI entry point
├── web_app.py               # Legacy web entry (redirects to web/app.py)
├── requirements.txt         # Dependencies
└── README.md                # This file
```

## Installation

1. Install dependencies:
```bash
pip install -r requirements.txt
```

2. Ensure you have the YOLO-World model file (`yolov8l-worldv2.pt`) in the project directory.

## Usage

### Web Interface (Recommended)

1. Start the web server:
```bash
python web/app.py
# or
./start_web.sh
```

2. Open your browser:
```
http://localhost:8000
```

3. Upload video, select ROI, configure settings, and process!

### Command Line Interface

```bash
# Basic usage
python main.py -i video.mp4 -o output.mp4

# With custom classes
python main.py -i video.mp4 -o output.mp4 -c "person" "car" "dog"

# Without tracking
python main.py -i video.mp4 -o output.mp4 --no-tracking

# Custom confidence threshold
python main.py -i video.mp4 -o output.mp4 --conf 0.5
```

## Dependencies

- `ultralytics>=8.0.0` - YOLO-World model
- `opencv-python>=4.5.0` - Video processing
- `supervision>=0.27.0` - Tracking (BoT-SORT/ByteTrack)
- `numpy>=1.21.0` - Numerical operations
- `flask>=2.0.0` - Web framework
- `werkzeug>=2.0.0` - WSGI utilities

## Architecture

The project follows a modular architecture:

- **Web Module** (`web/`): Flask application with separated concerns
  - `app.py`: Application factory
  - `config.py`: Configuration management
  - `routes.py`: API endpoints
  - `services.py`: Business logic (JobManager, VideoProcessor, VideoService)

- **Core Modules**: Reusable components
  - `detection/`: YOLO-World detection
  - `tracking/`: Object tracking
  - `video/`: Video I/O operations
  - `models/`: Data structures
  - `utils/`: Utility functions

## License

This project uses YOLO-World V2 from Ultralytics and supervision library.
# CV
# CV
