# Youth-Nex-Capstone Citation Pipeline
A data pipeline for extracting, normalizing, deduplicating, and reporting bibliographic citations from YouthNex annual appendix documents.

---

## Overview
This project automates the process of extracting citation data from yearly appendix documents (PDF, DOC, DOCX, etc.), deduplicating references across years, and generating clean bibliographic outputs for reporting and analysis.

**Pipeline flow:**
```mermaid
flowchart LR

A["<b>Raw Documents</b><br/>(PDF, DOC, DOCX)"] ==> B["<b>Text Extraction</b><br/>(multi-format parsing)"]

B ==> C["<b>Preliminary EDA</b><br/>(assess document &<br/>formatting variability)"]

C ==> D["<b>Citation Extraction</b><br/>(split into individual<br/>references)"]
D ==> N["<b>Normalization</b><br/>(standardize formatting)"]

%% Parallel development track
C ==> E["<b>Deduplication Pipeline</b><br/>(prototype on subset data)"]
E ==> F["<b>Similarity & Rule-Based<br/>Deduplication</b><br/>(refinement on sample set)"]

%% Integration step
N ==> G["<b>Standardized Citation Dataset</b>"]
F ==> G

G ==> H["<b>Integrated Pipeline</b>"]

H ==> I["<b>Final Outputs</b><br/>(deduplicated bibliography,<br/>metrics, reporting)"]
```
---

## Repository Structure


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
 
