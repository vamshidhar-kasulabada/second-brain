## convert to pdf


```
soffice --headless --convert-to pdf "yourfile.pptx" --outdir /path/to/output/directory
```
- `--headless`: Runs LibreOffice without the GUI.
- `--convert-to pdf`: Specifies the output format (PDF in this case).
- `"yourfile.pptx"`: Replace with the path to your .pptx or .docx or .doc file.
- `--outdir /path/to/output/directory`: Sets the output directory for the PDF.

> we cannot specify the output file name. The output file name will be same as inputfile. `--outdir` is used to only specify the output directory

## adding multiple files in input

```
soffice --headless --convert-to pdf "*.pptx" --outdir /path/to/output/directory
```
or
```
soffice --headless --convert-to pdf "file1.pptx" "file2.pptx" "file3.pptx" --outdir /path/to/output/directory
```
