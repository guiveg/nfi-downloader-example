# Metadata for NFI Downloader

## Overview of output formats

NFI Downloader provides data in three formats:

- **GeoJSON**: spatial, hierarchical format
- **CSV**: flat tabular format
- **Excel (XLSX)**: same tables as CSV, organized into sheets

A key difference between formats concerns how species information is represented:

- In **GeoJSON**, species information is **embedded within each plot**
- In **CSV and Excel**, species information is provided as a **separate table**

---

## Plot-level data (`plots_ifn2` or `plots_ifn3`)

Each record represents one inventory plot.


### Fields

- **plotId**  
  Unique identifier of the plot within the inventory.

- **ifn**  
  Inventory edition (e.g. `ifn3`).

- **province**  
  Spanish province where the plot is located.

- **municipality**  
  Municipality where the plot is located.
  
- **latWGS84** (CSV or Excel)
  Latitude of the plot in WGS84.
  
- **lngWGS84** (CSV or Excel)
  Longitude of the plot in WGS84.
  
- **geometry** (GeoJSON only)  
  Spatial location of the plot as a Point geometry, with coordinates
  `[longitude, latitude]` in WGS84.

- **dataCapture**  
  Date when the plot was measured.

- **plotifn2Id**  
  Identifier of the corresponding plot in SNFI2, when available.
  
- **plotifn3Id**  
  Identifier of the corresponding plot in SNFI3, when available.
  
- **plotIri**  
  Persistent IRI identifying the plot.

- **plotifn2Iri**  
  Persistent IRI of the corresponding SNFI2 plot, when available.
  
- **plotifn3Iri**  
  Persistent IRI of the corresponding SNFI3 plot, when available.
    
---

## Species-per-plot data (`infoSpecies`)

Each record represents the contribution of one tree species to one plot.

### Representation by format

- **GeoJSON**:  
  Species data appear as a nested list (`infoSpecies`) inside each plot feature.

- **CSV / Excel**:  
  Species data are provided in `plots_infoSpecies_ifn2.csv` or `plots_infoSpecies_ifn3.csv` (and the
  corresponding Excel sheet), with one row per plot–species combination.

### Fields

- **infoSpeciesId**  
  Unique identifier of the plot–species record.
  
- **ifn**  
  Inventory edition (e.g. `ifn3`).

- **plotId**  
  Identifier of the plot.
  
- **province**  
  Spanish province where the plot is located.

- **municipality**  
  Municipality where the plot is located.

- **speciesId**  
  Species identifier used in the inventory.

- **scientificName**  
  Scientific name of the species.

- **percentageOfSpecies**  
  Percentage contribution of the species within the plot.

- **numberTreesHa**  
  Number of trees per hectare for the species in the plot.

- **basalAreaM2Ha**  
  Basal area in square metres per hectare for the species in the plot.

- **volumeOverBarkM3Ha**  
  Volume over bark (m³/ha) for the species in the plot.

- **volumeUnderBarkM3Ha**  
  Volume under bark (m³/ha) for the species in the plot.

- **ageInYears**  
  Estimated age of the trees for the species in the plot, if available.

- **infoSpeciesIri**  
  Persistent IRI identifying the plot–species record.

- **plotIri**  
  Persistent IRI identifying the plot.

- **speciesIri**  
  Persistent IRI identifying the species.

---

## Tree-level data (`trees_ifn2` or `trees_ifn3`)

Each record represents an individual tree measured in the inventory.

### Fields

- **treeId**  
  Identifier of the tree.

- **ifn**  
  Inventory edition.

- **plotId**  
  Identifier of the plot where the tree is located.

- **province**  
  Province where the plot is located.

- **municipality**  
  Municipality where the plot is located.
  
- **latWGS84** (CSV or Excel)
  Latitude of the tree in WGS84.
  
- **lngWGS84** (CSV or Excel)
  Longitude of the tree in WGS84.
  
- **geometry** (GeoJSON only)  
  Spatial location of the tree as a Point geometry, with coordinates
  `[longitude, latitude]` in WGS84.

- **dbh1mm**, **dbh2mm**  
  Diameter at breast height measurements (millimetres).

- **heightM**  
  Total tree height (metres).

- **quality**  
  Tree quality class:
	- **Quality 1**: Healthy, vigorous, well-formed tree with no signs of aging; excellent future prospects and high-value production potential.
	- **Quality 2**: Healthy and vigorous, not dominated, with minor form defects; capable of producing several valuable products.
	- **Quality 3**: Moderately healthy or somewhat old/dominated; notable form defects but still yields some valuable products.
	- **Quality 4**: Weak, diseased, or old tree with many defects; only suitable for low-value products.
	- **Quality 5**: Very weak, diseased, or old, with poor form; very limited and low-value yields.
	- **Quality 6**: Dead tree (not yet decayed); may still provide some usable material.

- **expan**  
  Expansion factor used to scale individual trees to per-hectare values.

- **speciesId**  
  Species identifier.

- **scientificName**  
  Scientific name of the species.
  
- **dataCapture**  
  Date when the plot was measured.

- **treeifn2Id**  
  Identifier of the corresponding tree in SNFI2, when available.
  
- **treeifn3Id**  
  Identifier of the corresponding tree in SNFI3, when available.

- **treeIri**  
  Persistent IRI identifying the tree.
  
- **plotIri**  
  Persistent IRI identifying the plot.
  
- **speciesIri**  
  Persistent IRI identifying the species.

- **treeifn2Iri**  
  Persistent IRI of the corresponding SNFI2 tree, when available.
  
- **treeifn3Iri**  
  Persistent IRI of the corresponding SNFI3 tree, when available.
  
---

## Notes on identifiers and linking

- All plots, trees, species, and plot–species records are identified by
  persistent IRIs.
- These identifiers enable linking across inventory editions and integration
  with external data sources.
- The same identifiers appear consistently across GeoJSON, CSV, and Excel
  outputs.

---

## Intended use

NFI Downloader aims to facilitate the visualization, filtering, and downloading of SNFI data
in an integrated way. 

For full inventory documentation and official definitions, users should refer to
the original SNFI technical manuals.
