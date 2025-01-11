# BibTeX-Library
A utility library for BibTeX files written in C#.

## Ancestry
### Original Offshoot
This library is based on the [BibTeXLibrary](https://github.com/BERef/BibTeXLibrary).  The library has been heavily modified to correct issues and add additions.  The objective of these modifications is to prepare the library for use in an application for maintaining a BibTeX file (see [BibTeX Manager](https://github.com/lendres/BibTex-Manager-Maui)).  As a result, it is no longer compatible with the original library.

### Updated Library and User Interface
The combination of the large number of changes, the lack of maintenance of the original repository, and the requirement to update the project files and .Net version led to the decision to create a new repository (it no longer made sense to keep it as a fork of the original).  Please see [BibTeX Library Dot Net](https://github.com/lendres/BibTeX-Library-Dot-Net) for the updated version.  This version has an updated user interface [BibTeX Manager Maui](https://github.com/lendres/BibTex-Manager-Maui).

## Usage at a glance
- string -> BibEntry
```csharp
var parser = new BibParser(
                new StringReader(
                  "@article{keyword, title = {\"0\"{123}456{789}}, year = 2012, address=\"PingLeYuan\"}"));
var entry = parser.GetAllResult()[0];
```

- BibEntry
```csharp
// Get Property
entry.Type;       // string: Article
entry.Title;      // string: 0{123}456{789}
entry["Title"];   // string: 0{123}456{789}
```

- BibEntry -> string
```csharp
entry.ToString();
// @Article{keyword,
//   title = {0{123}456{789}},
//   year = {2012},
//   address = {PingLeYuan},
// }
```

- Local File -> BibEntries
```csharp
var parser = new BibParser(new StreamReader("text.bib", Encoding.Default));
var entries = parser.GetAllResult();

foreach(var entry in entries) { ... }
```
