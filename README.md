### Description

This repo includes two python3 scripts, which respectively print json and yaml
with full paths per value:

 - `grson`
 - `gryaml`


### Dependencies

 - python3


### Installation

Just drop them into somewhere in your `$PATH`


### Usage

```sh
$ grson < file.json
$ gryaml < file.yaml
$ command-that-outputs-json | grson
$ command-that-outputs-yaml | gryaml
```

### Example output

```sh
% cat example.json
[
  {
    "_id": "6080ee529c81f656bb9f1fd5",
    "tags": [
      "elit",
      "veniam",
      "tempor",
      "dolore",
      "irure",
      "non",
      "id"
    ],
    "friends": [
      {
        "id": 0,
        "name": "Jackson Gallegos"
      },
      {
        "id": 1,
        "name": "Matthews Patel"
      },
      {
        "id": 2,
        "name": "Powell Beasley"
      }
    ],
    "greeting": "Hello, undefined! You have 7 unread messages.",
    "favoriteFruit": "banana"
  },
  {
    "_id": "6080ee52582f0beb95582173",
    "tags": [
      "non",
      "id",
      "laborum",
      "esse",
      "incididunt",
      "sit",
      "in"
    ],
    "friends": [
      {
        "id": 0,
        "name": "Miranda Acosta"
      },
      {
        "id": 1,
        "name": "Blevins Giles"
      },
      {
        "id": 2,
        "name": "Sherry Wyatt"
      }
    ],
    "greeting": "Hello, undefined! You have 7 unread messages.",
    "favoriteFruit": "strawberry"
  }
]
%
% cat example.yaml
_id: 6080ee529c81f656bb9f1fd5
favoriteFruit: banana
friends:
- id: 0
  name: Jackson Gallegos
- id: 1
  name: Matthews Patel
- id: 2
  name: Powell Beasley
greeting: Hello, undefined! You have 7 unread messages.
tags:
- elit
- veniam
- tempor
- dolore
- irure
- non
- id
---
_id: 6080ee52582f0beb95582173
favoriteFruit: strawberry
friends:
- id: 0
  name: Miranda Acosta
- id: 1
  name: Blevins Giles
- id: 2
  name: Sherry Wyatt
greeting: Hello, undefined! You have 7 unread messages.
tags:
- non
- id
- laborum
- esse
- incididunt
- sit
- in
% grson < example.json
this[0]._id = "6080ee529c81f656bb9f1fd5"
this[0].tags[0] = "elit"
this[0].tags[1] = "veniam"
this[0].tags[2] = "tempor"
this[0].tags[3] = "dolore"
this[0].tags[4] = "irure"
this[0].tags[5] = "non"
this[0].tags[6] = "id"
this[0].friends[0].id = 0
this[0].friends[0].name = "Jackson Gallegos"
this[0].friends[1].id = 1
this[0].friends[1].name = "Matthews Patel"
this[0].friends[2].id = 2
this[0].friends[2].name = "Powell Beasley"
this[0].greeting = "Hello, undefined! You have 7 unread messages."
this[0].favoriteFruit = "banana"
this[1]._id = "6080ee52582f0beb95582173"
this[1].tags[0] = "non"
this[1].tags[1] = "id"
this[1].tags[2] = "laborum"
this[1].tags[3] = "esse"
this[1].tags[4] = "incididunt"
this[1].tags[5] = "sit"
this[1].tags[6] = "in"
this[1].friends[0].id = 0
this[1].friends[0].name = "Miranda Acosta"
this[1].friends[1].id = 1
this[1].friends[1].name = "Blevins Giles"
this[1].friends[2].id = 2
this[1].friends[2].name = "Sherry Wyatt"
this[1].greeting = "Hello, undefined! You have 7 unread messages."
this[1].favoriteFruit = "strawberry"
%
% grson < example.yaml
Traceback (most recent call last):
  File "/home/hyperair/bin/grson", line 25, in <module>
    obj = json.loads(sys.stdin.read())
  File "/usr/lib/python3.8/json/__init__.py", line 357, in loads
    return _default_decoder.decode(s)
  File "/usr/lib/python3.8/json/decoder.py", line 337, in decode
    obj, end = self.raw_decode(s, idx=_w(s, 0).end())
  File "/usr/lib/python3.8/json/decoder.py", line 355, in raw_decode
    raise JSONDecodeError("Expecting value", s, err.value) from None
json.decoder.JSONDecodeError: Expecting value: line 1 column 1 (char 0)
%
% gryaml < example.yaml
this._id = "6080ee529c81f656bb9f1fd5"
this.favoriteFruit = "banana"
this.friends[0].id = 0
this.friends[0].name = "Jackson Gallegos"
this.friends[1].id = 1
this.friends[1].name = "Matthews Patel"
this.friends[2].id = 2
this.friends[2].name = "Powell Beasley"
this.greeting = "Hello, undefined! You have 7 unread messages."
this.tags[0] = "elit"
this.tags[1] = "veniam"
this.tags[2] = "tempor"
this.tags[3] = "dolore"
this.tags[4] = "irure"
this.tags[5] = "non"
this.tags[6] = "id"
---
this._id = "6080ee52582f0beb95582173"
this.favoriteFruit = "strawberry"
this.friends[0].id = 0
this.friends[0].name = "Miranda Acosta"
this.friends[1].id = 1
this.friends[1].name = "Blevins Giles"
this.friends[2].id = 2
this.friends[2].name = "Sherry Wyatt"
this.greeting = "Hello, undefined! You have 7 unread messages."
this.tags[0] = "non"
this.tags[1] = "id"
this.tags[2] = "laborum"
this.tags[3] = "esse"
this.tags[4] = "incididunt"
this.tags[5] = "sit"
this.tags[6] = "in"
```
