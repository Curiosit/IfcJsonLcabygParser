# Ifcparser
IFC Parser is a Python script for automatical creating material takeoff from a properly exported IFC2X3 file, and converting that to JSON file format, to finally import into danish LCAByg program for calculating Carbon Footprint of buildings.

# Requirements
IfcOpenShell (https://github.com/IfcOpenShell/IfcOpenShell)
JSON
Pandas
Numpy
uuid

notebook.yml shows my current configuration of the python environment.

2 own libraries are being used here, both partially based on external code: 
ifcHelper.py
lcabygjson.py

# Running IfcJsonLcabygParser
ifc_to_lcabygjson.ipynb is a Jupyter notebook that imports an IFC file, reads the data of main building components (walls, slabs, roofs, etc.), saves them to a dataframe, and then generates a set of JSON files in a format readable by LCAByg 5.2 program.

# Preparing IFC file
The file needs to be exported from a BIM program (ie. Revit) with modified IFC2X3 Coordination View 2.0 settings.
It is important to select 'base quantities'
Optionally the parsing worked best with also selecting 'split walls, columns ducts by level', and 'Export Revit property sets' and 'Export IFC common property sets'.

# MVP
This is a minimum viable product, and thus has a very limited functionality, further additions to come...
Current version is able to export LCAByg Constructions ('Konstruktioner') with their quantity takeoff.

# What is LCAByg
LCAByg is a danish LCA (cabron footprint) assessment program developed by by BUILD (former Danish building research institute), Aalborg University with financial support from various actors in Denmark.

# Importing the files to LCAByg
The import follows the method from the JSON guide by LCAByg (lcabyg5_json_guide). The script creates 4 JSON files: elements.json constructions.json element_category_edges.json and constructions_extra.json that are needed to be replaced from the default import_example.


