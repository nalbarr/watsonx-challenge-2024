# Molecules

`
add molecule <name> | <smiles> | <inchi> | <inchikey> | <cid> [ as '<name>' ] [ basic ] [force ]
`

This command is how you add a molecule to a current working list of molecules in memory. When adding a molecule by name, this name will become the molecule’s identifying string.

It will take any molecules identifier from the following categories:
-smiles
-name or synonym
-smiles
-inchi
-inchikey
-cid

Options :
- as <name> : if the ` as ‘' ` not used the molecule the molecule identfier will be used for the molecules name. if the ` as '' ` not used the molecule the molecule identfier will be used for the molecules name.
You can set or override an name later for any molecule with the `rename molecule` command.
- ` basic ` Creates a molecule that does not have its properties and synonyms populated with pubchem data, this feature is only valid with a SMILES molecule identifier
- `force`: The `force` option allows you to ovveride the confirmation that you wish to add a molecule.

You can use the ‘mol’ shorthand instead of ‘molecule’.

You can specify any molecule by SMILES or InChI, and PubChem classified molecules also by name, InChIKey or their PubChem CID.
A molecule identifier can be in single quotes or defined with unquoted text. If you have spaces in your molecule identifier e.g. a name, then you must user a single quoted string

If you use the name of a molecule, the tool will do a caseless search of the names and synonyms first in current working list, then on pubchem.

Examples of how to add a molecule to your working list:

Add a molecule by name:
add molecule aspirin
or with single quotes
` display molecule ‘Aspirin 325 mg’ `

Add a molecule by name and force through the acknowledgement to add it:
add molecule aspirin force

Add a molecule by SMILES:
add molecule CC(=O)OC1=CC=CC=C1C(=O)O

Add a molecule by SMILES without populated pubchem properties:
add molecule CC(=O)OC1=CC=CC=C1C(=O)O basic

Add a molecule by CID:
add mol 2244

Add a molecule by InChI:
add mol InChI=1S/C9H8O4/c1-6(10)13-8-5-3-2-4-7(8)9(11)12/h2-5H,1H3,(H,11,12)
or with single quotes
add mol 'InChI=1S/C9H8O4/c1-6(10)13-8-5-3-2-4-7(8)9(11)12/h2-5H,1H3,(H,11,12)'

Add a molecule by InChIKey:
add mol BSYNRYMUTXBXSQ-UHFFFAOYSA-N

Add a molecule by InChIKey nd set its name to “mymol”:
add mol BSYNRYMUTXBXSQ-UHFFFAOYSA-N as 'mymol'

Add a molecule by SMILES nd set its name to “mymol” and not prepopulate values from pubchem:
add mol CC(=O)OC1=CC=CC=C1C(=O)O as 'mymol' basic


display molecule <name> | <smiles> | <inchi> | <inchikey> | <cid>
This command will display a molecule’s identifiers, propoerties, synonyms and any Analysis results it has been enriched with.
if the molecule exists in the current molecule workling list in memory the molecule will be retrieved from there if not pubchem will be checked to see if the molecule and its information is avialable there.

You can use the ‘mol’ shorthand instead of ‘molecule’.

If the requested molecule exists in your current working list, that version will be used.

You can specify any molecule by SMILES or InChI, and PubChem classified molecules also by name, InChIKey or their PubChem CID.
A molecule identifier can be in single quotes or defined with unquoted text. If you have spaces in your molecule identifier e.g. a name, then you must user a single quoted string

If you use the name of a molecule, the tool will do a caseless search of the names and synonyms first in current working list, then on pubchem.

Examples:

Display a molecule by name:
display molecule Aspirin

Display a molecule by SMILES:
display molecule CC(=O)OC1=CC=CC=C1C(=O)O

Display a molecule by InChI:
display mol InChI=1S/C9H8O4/c1-6(10)13-8-5-3-2-4-7(8)9(11)12/h2-5H,1H3,(H,11,12)

Display a molecule by InChIKey string:
display mol BSYNRYMUTXBXSQ-UHFFFAOYSA-N

Display a molecule by CID:
display mol 2244

