# NFI Downloader – Example Output Data

This repository contains example data generated with [**NFI Downloader**](https://descargaifn.gsic.uva.es/) for the
running example presented in the associated manuscript.

The aim of this repository is to:
- Illustrate the structure and content of the data exported by the application
- Clarify the differences between GeoJSON and tabular outputs
- Support transparency, reproducibility, and data reuse

The data was retrieved from [the **Semantic Forest** dataset](https://semanticforest.gsic.uva.es/sparql) and corresponds to
the **Spanish National Forest Inventory (SNFI)**. The plot selection is available [here](<https://descargaifn.gsic.uva.es/app?loc=41.509349,-4.563446,11z&ifn=ifn3&mapType=default&mapDetails=munis&txand=true&sp=(%27UXCL%2FL40MVXCI%2FI47-122MpolisR%5B%5BK413129767937704G6904067951254N42755021208715G788597102742643D537143745168024G8497085529379N60137288164547G7288589435629N51143421210339G659507747273893)%5D%5DTP2J*E2W*E2F~P3J*E3W*E3F)*AkosHmedio-aAhttps%3A%2F%2Fdatos.iepnb.es%2FB%2Ftaxon%2FSpecies2CrecursoHterritoriQD)%2CKEmbiente%2FPFB6%27TtxfiltO)~manualO)~bloqO))G~lng!-4.H%2Fsector-publicQIVcipalityJO%27txR%27K(%27lat!41.LUinceM!true)~N556DO!(PifnQo%2FR!%5BT%5D~UprovVmuniWB3%27~XsO%27A%01XWVUTRQPONMLKJIHGFEDCBA*_>).

---

## Repository contents

### Data files

- `geojson/`  
  Spatial outputs in GeoJSON format. Plot features include geometry and embedded
  species summaries.

- `csv/`  
   Flat tabular outputs suitable for statistical analysis and custom workflows.

- `excel/`  
  A single Excel workbook (`downloadNFI.xlsx`) containing one sheet per dataset,
  corresponding to the CSV files.


### Documentation

- **METADATA.md**  
  A comprehensive metadata file describing:
  - All plot‑, species‑, and tree‑level fields
  - Units and meanings of each variable
  - Differences between GeoJSON and CSV/Excel representations
  - Identifier usage and linking across datasets

Users are strongly encouraged to consult **METADATA.md** before using the data.

---

## Output formats

### GeoJSON
- `plots_ifn2.geojson`  
  Point features representing plots in SNFIv2.  
  
- `trees_ifn2.geojson`  
  Point features representing individual trees measured in SNFIv2.
- `plots_ifn3.geojson`  
  Point features representing plots in SNFIv3. 

- `trees_ifn3.geojson`  
  Point features representing individual trees measured in SNFIv3.

### CSV
- `plots_ifn2.csv`: Plot-level attributes (SNFIv2)
- `plots_infoSpecies_ifn2.csv`: Species-level summaries per plot (SNFIv2)
- `trees_ifn2.csv`: Tree-level measurements (SNFIv2) 
- `plots_ifn3.csv`: Plot-level attributes (SNFIv3)
- `plots_infoSpecies_ifn3.csv`: Species-level summaries per plot (SNFIv3)
- `trees_ifn3.csv`: Tree-level measurements (SNFIv3) 

### Excel
- `downloadNFI.xlsx`  
  Contains the same datasets as the CSV files, organized into separate sheets.

---

## Important note on species information

Species‑per‑plot information is represented differently depending on the format:

- **GeoJSON**
  Species data are embedded within each plot feature as a nested list
  (`infoSpecies`), reflecting a hierarchical structure.

- **CSV and Excel**
  The same information is provided as **separate tables**
  (`plots_infoSpecies_ifn2.csv` or `plots_infoSpecies_ifn3.csv`), with one row per plot–species combination.

This difference is fully documented in **METADATA.md**.

---

## Intended use

These files are provided as **example outputs** to illustrate the structure and
content of data that can be downloaded with NFI Downloader. They are intended
for:

- Understanding the application’s outputs
- Testing analytical workflows
- Reproducing the running example shown in the manuscript

They are not intended to replace official bulk SNFI data deliveries.

---

## Reference

These example data accompany a manuscript under review that describes the
NFI Downloader application and its use of the Semantic Forest dataset.

A formal citation will be added here if the paper is accepted.
