SilverGraph
===========

Creates data model visualisations of SilverStripe DataObjects, showing fields, relations and ancestry.
Can output images in .png, .svg and raw GraphViz "dot" format.
Flexible configuration options and can be called from command line and URL.

##Installation##
* Manual: Download and extract the silvergraph folder into the top level of your site, and visit /dev/build?flush=all to rebuild the database.
* Composer/Packagist: Install composer and then run `composer require froog/silvergraph dev-master`

##Requirements##
 * SilverStripe 3.0.0+
 * To create images: GraphViz (latest version) http://www.graphviz.org/
 	To install (Debian/Ubuntu): `apt-get install graphviz`

##Usage##

###Command line###

Default png image:   `sake Silvergraph/png > datamodel.png`
Parameter example:   `sake Silvergraph/png location=mysite,cms inherited=1 exclude=SiteTree > datamodel.png`
Default dot file:    `sake Silvergraph/dot > datamodel.dot`

###Browser: (logged in as admin)###

http://mysite.com/Silvergraph/png
http://mysite.com/Silvergraph/png?location=mysite,cms&inherited=1&exclude=SiteTree
http://mysite.com/Silvergraph/dot

###Parameters###

####Specify the folder to look for classes under
location=mysite <default>   Only graph classes under the /mysite folder
location=/                  Graph ALL classes in every module (warning - may take a long time and could generate a large .png)
location=mysite,mymodule    Only graph classes under /mysite and /mymodule folders

####Remove specific classes from the graph
exclude=SiteTree
exlcude=SiteTree,File

####Show or hide inherited relations
inherited-relations=0 <default> Don't show inherited relations
inherited-relations=1			Show inherited relations (verbose)

####Include DataObject on the graph
include-root=0 <default>    Don't graph DataObject
include-root=1              Graph DataObject

####Group classes by folder/modules
group = 1 <default>  Don't group by folders
group = 0            Group the folders(modules) into their own boxes

### TO BE IMPLEMENTED

####How far to traverse and render relations
depth=0  Don't show any relations
depth=1  Only show relations between included classes
depth=2  Show next level of classes

####How far to show decesndants
ancestry=0 Don't show any ancestry relations
ancestry=1  <default> Show only immediate descendants

####Show or hide inherited database fields
inherited-fields=0 <default> Don't show inherited fields
inherited-fields=1			Show inherited fields (verbose)