## What needs to be done to get this shit to Work

To add categories the following items will need to be defined in store14 file

- @classifyarrayname
- @classifyarray
- %categoryarray
- %defaultcategoryarray
- %categoryarrayname
- %categoryarrayattri
- %categoryarrayattriname

### Example Use

##### @classifyarrayname
This section of the file determines what text will be displayed when representing classifications

For example, if we have the classification ```appliances``` and ```tools``` then we want to configure its display names like so
```
@classifyarrayname=("$lang{'Appliances'}", "$lang{'Tools'}");
```

##### @classifyarray
This is where we specify the name by which each classification will be known to the program. Think of it kind of like a variable or a "key"

Again, for our "appliances" and "tools" classifications
```
@classifyarray=("appliances", "tools")
```

##### %categoryarray
Here is where we will define the sup-categories for each of our classifications

This has the following pattern
```
"classification" => [
    "category",
    "category",
    .
    .
    .
]
```
So for our appliances classification we will do
```
%categoryarray=(
                "appliances" => [
                    "washer",
                    "dryer",
                    "sink"
                ]
);
```

##### %categoryarrayname
Like with classifications, this will be where we define what the display name will be for each category. These must be in the same order as the %categoryarray is defined

NOTE: The text within ```$lang{'...'}``` does not have to match the text in the category, it is mearly a key to lookup in the english file.
```
%categoryarrayname=(

                "appliances" => [
                    "$lang{'Washer'}",
                    "$lang{'Dryer'}",
                    "$lang{'Sink'}"
                ]
);
```

##### %defaultcategoryarray
Honestly, I don't know what this does, so just set it to the first category in your list.

```
%defaultcategoryarray=(
                      "appliances" => ["washer"]
);
```

##### %categoryarrayattri
This is where you will define what attributes each category will have

```
%categoryarrayattri=(

              "appliances" => {
                  "washer"    =>   ["price", "features"],
                  "dryer"     =>   ["price", "features"],
                  "sink"      =>   ["price"]
              }
);
```

##### %categoryarrayattriname
Like all sections prior to, this is where you define the display name of each attribute

```
%categoryarrayattriname=(
                "computerhardware" => {
                    "washer"       =>   ["$lang{'Price:'}|8|&nbsp;&nbsp", "$lang{'Features:'}|8|<br><br>"],
                    "dryer"        =>   ["$lang{'Price:'}|8|&nbsp;&nbsp", "$lang{'Features:'}|8|<br><br>"],
                    "sink"     =>   ["$lang{'Price:'}|8|&nbsp;&nbsp"]
                }
)
```

### English file
Everywhere you used a ```$lang{'...'}``` you need to define the value here. You don't have to define the same key multiple times though.

key#value#

```
sub customize {
$langindexkey=
"Appliances#Appliances#
Tools#Tools#
Washer#Washer#
Dryer#Dryer#
Sink#Sink#
Price:#Price:#
Features:#Features:#
";

}
```
