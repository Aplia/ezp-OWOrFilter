owOrFilter :
-------------------------
OWOrFilter (for OpenWide Object Relations Filter) provides an extended attribute filter for "Object relation" and "Object relations" datatypes.
This filter supports basic logical operators.
This will work with single relations as well as multiple.


[![Latest Stable Version](https://img.shields.io/packagist/v/aplia/oworfilter.svg?style=flat-square)](https://packagist.org/packages/aplia/oworfilter)
[![Minimum PHP Version](https://img.shields.io/badge/php-%3E%3D%205.3-8892BF.svg?style=flat-square)](https://php.net/)

Usage
-------------------------

This filter is used like any extended attribute filter, as explained on the
documentation for the content/list fetch function:
http://doc.ez.no/eZ-Publish/Technical-manual/4.x/Reference/Modules/content/Fetch-functions/list

Installation
-------------------------

Install with Composer:
```
composer require aplia/oworfilter
```

---------------------------------------------
Examples :
---------------------------------------------

Single object_id, single attribute :
---------------------------------------------

```tpl
{def $nodeList = fetch(content, list,
	hash(
		parent_node_id, XX,
		extended_attribute_filter, hash(
			'id', 'orfilter',
			'params', array(
				array('classe1/attribut1', 61)
		      )
		)
	)
)}
```


Multiple object_ids, single attribute :
---------------------------------------------

```tpl
{def $nodeList = fetch(content, list,
	hash(
		'parent_node_id', XX,
		'extended_attribute_filter', hash(
			'id', 'orfilter',
			'params', array(
				array('classe1/attribut1', array(70, 71), 'or')
			)
		)
	)
)}
```



Multiple object_ids, multiple attributes :
---------------------------------------------
```tpl
{def $nodeList = fetch(content, list,
	hash(
		'parent_node_id', XX,
		'extended_attribute_filter', hash(
			'id', 'orfilter',
			'params', array(
				'or',
				array('classe1/attribut1', array(70, 71), 'or'),
				array('classe2/attribut2', array(80, 81), 'and')
			)
		)
	)
)}
```

---------------------------------------------

