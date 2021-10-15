# XMLSTARLET

## Display element structure of XML document: `el`

````bash
xmlstarlet el atom-icon-associations.xml
xmlstarlet el -a atom-icon-associations.xml  # And attributes.
xmlstarlet el -v atom-icon-associations.xml  # Attributes and values.
````

## Select data or query XML document(s) (XPATH, etc): `sel`

````bash
xmlstarlet sel --root atom-icon-associations.xml  # Print root element <xsl-select>.
````


## Edit/Update XML document(s): `ed`

````bash
xmlstarlet ed atom-icon-associations.xml
````