`display sources <name> | <smiles> | <inchi> | <inchikey> | <cid>`
Display the sources of a molecule’s properties, attributing back to how they were calculated or sourced.

If the requested molecule exists in your current working list, that version will be used.

You can specify any molecule by SMILES or InChI, and PubChem classified molecules also by name, InChIKey or their PubChem CID.
A molecule identifier can be in single quotes or defined with unquoted text. If you have spaces in your molecule identifier e.g. a name, then you must user a single quoted string

If you use the name of a molecule, the tool will do a caseless search of the names and synonyms first in current working list, then on pubchem.

`rename molecule <molecule_identifer_string> as <molecule_name>`
Rename a molecule in the current working list.

{MOL_SHORTHAND}

Example:
Let’s say you’ve added a molecule “CC(=O)OC1=CC=CC=C1C(=O)O” to your current working list of molecules, you can then rename it as such:
rename molecule CC(=O)OC1=CC=CC=C1C(=O)O as Aspirin

`export molecule <name> | <smiles> | <inchi> | <inchikey> | <cid> [ as file ]`
When run inside a jupyter lab notebook, this will return a dictionary of the molecule’s properties. When run from the command line, or when as file is set, the molecule will be saved to your workspace as a JSON file, named after the molecule’s identifying string.
If the molecule is in your current working list it will be retrieved from there, if the molecule is not there pubchem will be called to retrieve the molecule.

You can use the ‘mol’ shorthand instead of ‘molecule’.

If the requested molecule exists in your current working list, that version will be used.

If you use the name of a molecule, the tool will do a caseless search of the names and synonyms first in current working list, then on pubchem.

Examples

export molecule aspirin
export molecule aspirin as file

`remove molecule <name> | <smiles> | <inchi> | <inchikey> | <cid>`
Remove a molecule from the current working list based on a given molecule identifier.

{MOL_SHORTHAND}

Examples:

Remove a molecule by name:
remove molecule Aspirin

Remove a molecule by SMILES:
remove molecule CC(=O)OC1=CC=CC=C1C(=O)O

Remove a molecule by InChIKey:
remove mol BSYNRYMUTXBXSQ-UHFFFAOYSA-N

Remove a molecule by InChI:
remove mol InChI='1S/C9H8O4/c1-6(10)13-8-5-3-2-4-7(8)9(11)12/h2-5H,1H3,(H,11,12)'

Remove a molecule by CID:
remove mol 2244

`list molecules`
List all molecules in the current working list.

`save molecule-set as <molecule_set_name>`
Save the current molecule workking list to a molecule-set in your workspace.

Example:
save molset as my_working_set

`load molecule-set|molset <molecule-set_name>`
Loads a molecule-set from your workspace, and replaces your current list of molecules with the molecules from the given molecule-set.
Example:
load molset my_working_set

`merge molecule-set|molset <molecule-set_name> [merge only] [append only]`
This command merges a molecule-set from your workspace into cour current working list of molecules in memory, and updates properties/Analysis in existing molecules or appends new molecules to the working list.

Options:
- ` merge only Only merges with existing molecules in list <br> - append only Only append molecules not in list <br> merge molset my_working_set`

`list molecule-sets`
List all molecule sets in your workspace.

