jkid
====

Command-line json explorer. Useful to explore big jsons.  
jkid was written in Python.

Usage
-----

	jkid [options] [key1 [key2 [...]]] file

Works also with `stdin` and no `file` argument.  
A key can be an object key or an array index. Array indexes can be negative.  
If you have an array or an object which contains similar objects (i.e. objects that share the same name/value structure),
you can use a dot `.` as a key at some level : it will expand the json for every object at that level (see examples 2 and 3),
allowing for 'transversal' exploration of the json. Note that in that case the following keys must be in all objects at that level.

Options :

    -f / --flexible Returns null if a key is not in the object. Useful when using the dot `.` key and following keys are not in all sub-objects.
	-p / --preview	Displays only one level, with information on the object's content at that level. Prevents console logorrhea.
	-c / --count	For arrays, returns the length; For objects, returns the number ok keys; For strings, returns the length. Else returns 0.
	-q / --quiet	
	-h / --help		

Example
-------
	$  echo '{"a":"b", "c": ["d", {"e" : "f"}, {"g" : [1,2,{"h":"i"}]} ] }' > test.json
	$  jkid c 2 g test.json
	object["c"][2]["g"]
	[
	  1, 
	  2, 
	  {
	    "h": "i"
	  }
	]
	$
	$  echo '[{"a":1,"b":0},{"a":2,"b":0},{"a":3,"b":0}]' | jkid . a
	object[.]["a"]
	[
	  1, 
	  2, 
	  3
	]
	$
	$  echo '{"john":{"size":20, "eyes":"green"}, "bob":{"size":30, "eyes":"brown"}}' > test3.json
	$  jkid . size test3.json 
	object[.]["size"]
	{
	  "bob": 30, 
	  "john": 20
	}
	$  jkid . eyes test3.json 
	object[.]["eyes"]
	{
	  "bob": "brown", 
	  "john": "green"
	}


Installation
------------
Use directly `./jkid` or copy jkid in a directory that's in your `$PATH` or symlink it.

Requirements
------------

Python.