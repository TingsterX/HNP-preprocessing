## Nonhuman Primate (NHP) f/MRI data preprocessing

This repo contains NHP data preprocessing documents,and example codes. Unlike human data, NHP data preprocessing could be challenging, since most of the imaging tools are originally developed for human data. Besides specific parameters setting, there are several issues may only happen for NHP data. At the current stage, it is difficult to have an easy, end-to-end pipeline works well for all NHP f/MRI data, in particular for data from multiple sites (differnt scanner, coils, acquisition protocols, data quality, etc.). 


```
----------------------------------------------------------------------
|   _/.-.-.\_                                                        |
|  ( ( o o ) )                                                       |
|   |/  "  \|                                                        |
|    \ \-/ /   This repo is not a tutorials and it won't walk        |
|    /`"""`\   through every little details of the tools. Instead,   |
|   /       \  it provides examples of lessons learned from mistakes,|
| tricks, clues to debug or tweak the pipeline for NHP data.         |
|                                                                    |
----------------------------------------------------------------------
```

----

### Requirement
- [FreeSurfer](https://surfer.nmr.mgh.harvard.edu/)
- [FSL](https://fsl.fmrib.ox.ac.uk/fsl/fslwiki/)
- [afni](https://afni.nimh.nih.gov/)
- [ANTs](https://stnava.github.io/ANTs/)
- [SPM](https://www.fil.ion.ucl.ac.uk/spm/) (Matlab required)
- [Connectome Workbench](https://www.humanconnectome.org/software/connectome-workbench)
- [ITK-SNAP](http://www.itksnap.org/pmwiki/pmwiki.php)

----

### Macaque Templates 
- **F99**
    - **Keywords**: Classic standard template
    - Format/tools: Caret 
    - The 'first generation' of macaque surface template. Multiple parcellation maps have converted to this space. 
    - Ref: [Van Essen et al., 2012](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3500860/)

- **Yerkes19**
    - **Keywords**: HCP-style
    - Format/tools: NIFTI/GIFTI, workbench
    - The 'second generation' of F99, HCP-style macaque template including brain mask, volume segmentation in FreeSurfer format, symmetric surface meshes (164k_fs_LR, 32k_fs_LR, 10k_fs_LR), morphometric maps (T1w/T2w, ) etc.
    - [HCP-style Macaque Pipeline](https://github.com/Washington-University/NHPPipelines/tree/master/global/templates)
    - [Yerkes19 Atlas on BALSA](https://balsa.wustl.edu/reference/show/976nz) 
    - Ref: [Donahue et al., 2016](https://pubmed.ncbi.nlm.nih.gov/27335406/), [Autio et al., 2019 biorxiv](https://www.biorxiv.org/content/10.1101/602979v1)

- **NMT**
    - **Keywords**: High quality, high resolution
    - Format/tools: NIFTI/GIFTI, afni
    - Macaque template generated from 31 high quality data in 0.25 mm resolution, including brain mask, segmentation, surface and morphometric maps (e.g. thickness). 
    - [NMT Pipeline](https://github.com/jms290/NMT)
    - Ref: [Seidlitz et al., 2017] (https://pubmed.ncbi.nlm.nih.gov/28461058/)

- **D99**
    - **Keywords**:  3D Digital template from [Saleem adn Logothetis atlas](https://books.google.com/books?hl=en&lr=&id=tuVyU2-s8MUC&oi=fnd&pg=PP2&ots=yGMq0Lsf48&sig=aA-yVeh01CfKVmD6LCLWtyFLiQ0). (A 'Talairach-like' macaque template for afni fans)
    - Format/tools: GIFTI, afni & suma
    - Ref: [Reveley et al., 2017](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6075609/)

----

### Resources
- Data: [The PRIMatE Data Exchange - PRIME-DE](http://fcon_1000.projects.nitrc.org/indi/PRIME)

- Parcellation: 
    - [Markov et al., 2011](https://pubmed.ncbi.nlm.nih.gov/21045004/), [2014](https://pubmed.ncbi.nlm.nih.gov/23010748/)
        - Markov parcellation (Yerkes19 space) [Donahue et al., 2016](https://pubmed.ncbi.nlm.nih.gov/27335406/)
    - [CoCoMac](http://cocomac.g-node.org/main/index.php) 
    - [SBA - Scale Brain Atlas](https://scalablebrainatlas.incf.org/index.php)
    - LV00 - [Lewis and Van Essen, 2000](https://pubmed.ncbi.nlm.nih.gov/11058227/)
    - FV91 - [Felleman and Van Essen, 1991](https://pubmed.ncbi.nlm.nih.gov/1822724/)
    - B05 - Brodmann, 1905
    - BB47 - von Bonin and Bailey 1947
    - PHT00 - Paxinos et al., 2000
    - FOAP00 - Ferry et al., 2000
    - PG91 - Preuss and Goldman-Rakic 1991
    - UD86 - Ungerleider and Desimone, 1986; Ungerleider and Desimone, 1986
    - Bezgin et al., 2008
    - Ref: [Bezgin et al., 2012](https://pubmed.ncbi.nlm.nih.gov/22521477/) 

- Reference: [Van Essen et al., 2019](https://www.pnas.org/content/116/52/26173), 

----
## [Welcome to the monkey world](issues_and_fix.md)
```
Pop quiz: Which one is a gibbon and which one is a macaque？

     |  c(..)o    @(..)D  
      \__(-)        (-)__/
          /\  (      /\
       __/(_)__)    (_)\_
```
### [Issues](issues_and_fix.md)
- A first galance
    - Size
    - Male versus Female 
    - Open scalp
- Orientation
- Denoise
- Crop and ACPC alignment
- Brain extraction (skull stripping)
- Intensity correction
- Segmentation
- Surface reconstruction 
- *ex vivo* image and fake T1 image
- Contrast agent for fMRI data
- Distortion
- Ghost effect

