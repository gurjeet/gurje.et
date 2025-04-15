This directory contains the various versions of my resume created over the
years.

The primary editable file is GurjeetResume.odt. The seondary, 2-page resume,
Gurjeet_Singh_Resume.docx and the corresponding PDF file are for places and
people that insist shorter, official-looking resumes.

To update the primary resume, edit the GurjeetResume.odt file using LibreOffice,
and then generate a PDF file using LibreOffice's 'Export as PDF' feature, or the
CLI example shown in the next paragraph.

After updating the .odt copy, use the following command to generate the PDF copy
of the resume; `soffice` command can be found in the LibreOffice distribution.

    soffice --convert-to pdf GurjeetResume.odt

If needed, split the PDF file to share smaller version of the resume. Use the
`pdfseparate`, and its counterpart `pdfunite`, to create the smaller file.
These utilities can be installed using the `poppler` package.

    TMP_STR=$(date +resume-split-%Y%m%d%H%M%S) # Deliberately not using mktemp
    pdfseparate -f 1 -l 5 GurjeetResume.pdf "$TMPDIR/$TMP_STR.%d.pdf"
    pdfunite "$TMPDIR/$TMP_STR."{1,2,3,4,5}.pdf GurjeetResume-short.pdf

If you install `odt2txt`, then you can use the `git diff` command to see the edits
made in the resume ODT file. Just add the following section to `~/.gitconfig`.

```
[diff "odf"]
        binary = true
        textconv = odt2txt
```
