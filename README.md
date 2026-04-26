# Youth-Nex-Capstone
This repository will be the home for all necessary code for our capstone project.


Data Input Requirements 

 

Directory Organization 
- The base directory (`BASE`) must contain year-level subfolders: 
`BASE/ 
    2020/ 
    2021/ 
    2022/ 
    2023/ 
    2024/ 
    2025/` 
- Each year folder is processed independently. 

Appendix Folder Identification 
- Within each year folder, the pipeline searches recursively for subdirectories containing the keyword: `appendices` 
- Matching is:  
    - case-insensitive  
    - based on partial string match (e.g., `Appendices`, `appendices_final`, etc.) 

Target File Selection 
- Within identified appendix folders, files are selected if their filenames contain:  
    - `"final"` OR  
    - `" lb"` (note: includes a leading space before "lb")  
- Matching is:  
    - case-insensitive
    - applied to the full filename
 
