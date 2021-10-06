# About

This library was primarily developed as a learning experience but may prove useful as a general purpose suite of libraries usable in a variety of situations.

## Objective

These files are not intended to be operated as single-file libiraries but rather a collection of smaller libraries that operate cooperatively.

The intent is to grow the library as new needs occurs during the various project / demo developments. If there is specify interest or demand adjustments can be made if viable.

## Library Structure
The following is a library hirarchy focused on piTerminal as an example structure. It also includes any unreferenced libraries. A brief cutsheet of library features is also listed.
<table style="border-width:0px; margin: 0px; padding: 0px">
<tr>

<td style="vertical-align: top">

<h3>piCommon</h3>
<p>Common Constants and Functions for All Applications and Libraries</p>
<ul style="margin-bottom: 28px">
<li>Timeout Constants</li>
<li>Timeout to and from System Count Functions</li>
<li>Standard Library Abort Codes and Strings</li>
</ul>

<h3>piDiagnostics</h3>
<p>Troublingshoot and Profiling Tools</p>
<ul style="margin-bottom: 28px">
<li>Stack Usage Monitoring</li>
</ul>

<h3>piString</h3>
<p>String Formatting and Parsing</p>
<ul style="margin-bottom: 28px">
<li>String Formatting (similar to printf)</li>
<li>String Parsing</li>
<li>Unbound from Communication Library (use any)</li>
</ul>

<h3>piInlineSerial</h3>
<p>Asyncronuous Serial Communication as Background Service</p>
<ul style="margin-bottom: 28px">
<li>Read and Write Buffers</li>
<li>Automatic background buffer handling</li>
<li>Error Detection and Signaling</li>
</ul>

<h3>piTerminal</h3>
<p>Basic Terminal-Like User Interface</p>
<ul style="margin-bottom: 28px">
<li>Promp-style Input</li>
<li>Cursor Movement</li>
<li>Inserting/Deleting anywhere within the line</li>
</ul>
</td>
<td><img src="Documentation/Graph/piLibrary%20Dependency.svg"/></td>
</tr>
</table>

## Build Tools
The library is designed to be used with **Parallax PropTool**. Due to certain Spin2 constructs, some libraries are known to be incompatible with other toolchains. Only PropTool has been thoroughly tested.

## Contributions

The library has been made open source for use, to lead as an example, and to allow the community to contribute by using github tools or through community interaction. You can find me at the Parallax Forums under the name *DarkInsanePyro*.

# Getting Started

## Prerequisites

* PropTool 1.5.2 or newer

## Installation
Clone or download this repo from github. If a ZIP is downloaded, extract it to its own folder.

**Cloning:**
```sh
git clone https://github.com/Perpetual-Intrigue/piLibrary.git
```

### Standalone Demo
1. Copy the demo files from /Demo to the parent folder along side the library files
2. Open the desired Demo_* file with PropTool
3. Optionally assign as *Top Object File*
4. Compile and Run with Debugging Enabled

### Application-Local Installation
1. Copy required libraries and their dependencies to your applications source folder
2. Reference the required libraries as OBJ instances

### Library Installation
1. Move the library files from *Root* to the the PropTool's library folder
   * Windows: *User*/Documents/PropTool/Library
2. Test the installation by trying to compile one of the Demo_* files provided in the *Root*/Demos folder

## Usage

Include any required libraries as OBJs within your application. Follow the documentation provided within the library. The recommended way to view this is by using the *Documentation* view within the PropTool application on the target libraries.

Some libraries only provide support functions and should be treated like singletons. Although this isn't possible with the software, the overhead of creating one-off instances of the library are minimal (1 long per instance generally). Library nomenclature follows that singletons use the same library name as seen to indicate it is not genuinely an instance.

## Basic Example
```
OBJ
  piCommon:   "piCommon"
  piString:   "piString"
  serial:     "piSerial"

PUB Main()
  serial.Start(9600, 0, 1, serial.DEFAULT_CONFIG)
  repeat
    serial.Write(string("Hello World!",piString.CR,piString.LF), -1, piCommon.TIME_INFINITE)
```


# License
This library is destributed under the MIT License. See [LICENSE](LICENSE.md) for more information.
