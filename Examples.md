Example usage
=========

The examples below show the usage of `XMLXPath()` based on the following XML

```xml
<?xml version="1.0" encoding="utf-8"?>
<stock>
    <account>
        <name>Some Company</name>
    </account>
    <colours>
		<colour colourname="ACY">
			<longname>Antique Cherry Red</longname>
			<sizes>
				<p fts="276" size="S" nextday="0" cap="0" mystat="-"/>
				<p fts="386" size="M" nextday="0" cap="0" mystat="-"/>
				<p fts="677" size="L" nextday="0" cap="0" mystat="-"/>
				<p fts="393" size="XL" nextday="0" cap="0" mystat="-"/>
				<p fts="93" size="XXL" nextday="0" cap="0" mystat="-"/>
			</sizes>
		</colour>
		<colour colourname="ASA">
			<longname>Antique Sapphire</longname>
			<sizes>
				<p fts="76" size="S" nextday="0" cap="0" mystat="-"/>
				<p fts="143" size="M" nextday="0" cap="0" mystat="-"/>
				<p fts="119" size="L" nextday="0" cap="0" mystat="-"/>
				<p fts="108" size="XL" nextday="0" cap="0" mystat="-"/>
				<p fts="19" size="XXL" nextday="0" cap="0" mystat="-"/>
			</sizes>
		</colour>
        <colour colourname="BLK">
			<longname>Black</longname>
			<sizes>
				<p fts="76" size="S" nextday="0" cap="0" mystat="-"/>
				<p fts="143" size="M" nextday="0" cap="0" mystat="-"/>
				<p fts="119" size="L" nextday="0" cap="0" mystat="-"/>
				<p fts="108" size="XL" nextday="0" cap="0" mystat="-"/>
				<p fts="19" size="XXL" nextday="0" cap="0" mystat="-"/>
			</sizes>
		</colour>
    </colours>
</stock>
```

#### Get the name of the account holder
```
Let([
    NameNode = XMLXPath( XML; "/stock/account/name" )
  ];
 XMLValue(NameNode)
)
```
Will return
```
Some Company
```

#### Get the long name of the first colour
```
Let([
    ColourNode = XMLXPath( XML; "/stock/colours/colour[1]/longname")
  ];
 XMLValue(ColourNode)
)
```
Will return
```
Antique Cherry Red
```


#### Get the colourname attribute of the third colour
```
Let([
    Attribute = XMLXPath( XML; "/stock/colours/colour[3]/@colourname")
  ];
 Attribute
)
```
Will return
```
BLK
```


#### Find the value of the 'fts' attribute for size XXL where the colour colourname attribute is ASA
```
Let([
    FTS = XMLXPath( XML; "/stock/colours/colour[@colourname='ASA']/sizes/p[@size='XXL']/@fts" )
  ];
 FTS
)
```
Will return
```
19
```