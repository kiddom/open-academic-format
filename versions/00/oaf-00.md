# Open Academic Format v0.0 (DRAFT)

## Abstract

Open Academic Format defines conceptual and concrete data structures as well as hierarchy to
pragmatically describe Academic Content such as Curriculum and Materials for Assignments. It aims to
increase ease of interoperability and general usage of said content in varied educational software
platforms.

## Status of Document

This document is a draft.

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

All data structures, unless otherwise noted, must allow an optional **id** field. Said **id** field must be [**IRI**](https://www.ietf.org/rfc/rfc3987.txt) compatible.

All data structures, unless otherwise noted, must allow an optional **ref** field. Said **ref** field must accept values previously defined in **id** fields.

### Summary

The summary shall be placed at the top of the file. There may only be one. This data structure **must not** include an **id**.

```json
{
  "author": "Anne Sullivan",
  "authors": ["Maria Montessori", "Jaime Escalante"],
  "date": "2019-02-19T23:20:50.52Z",
  "language": "en-US",
  "languages": ["fr-CA", "es-MX"],
  "title": "",
  "version": "",
  "organization": "what is this"
}
```

* author - Single author of this file. Should be a human.
* authors - An array of authors of this file. Should be humans.
* date - Date and time this file was created, or updated. Must be [RFC 3339](https://tools.ietf.org/html/rfc3339) compliant.
* language - Default language for the content described by this file.
* languages - Languages available in the content described by this file. If **language** is omitted, the first language in this list shall be considered the default.

### License

We're envisioning GPLv3 as the license for this specification.

### Asset

```json
{
  "url": "https://asset.host.edu/path/to/item",
}
```

### Grade

```json
{
  "id": "urn:grade:5",
  "name": "5th Grade",
  "names": {
    "fr-CA": "5ième année",
    "es-MX": "5 año"
  },
  "value": "5"
}
```

### MediaType

### Note

### Rubric

### Scoring

#### Scheme

#### Band

### Skills

```json
{
  "id": "urn:skill:k.cc.1",
  "name": "K.CC.1",
  "type": "Counting And Cardinality",
  "subtype": "Know Number Names And The Count Sequence.",
  "grade": "urn:grade:k",
  "grades": ["urn:grade:k"]
}
```

### Subject

```json
{
  "id": "urn:subject:trigonometry",
  "name": "Trigonometry",
  "names": {
    "fr-CA": "Trigonométrie",
    "es-MX": "Trigonometría",
  },
  "parent": "urn:subject:math"
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
  "curriculum": "urn:curriculum:english:1",
  "curriculums": [
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
  "days": 20,
  "skills": [
    "urn:skill:k.cc.1"
  ]
}
```

## Assignment Data Structures

### Assignment

```json
{

}
```

### Type

```json
{
  
}
```