`enrich molecules with analysis
This command Enriches every molecule in your current working list of molecules with the analysis results. This assumes that molecules in the current working list was the input or result for the analysis.

`clear analysis cache`
this command clears the cache of analysis results for your current workspace.

`clear molecules`
This command clears the working list of molecules.

`@(<name> | <smiles> | <inchi> | <inchikey> | <cid>)>><molecule_property_name>`
This command request the given property of a molecule, it will first try and retrieve the provided molecule from your working list of molecules, if it is not there it will will try and retrieve the molecule from pubchem.

The @ symbol should be followed by the molecule’s name, SMILES, InChI, InChIKey or CID, then after the >> include one of the properties mentioned below.

E.g. @aspirin>>xlogp

You can specify any molecule by SMILES or InChI, and PubChem classified molecules also by name, InChIKey or their PubChem CID.
A molecule identifier can be in single quotes or defined with unquoted text. If you have spaces in your molecule identifier e.g. a name, then you must user a single quoted string

If you use the name of a molecule, the tool will do a caseless search of the names and synonyms first in current working list, then on pubchem.

Examples of how to retrieve the value of a molecules property:

Obtain the molecular weight of the molecule known as Aspirin.
@aspirin>>molecular_weight

Obtain the canonical smiles string for a molecule known as Aspirin.
@aspirin>>canonical_smiles

Obtain a molecules xlogp value using a SMILES string.
@CC(=O)OC1=CC=CC=C1C(=O)O>>xlogp

Available properties: atom_stereo_count, bond_stereo_count, canonical_smiles, charge, cid, complexity, conformer_count_3d, conformer_id_3d, conformer_model_rmsd_3d, conformer_rmsd_3d, coordinate_type, covalent_unit_count, defined_atom_stereo_count, defined_bond_stereo_count, effective_rotor_count_3d, exact_mass, feature_acceptor_count_3d, feature_anion_count_3d, feature_cation_count_3d, feature_count_3d, feature_donor_count_3d, feature_hydrophobe_count_3d, feature_ring_count_3d, h_bond_acceptor_count, h_bond_donor_count, heavy_atom_count, inchi, inchikey, isomeric_smiles, isotope_atom_count, iupac_name, mmff94_energy_3d, mmff94_partial_charges_3d, molecular_formula, molecular_weight, molecular_weight_exact, monoisotopic_mass, multipoles_3d, multipoles_3d, pharmacophore_features_3d, pharmacophore_features_3d, rotatable_bond_count, sol, sol_classification, tpsa, undefined_atom_stereo_count, undefined_bond_stereo_count, volume_3d, x_steric_quadrupole_3d, xlogp, y_steric_quadrupole_3d, z_steric_quadrupole_3d

`load molecules using file '<csv_or_sdf_filename>' [ merge with pubchem ]`
This command Loads molecules from a CSV or SDF file into the molecule working list. Optionally you can add merge with pubchem to the command to fill in missing properties of the molecule.

`export molecules [ as <csv_filename> ]`
This command exports the molecules in the current working list of molecules.

When run inside a Notebook, this will return a dataframe. When run from the command line, the molecules will be saved to your workspace as a CSV file named “result_#.csv”. The rows will be numbered with the highest number representing the latest molecule that was added.

`show molecule <name> | <smiles> | <inchi> | <inchikey> | <cid>`
Inspect a molecule in the browser.

{MOL_SHORTHAND}

When you show a molecule by SMILES or InChI, we can display it immediately. When you show a molecule by name, InChIKey or PubChem CID, we need to first retrieve it from PubChem, which can take a few seconds.

Examples of how to show a molecule and its proerties in the molecule viewer:

show mol aspirin
show mol CC(=O)OC1=CC=CC=C1C(=O)O
show mol InChI=1S/C9H8O4/c1-6(10)13-8-5-3-2-4-7(8)9(11)12/h2-5H,1H3,(H,11,12)
show mol 2244

`show molecules using ( file '<mols_file>' | dataframe <dataframe> ) [ save as '<sdf_or_csv_file>' | as molsobject ]`
Launch the molecule viewer to examine and select molecules from a SMILES sdf/csv dataset.

## Utility
`load molecules using dataframe <dataframe> [ merge with pubchem ]`
This command Load molecules into the molecule working list from a dataframe.

If the ` merge with pubchem` clause is used then loaded molecules will have properties that are not in the source file filled in using pubchem requests, this will slow the process down

`merge molecules data using dataframe <dataframe> [ merge with pubchem ]`
This command merges molecules into the molecule working list from a dataframe.

`display data '<filename.csv>'`
Display data from a csv file.

`-> result save [as '<filename.csv>']`
Save table data to csv file.

`-> result open`
Explore table data in the browser.

`-> result edit`
Edit table data in the browser.

`-> result copy`
Copy table data to clipboard, formatted for spreadheet.

`-> result display`
Display the result in the CLI.

`-> result as dataframe`
Return the result as dataframe (only for Jupyter Notebook)

`edit config '<json_config_file>' [ schema '<schema_file>']`
Edit any JSON file in your workspace directly from the CLI. If a schema is specified, it will be used for validation and documentation.
