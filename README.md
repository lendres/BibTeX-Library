# BibTeX-Library
A utility library for BibTeX files written in C#.

## Ancestry
### BibTeX-Library
This library is based on the [BibTeXLibrary](https://github.com/BERef/BibTeXLibrary).  The library has been heavily modified to correct issues and add additions.  As a result, it is no longer compatible with the original library.  The objective of these modifications is to prepare the library for use in an application for maintaining a BibTeX file (see [BibTeX Manager]((https://github.com/lendres/BibTeX-Manager)).

This library is no longer actively maintained and updated.  It has been updated for use with .Net Maui, see below.

### Updated Library and User Interface
Please see [BibTeX Library Dot Net](https://github.com/lendres/BibTeX-Library-Dot-Net) for the updated version.  This version has an updated user interface [BibTeX Manager Maui](https://github.com/lendres/BibTex-Manager-Maui).

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
