#### Printing
```tcl
puts "hello world"; #prints hello world
```
Semicolon is not required to write single line commands without comments
{} may be used to print instead of double quotes, however it does not recognize variables
#### variables
```tcl
set str "this is str";
set value "1.5";
puts "$str";
puts"value is $value";
```
#### Command interpolation
```tcl
set a "5";
set b $a;
```
is the same as
```tcl
set b [set a "5"];
```
#### Arithmetic
```tcl
set a "5";
set b "3";
set c [expr "$a + $b"]; #8
```

##### Bitwise operations
* & = bitwise AND
* | = bitwise OR
* ^ = bitwise XOR
#### loops
