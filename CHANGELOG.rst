#########
Changelog
#########


v0.6dev
=======

Breaking changes
================

* New implementation of the characterize function of the extension object.
  The new method generalizes the previous method for region/sector specific characterizations.
  It is tightly coupled to the general characterize function which allows characterization accross
  different extensions (see point under New features).

* get_extensions has a new signature. 
  Two new paramters, names and istance_names.

    - 'names' allows to filter the extensions by name (set names of the attribute .name
        or the instance names, also allows to pass the extension itself). Can be used
        to harmonize the names of an extension list.
    - 'instance_names' can be set to False to get the "set names" of the extensions.

  When using keyword arguments before, the new signature should just work.

* remove_extension: 
  Previous all extensions got removed when no name was given.
  This has changed. Now all extensions are kept when no name is given (TypeError is raised).
  To remove all extensions, use mrio.remove_extension(mrio.get_extensions())

* concate_extension renamed to extension_concate to make it consistent with extension_convert and _characterize

* concate_extension argument "name" renamed to "new_extension_name"

* minimal python version pushed to 3.9, pandas version pushed to 2.1

New features
============

* New top-level characterize function

* Extension concatenation function also available as method of an mrio object.

* added functionality to download and parse 2023 release of OECD IO tables (by @jaimeoliver1, #132)

* Added draft Gosh implementation for downstream analysis (by @Beckebanze , #136)

    - equivalent of A for Ghosh (A* in literature, called As in pymrio)
    - the Ghosh inverse (often referred to G in literature). 
    - downstream scope 3 multiplier, M_{down}, such the sum of the M+M_{down} is the full scope multiplier, with M the existing multiplier in pymrio that covers scope 1,2&3 upstream.
    - a short addition to the pymrio background page that introduces the Ghosh model
    - tests that test the functionality of the added functions



Depracted
=========

* extension.get_row_data()
  The method get_row_data() is deprecated and will be removed in v0.6.0. 
  Use extension.extract() instead.


Misceallaneous
==============

* Updated and restructuring of the documentation
* Fixed multiple warnings due to deprecation in pandas
* Version definition now in pyproject.toml, version attribute set in script

***************************
v0.5.4 - 20240412
***************************

New features
============

* added functionality to download and parse 2023 release of OECD IO tables (by @jaimeoliver1, #132)

* Added draft Gosh implementation for downstream analysis (by @Beckebanze , #136)

    - equivalent of A for Ghosh (A* in literature, called As in pymrio)
    - the Ghosh inverse (often referred to G in literature). 
    - downstream scope 3 multiplier, M_{down}, such the sum of the M+M_{down} is the full scope multiplier, with M the existing multiplier in pymrio that covers scope 1,2&3 upstream.
    - a short addition to the pymrio background page that introduces the Ghosh model
    - tests that test the functionality of the added functions

***************************
v0.5.3 - 20231023
***************************

Bugfixes
========

* Fix downloader for new Zenodo API (by @hazimhussein)
* Fix coverage report (by @konstantinstadler)

***************************
v0.5.2 - 20230815
***************************

New features
============

* OECD bundle download (by @hazimhussein) - see https://pymrio.readthedocs.io/en/latest/notebooks/autodownload.html#OECD-download
* Fix EORA26 parsing (by @hazimhussein)

Development
===========

* Switched to Micromamba in the CI 
* Fixed readthedocs settings


***************************
v0.5.1 - 20230615
***************************

* small bugfix with version numbering

***************************
v0.5.0 - 20230615
***************************

Development
===========

* Move the repository to the public IndEcol organization on GitHub: https://github.com/IndEcol/pymrio

Breaking changes
================

* dropped support for Python 3.7 and added 3.10 and 3.11
* License changed to LESSER GNU GENERAL PUBLIC LICENSE v3 (LGPLv3)
* added pyarrow as requirment

New features
============

* Autodownloader for GLORIA MRIO (by @hazimhussein)
* Support of parquet format for load and save function 


Bugfixes
============

* Fix Eora downloader (by @hazimhussein)

***************************
v0.4.8 - 20221116
***************************

* Added inbuild classification for 
  - Test MRIO
  - EXIOBASE 2 
  - EXIOBASE 3

* Method for renaming sectors/regions based on the built in classification
* Method for aggregating duplicated indexes

Bugfixes
========

* F_Y was removed in reset_full - fixed
* updated deprecated pandas methods - fix #93

***************************
v0.4.7 - 20220428
***************************

* Fixed OECD downloader and parser (by @jaimeoliver1)

***************************
v0.4.6 - 20211118
***************************

* Fixed indexing bug in calc_accounts for non-full Y 
* Added Stadler 2021 reference
* change github actions testing to development -> production for multiple os

Breaking changes
================

* dropped support for Python 3.6

***************************
v0.4.5 (March 03, 2021) 
***************************

Bugfixes
========

* Index sorting consistent for all characterized impacts 


***************************
v0.4.4 (February 26, 2021) 
***************************

Bugfixes
========

* Characterization for cases when some stressors are missing from the characterization matrix
* Spelling mistakes
* Fixed installation description in readme and documentation

***************************
v0.4.3 (February 24, 2021) 
***************************

New features
============

* Added automatic downloader for EXIOBASE 3 files
* Method for characterizing stressors (pymrio.Extension.characterize)

Bugfixes
========

* Fixed: xlrd and numpy requirments for later pandas versions

Development
===========

* Switched from travis to github actions for testing and converage reports

***************************
v0.4.2 (November 19, 2020)
***************************


Bugfixes
========

* Fixed: OECD parsing bug caused by pandas update
* Fixed: Missing inclusion of auxiliary data for exiobase 2
* Fixed: Making python version explicit and update package requirements
* Fixed: hard-coded OS specific path

Development
===========

* switched to black code style
* updated travis.yml for testing different python versions
* added github workflows for automated releases
* switched to git trunk based development


***************************
v0.4.1 (October 08, 2019)
***************************

Bugfixes
========

* Fixed: Parsing EXIOBASE 3 from zip on Windows system
* Fixed: Doc spelling

New features
============

* The tutorial notebooks of the documentation are now also used for integration 
  tests. See CONTIBUTING.rst for more infos.

***************************
v0.4.0 (August 12, 2019)
***************************

New features
============

* New parser and automatic downloader for the OECD-ICIO tables (2016 and 2018 
  release)
* Improved test coverage to over 90 %
* Equality comparison for MRIO System and Extension


Bugfixes
========

* Fixed some typos

Backward incompatible changes
==============================

* Minimum python version changed to 3.7
* The FY and SY matrixes has been renamed to F_Y and S_Y. Previously stored 
  data, however, can still be read (FY/SY files are automatically parsed as F_Y 
  and S_Y)

***************************
v0.3.8 (November 06, 2018)
***************************

Hotfix for two EXIOBASE 3 issues

* FY in the raw files is named F_hh. F_hh now get automatically renamed to FY.
* In the ixi tables of EXIOBASE 3 some tables had ISO3 country names. The parser now renames these names to the standard ISO2. 

*************************
v0.3.7 (October 10, 2018)
*************************

New features
============

* pymrio.parse_exiobase3, accepting the compressed archive files and extraced data (solves #26)
* pymrio.archive for archiving MRIO databases into zipfiles (solves #26)
* pymrio.load and pymrio.load_all can read data directly from a zipfile (solves #26)

Bugfixes
========

* Calculate FY and SY when final demand impacts are available (fixes issue #28) 
* Ensures that mrio.x is a pandas DataFrame (fixes issue #24)
* Some warning if a reset method would remove data beyond recovery by calc_all (see issue #23 discussion)

  
Removed functionality
=====================

* Removed the Eora26 autodownloader b/c worldmrio.com needs a registration now (short time fix for #34)
  
Misc
====

* pymrio now depends on python > 3.6
* Stressed the issue driven development in CONTRIBUTING.rst


***********************
v0.3.6 (March 12, 2018)
***********************

Function get_index now has a switch to return dict
for direct input into pandas groupby function.

Included function to set index across dataframes.

Docs includes examples how to use pymrio with pandas groupby.

Improved test coverage.


**********************
v0.3.5 (Jan 17, 2018)
**********************

Added xlrd to requirements

**********************
v0.3.4 (Jan 12, 2018)
**********************

API breaking changes  
=====================

- Footprints and territorial accounts were renamed to "consumption based accounts" and "production based accounts": D_fp was renamed to D_cba and D_terr to D_pba 

**********************
v0.3.3 (Jan 11, 2018)
**********************

Note: This includes all changes from 0.3 to 0.3.3

- downloaders for EORA26 and WIOD
- codebase fully pep8 compliant
- restructured and extended the documentation
  
- License changed to GNU GENERAL PUBLIC LICENSE v3
  
Dependencies
============

- pandas minimal version changed to 0.22
- Optional (for aggregation): country converter coco >= 0.6.3

API breaking changes  
=====================

- The format for saving MRIOs changed from csv + ini to csv + json. Use the method '_load_all_ini_based_io' to read a previously saved MRIO and than save it again to convert to the new save format.
- method set_sectors(), set_regions() and set_Y_categories() renamed to rename_sectors() etc.
- connected the aggregation function to the country_converter coco
- removed previously deprecated method 'per_source'. Use 'diag_stressor' instead.


**********************
v0.2.2 (May 27, 2016)
**********************

Dependencies
============

- pytest. For the unit tests.

Misc
====

- Fixed filename error for the test system.
- Various small bug fixes.
- Preliminary EXIOBASE 3 parser.
- Preliminary World Input-Output Database (WIOD) parser.

**********************
v0.2.1 (Nov 17, 2014)
**********************

Dependencies
============

- pandas version > 0.15. This required some change in the xls reading within
  the parser.
- pytest. For the unit tests.

Misc
====

- Unit testing for all mathematical functions and a first system wide check.
- Fixed some mistakes in the tutorials and readme

**********************
v0.2.0 (Sept 11, 2014)
**********************

API changes
===========

- IOSystem.reset() replaced by IOSystem.reset_all_to_flows()
- IOSystem.reset_to_flows() and IOSystem.reset_to_coefficients() added
- Version number attribute added
- Parser for EXIOBASE like extensions (pymrio.parse_exio_ext) added.
- plot_accounts now works also for for specific products (with parameter "sector")

Misc
====

- Several bugfixes
- Mainmodule split into several packages and submodules
- Added 3rd tutorial
- Added CHANGELOG

**********************
v0.1.0 (June 20, 2014)
**********************

Initial version
