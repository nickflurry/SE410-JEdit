# SE410-JEdit
JEdit for class

This branch is working on the following features of JEdit 
## Syntax Highlighting 
Our project extended jEdit languages highlighting feature, making it supports more languages. 

1. Edit-Mode Files <br />

In JEdit, Edit modes are defined in XML files, which determines the look of the text in the editor pane.
For example, java.xml specifies the highlighting rules for JAVA, JAVADOC. 
These files are usually placed in two directories:

* Setting directory <br />
** Mac:     ~/Library/jEdit/modes
** Windows: ~/AppData/jEdit/modes 

* Installation directory <br />
** path-to-where-u-install-jEdit/jEdit/modes

2. Load Mode File <br />
There are two ways to load a mode file and enable that edit mode in jEdit. 
* Add xml file to list manually<br />
In the directory(s) where the Edit Mode Files are placed, there is another xml file named catalog.xml
All edit modes contained in that directory must be listed in the catalog. We can add our own edit mode 
to list by just adding one sentence in catalog.xml:

```xml
<MODES>
...other modes listed here....
    <MODE NAME="matlab" FILE ="matlab.xml" FILE_NAME_GLOB="*.matlab"/>
...other modes listed here....
<MODES>
```
In this exmample, the mode tag has 3 attributes. <br />
```NAME ```  the name of our Edit mode. <br />
```File ``` the xml file specifying our mode <br />
```FILE_NAME_GLOB ``` the pattern of the files which our edit mode has effect on <br />

* Add mode with jEdit UI
Utilities -> Global Options... ->Editing -> Editing Modes 
![add_mode_with_jedit_ui](https://github.com/nickflurry/SE410-JEdit/blob/twig-jin/screenshot/addmode.PNG)

3. jEdit matlab highlighting V.S matlab built-in highlighting
![matlab-built-in highlighting](https://github.com/nickflurry/SE410-JEdit/blob/twig-jin/screenshot/originalhilighting.PNG)
![jedit-matlab-highlighting](https://github.com/nickflurry/SE410-JEdit/blob/twig-jin/screenshot/matlabhighlighting.PNG)

* highlighting rules improvement: 
** highlight all the function, function names are identified if matching the pattern function_name_to_be_highlighted()
** highlight all the numbers since matlab is a mathematic tool
** remove unnecessary highlighting

## FTP PLUGIN 
## jEdit PLUGIN MECHANISM
1. The files structure of plugin <br /> 
* Root Directory:<br /> 
    * build.xml
    * dockables.xml: implicitly define actions by defining dockable windows in dockable.xml 
    * actions.xml: explicitly define actions in actions.xml
    * servies.xml: work with other plugins         
    * PluginName.props: name/value pairs used to store human-readable strings, user settings, and various other forms of meta-data. 
    * users-guide.xml
    * description.html

* other resources in packages/subfolders

2. Load the plugin 
During startup, jEdit loads the default set of properties, followed by plugin properties stored in plugin JAR files, finally followed by user properties.


