# Open Academic Format v0.0 (DRAFT)

## Abstract

Open Academic Format defines conceptual and concrete data structures as well as hierarchy to
pragmatically describe Academic Content such as Curriculum and Materials for Assignments. It aims to
increase ease of interoperability and general usage of said content in varied educational software
platforms.

## Status of Document

This document is a draft, and is open for comments via [GitHub Issues](https://github.com/kiddom/open-academic-format/issues).

## Terminology and Conformance Language

Normative text describes one or both of the following kinds of elements:

* Vital elements of the specification
* Elements that contain the conformance language key words as defined by [IETF RFC 2119](https://www.ietf.org/rfc/rfc2119.txt) "Key words for use in RFCs to Indicate Requirement Levels"

Informative text is potentially helpful to the user, but dispensable. Informative text can be changed, added, or deleted editorially without negatively affecting the implementation of the specification. Informative text does not contain conformance keywords.

All text in this document is, by default, normative.

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be interpreted as described in [IETF RFC 2119](https://www.ietf.org/rfc/rfc2119.txt) "Key words for use in RFCs to Indicate Requirement Levels".

## Definitions and Terminology

TODO

## Table of Contents

TODO

## Introduction

TODO

## Base Data Structures

All data structures, unless otherwise noted, **MUST** allow an optional **id** field. Said **id** field **MUST** be [**IRI**](https://www.ietf.org/rfc/rfc3987.txt) compliant. While IRIs accepts several protocols, IRIs used within this format **SHALL** use the following protocols.

* urn
* https

All data structures, unless otherwise noted, **MUST** allow an optional **ref** field. Said **ref** field **MUST** accept values previously defined in **id** fields within said document. A **ref** may also use a publicly defined **id** values.

### Summary

The summary **SHALL** be placed at the top of the file. There may only be one. This data structure **MUST NOT** include an **id**.

```json
{
  "authors": ["Maria Montessori", "Jaime Escalante"],
  "date": "2019-02-19T23:20:50.52Z",
  "languages": ["en-US", "fr-CA", "es-MX"],
  "title": "Kindergarten Curriculum",
  "version": "1",
  "organization": "what is this"
}
```

* authors - An array of authors of this file. Should be humans. All authors **MUST** be displayed when requested.
* date - Date and time this file was created, or updated. Must be [RFC 3339](https://tools.ietf.org/html/rfc3339) compliant.
* languages - Languages available in the content described by this file. The first language in this list **SHALL** be considered the default.

### License

Open Academic Interchange Format for Curriculum and Materials.

Copyright (C) 2019  Kiddom, Inc.

This specification is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This specification is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see <http://www.gnu.org/licenses/>.

### Asset

```json
{
  "id": "urn:kiddom.co:asset:fb060824-9842-48b8-ae82-cf528cc106ca",
  "url": "https://asset.host.edu/path/to/item",
}
```

### Grade

```json
{
  "id": "urn:grade:5",
  "names": {
    "en-US": "5th Grade",
    "fr-CA": "5ième année",
    "es-MX": "5 año"
  },
  "value": "5"
}
```

### MediaType

```json
{
  "category": "image",
  "content_type": "image/png",
  "name": "PNG Image"
}
```

### Note

```json
{
}
```

### Rubric

```json
{
  "name": "Critical Thinking",
  "description": "General Education Scoring Guide for Critical Thinking",
  "criteria": [
    {
      "name": "Interpretation",
      "levels": [
        {
          "value": 1,
          "description": "Fails to question data. Ignores bias. Misses major content areas. Detects no inconsistencies. Chooses biased sources."
        },
        {
          "value": 2,
          "description": "Identifies some questions. Notes some bias. Recognizes basic content. States some inconsistencies. Selects sources adequately."
        },
        {
          "value": 3,
          "description": "Asks insightful questions. Detects bias. Categorizes content. Identifies inconsistencies. Recognizes context."
        },
        {
          "value": 4,
          "description": "Analyzes insightful questions. Refutes bias. Critiques content. Examines inconsistencies. Values information."
        }
      ]
    }
  ]
}
```

### Scoring

```json
```

#### Scheme

```json
```

#### Band

```json
```

### Skills

```json
{
  "id": "urn:skill:k.cc.1",
  "name": "K.CC.1",
  "type": "Counting And Cardinality",
  "subtype": "Know Number Names And The Count Sequence.",
  "grades": ["urn:grade:k"]
}
```

### Subject

```json
{
  "id": "urn:subject:trigonometry",
  "names": {
    "en-US": "Trigonometry",
    "fr-CA": "Trigonométrie",
    "es-MX": "Trigonometría",
  },
  "parent": "urn:subject:mathematics"
}
```

## Curriculum Data Structures

### Course

```json
{
  "name": "English 1",
  "grades": [
    "urn:grade:k"
  ],
  "subjects": [
    "urn:subject:ela"
  ],
  "curriculums": [
    "urn:curriculum:english:1",
    "urn:curriculum:english:2",
    "urn:curriculum:english:3"
  ]
}
```

### Curriculum

```json
{
  "id": "urn:curriculum:english:1",
  "name": "English 1 Curriculum",
  "units": [
    "urn:unit:nouns",
    "urn:unit:verbs",
  ]
}
```

### Unit

```json
{
  "id": "urn:unit:nouns",
  "name": "Nouns & Adjectives: A Love Story",
  "description": "A longer, more descriptive set of sentences. Possibly paragraphs.",
  "skills": [
    "urn:skill:k.cc.1"
  ]
}
```

## Assessment Data Structures

### Assessment

```json
{
  "id": "urn:assessment:123456",
  "name": "Student-Facing Task Statement",
  "type": "urn:type:paper",
}
```

### Assessment: Homework

```json
{
  "id": "urn:assessment:123456",
  "type": "urn:type:homework",
  "name": "Student-Facing Task Statement",
  "description": "Think about your work today, and write your best definition of area.",
}
```

### Assessment: Paper

```json
{
  "id": "urn:assessment:123456",
  "type": "urn:type:paper",
  "name": "Student-Facing Task Statement",
  "description": "Think about your work today, and write your best definition of area.",
  "formats": [
    "application/msword",
    "application/vnd.openxmlformats-officedocument.wordprocessingml.document",
    "application/vnd.oasis.opendocument.text",
    "application/pdf",
  ]
}
```

### Assessment: Video

```json
{
  "id": "urn:assessment:123456",
  "type": "urn:type:video",
  "name": "Student-Facing Task Statement",
  "description": "Watch this video.",
  "resources": [
    {
      "category": "video",
      "content_type": "video/youtube",
      "name": "",
      "url": "https://..../"
    }
  ]
}
```

### Assessment: Quiz

```json
{
  "id": "urn:assessment:123456",
  "type": "urn:type:quiz",
  "name": "Student-Facing Task Statement",
  "description": "Look for a pattern in the figures.",
  "questions": [
    {
      "description": "1. How many total tiles will be in:\n\n\ta. the 4th figure?\n\tb. the 5th figure?\n\tc. the 10th figure?\n\n<img src\"\" />",
      "ordered": [
        "url:assessment:answer:123456",
        "url:assessment:answer:234567",
        "url:assessment:answer:345678"
      ],
      "answers": [
        {
          "id": "url:assessment:answer:123456",
          "description": "28 tiles",
          "type": "urn:input:mathematical",
        },
        {
          "id": "url:assessment:answer:234567",
          "description": "35 tiles",
          "type": "urn:input:mathematical",
        },
        {
          "id": "url:assessment:answer:345678",
          "description": "70 tiles",
          "type": "urn:input:mathematical",
        }
      ],
      "type": "urn:assessment:quiz:fill-blanks",
      "resources": [
        {
          "category": "applet",
          "content_type": "applet:geogebra",
          "name": "Geogebra Applet",
          "url": "https://..../"
        }
      ]
    }
  ]
}
```

#### Assessment: Quiz, question types
* Multiple choice - `urn:assessment:quiz:multiple-choices`
* Fill in the blank - `urn:assessment:quiz:fill-blanks`
* Freeform submit - `urn:assessment:quiz:open-response`
* Submit document - `urn:assessment:quiz:submit-document`


### Type information

```json
{
  "id": "urn:assessment:type:paper",
  "name": "Paper",
  "description": "A written assignment",
}
```

A Type of Assessment. Implementors **MUST NOT** restrict to known types. The following types **SHALL** always be available for use.

* Homework - `urn:type:homework`
* Paper - `urn:type:paper`
* Quiz - `urn:type:quiz`
* Video - `urn:type:video`
