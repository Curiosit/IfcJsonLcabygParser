# IfcJsonLcabygParser
IfcJsonLcabygParser is a Python script for automatical creating material takeoff from a properly exported IFC2X3 file, and converting that to JSON file format, to finally import into danish LCAByg program for calculating Carbon Footprint of buildings.

# Requirements
- IfcOpenShell (https://github.com/IfcOpenShell/IfcOpenShell)
- JSON
- Pandas
- Numpy
- uuid

notebook.yml shows my current working configuration of the python environment with package versions.

2 own libraries are being used here, both partially based on external code: 
ifcHelper.py
lcabygjson.py


# Running IfcJsonLcabygParser
ifc_to_lcabygjson.ipynb is a Jupyter notebook that imports an IFC file, reads the data of main building components (walls, slabs, roofs, etc.), saves them to a dataframe, and then generates a set of JSON files in a format readable by LCAByg 5.2 program.

![ifcexport](https://user-images.githubusercontent.com/17218693/194769242-5da42ba1-b231-4419-93b4-5e234920e6af.JPG)

# Preparing IFC file
The file needs to be exported from a BIM program (ie. Revit) with modified IFC2X3 Coordination View 2.0 settings.
It is important to select 'base quantities'
Optionally the parsing worked best with also selecting 'Export Revit property sets' and 'Export IFC common property sets'.

# MVP
This is a minimum viable product, and thus has a very limited functionality, further additions to come...
Current version is able to export LCAByg Constructions ('Konstruktioner') with their quantity takeoff.

# What is LCAByg
LCAByg is a danish LCA (carbon footprint) assessment program developed by by BUILD (former Danish building research institute), Aalborg University

# Importing the files to LCAByg
The import follows the method from the JSON guide by LCAByg team (lcabyg5_json_guide). The script creates 4 JSON files: elements.json constructions.json element_category_edges.json and constructions_extra.json that are needed to be replaced from the default import_example.
You need to setup engine.yaml file in your main LCAByg folder. The path to "IfcJsonLcabygParser" should be set to lcabyg_json folder


# Important sources:
- https://github.com/johannesmichael/ifc-python/blob/master/modules/ifc_pset_utils.py
- https://thinkmoult.com/using-ifcopenshell-parse-ifc-files-python.html
- https://github.com/johannesmichael/ifc-python/blob/master/modules/ifc_pset_utils.py
- https://www.kaggle.com/code/ponybiam/introduction-to-ifcopenshell-functions/notebook
- https://blenderbim.org/docs-python/ifcopenshell-python/hello_world.html


