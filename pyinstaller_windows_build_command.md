# Command to build standalone executable for Windows
Note: This requires [PyInstaller](https://www.pyinstaller.org/) to be installed in addition to the requirements in `requirements.txt`.

```bash
pyinstaller --clean --hidden-import PyQt5.sip dicom_to_png.py
```

(Tested on Windows 10.)
