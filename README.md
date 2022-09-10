# tex-pptx-pdf-builder

Tools to build office and tex to pdf in GitLab CI pipeline.
Github Action support is planned.

All source tex files need to be listed in `tex/Makefile`
All office files in `pptx/Makefile`. All file formats supported in libreoffice may be used.

Build files are saved as job artifacts in Gitlab and may be downloaded here:

## Download Tex

- [TEX-PDF](https://gitlab.com/<namespace>/<repository>/-/jobs/artifacts/<branch>/raw/<path>/tex/Beispiel.pdf?job=build-tex)

## Download PPTX

- [PPTX-PDF](https://gitlab.com/<namespace>/<repository>/-/jobs/artifacts/<branch>/raw/<path>/pptx/Lorem-Ipsum-1.pdf?job=convert-pptx)
- [PPTX-PDF](https://gitlab.com/<namespace>/<repository>/-/jobs/artifacts/<branch>/raw/<path>/pptx/Lorem-Ipsum-2.pdf?job=convert-pptx)

