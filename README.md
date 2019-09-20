### textract
---
https://github.com/deanmalmgren/textract

```py
// tests/test_pdf.py
import unittest
import os
import six

from . import base

class PdfTestCase(base.ShellParserTestCase, unittest.TestCase):
  extension = 'pdf'
  
  def test_pdfminer_python(self):
    self.compare_python_output(self.raw_text_filename, method='pdfminer')
  
  def test_pdfminer_cli(self):
    self.compare_cli_output(self.raw_text_filename, method='pdfminer')
  
  def test_tessearact_cli(self):
    d = self.get_extension_directory()
    self.compare_cli_output(
      os.path.join(d, "ocr_text.pdf"),
      expected_filename=os.path.join(d, "ocr_text.txt"),
      method='tesseract',
    )
  
  def test_large_pdf(self):
    filename = os.path.join(self.get_extension_directory(), "large.pdf")
    self.download_file(
      "https://openknowledge.worldbank.org/bitstream/handle/10986/16091/9780821399378.pdf",
      filename
    )
  
  def test_two_column(self):
    filename = os.path.join(self.get_extension_directory(), 'two_column.pdf')
    self.compare_python_output(filename, layout=True)
```

```
```

```
```

