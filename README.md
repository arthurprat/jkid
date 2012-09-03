jkid
====

Small shell json reader. Useful to explore big jsons contained in files. Written in Python.

Usage : jkid \[options\] \[key1 \[key2 \[...\]\]\] < input

Example :
	$  echo '{"a":"b", "c": ["d", {"e" : "f"}, {"g" : [1,2,3,4]} ] }' > test.json 
	$  jkid c 2 g < test.json
	c > f :
	{
  	  "g": "h"
	}

Installation : copy jkid in a directory in your $PATH.

Requirements : Python.