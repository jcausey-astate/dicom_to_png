# DICOM to PNG
Converts individual DICOM files PNG format, or directories containing DICOM
files to flattened directories of PNG images.

## Installation
It is recommended to use a [virtual environment](https://virtualenv.pypa.io/en/stable/).

### Requirements
**System:**

* [QT5](https://www.qt.io/)

**Python:**

* dicom-numpy
* numpy
* pydicom
* pypng
* PyQt5
* toml

To aid in setup, the file `requirements.txt` is provided; use it with the command:

```bash
pip install -r requirements.txt
```

Note that you will need to install [QT5](https://www.qt.io/) first.

## Usage
### GUI
#### Drag-and-Drop interface
Simply drag-and-drop DICOM files or DICOM directories (or even folder trees)
onto the application window to convert the files to PNG.  The assumption is made that
all files will be uniquely named.

#### The "Add Files" button
Click the "Add Files" button to add DICOM files from a system dialog.  You may chose one file or multiple files.

#### The "Add Folder" button
Click the "Add folder" button to select a DICOM folder (or folder tree) to automatically (and recursively) convert all DICOM files in the folder (or tree) to PNG, and place the converted files into the output folder.

#### The "Save to..." button
Click the "Save to..." button to change the output folder location.  This is the folder where output (PNG) images are saved.  By default, it will be the "dicom_to_png" folder in your "Home" folder, but you can select any drive or folder you like with this button.

#### The "Stop" button
When you start a conversion batch, you can stop it if necessary by pressing this button.  Any files already converted before pressing "Stop" will be located in the output folder.

#### The "Exit" button
Press "Exit" to safely exit the converter application.  This button is automatically disabled when conversion work is ongoing.  If you really need to exit while conversions are incomplete, you can use the "Stop" button to stop first, then "Exit", or use the native close button in the title bar.

### CLI
CLI not implemented yet.

## Features
The DICOM image is processed by applying re-scaling as specified in the DICOM metadata, and if there is a LUT (intensity Look Up Table) present in the DICOM metadata, the (first available) LUT is applied as well.  Output is saved as greyscale PNG images in the output folder.

## Limitations
This tool works for DICOM images that contain one "slice" per file.  Multi-slice (3+ dimensional) DICOM is not supported.  All files must be uniquely named; output filenames match the DICOM file names with the addition of the ".png" extension.

## Known Issues
* In Mac OS, the "Save to..." dialog does not use the native interface.  There is an unresolved crash if the "New Folder" button in the native interface is pressed.  The non-native dialog does not have this issue.
* In Mac OS, trying to create a "New Folder" in the "Add Folder" dialog may cause a crash.

## MIT License

Copyright 2018 Jason L Causey, Arkansas State University

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.