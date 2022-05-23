---
title: Expressjs API Boilerplate Dev Setup
published: false
description: 
tags: multipurpose api, express.js, boilerplate
//cover_image: https://direct_url_to_image.jpg
---

## Create api project with express-generator
- no-views
- project name e.g my-api
```bash
npx express-generator --no-view --git my-api
```

## Directory structure
1. Enter app directory
```bash
cd my-api
```
2. delete /public folder and its content
```bash
rm -r public
```
3. End Structure
```
.
├── app.js
├── bin
│   └── www
├── package.json
└── routes
    ├── index.js
    └── users.js

2 directories, 5 files 
```
## Create following folders
```bash
mkdir controllers && mkdir services && mkdir database
```
### Inside controllers and services directories add files
```bash
touch controllers/apiController.js && touch services/apiService.js
```

### In database directory
```bash
touch db.json Item.js
```

### Directory structure now looks like this
```
.
├── app.js
├── bin
│   └── www
├── controllers
│   └── apiController.js
├── database
│   ├── db.json
│   └── Items.js
├── package.json
├── public
│   ├── images
│   ├── javascripts
│   └── stylesheets
│       └── style.css
├── routes
│   ├── index.js
│   └── users.js
└── services
      └── apiService.js
 

8 directories, 8 files

```

## Open /controllers/apiController.js with vim editor

```bash
vim controllers/apiController.js
```

```js
// In /controllers/apiController.js
const getAllItems = (req, res) => {
  res.send("Get all items");
};

const getOneItem = (req, res) => {
  res.send("Get an existing item");
};

const createNewItem = (req, res) => {
  res.send("Create a new item");
};

const updateOneItem = (req, res) => {
  res.send("Update an existing item");
};

const deleteOneItem = (req, res) => {
  res.send("Delete an existing item");
};

module.exports = {
  getAllItems,
  getOneItem,
  createNewItem,
  updateOneItem,
  deleteOneItem,
};
```

### Pasting in vim in normal mode 
```vim
"+gP
```
### Inside routes/index.js add following

```js
router.get("/", itemController.getAllItems);

router.get("/:itemId", itemController.getOneItem);

router.post("/", itemController.createNewItem);

router.patch("/:itemId", itemController.updateOneItem);

router.delete("/:itemId", itemController.deleteOneItem);

```

### In services/apiService.js
```js
const getAllItems = () => {
  return;
};

const getOneItem = () => {
  return;
};

const createNewItem = () => {
  return;
};

const updateOneItem = () => {
  return;
};

const deleteOneItem = () => {
  return;
};

module.exports = {
  getAllItems,
  getOneItem,
  createNewItem,
  updateOneItem,
  deleteOneItem,
};
```

```js
// In /controllers/apiController.js
// *** ADD ***
const apiService = require("../services/apiService");

const getAllItems = (req, res) => {
   const allItems = itemService.getAllItems();
  res.send("Get all items");
};

const getOneItem = (req, res) => {
   const item = itemService.getOneItem();
  res.send("Get an existing item");
};

const createNewItem = (req, res) => {
   const createdItem = itemService.createNewItem();
  res.send("Create a new item");
};

const updateOneItem = (req, res) => {
   const updatedItem = itemService.updateOneItem();
  res.send("Update an existing item");
};

const deleteOneItem = (req, res) => {
   const item = itemService.deleteOneItem();
  res.send("Delete an existing item");
};

module.exports = {
  getAllItems,
  getOneItem,
  createNewItem,
  updateOneItem,
  deleteOneItem,
};
```

## db.json paste your test json 

```json
{
    "first_name": "John",
    "last_name": "Doe",
    "email": "",
    "ewallet_reference_id": "John-Doe-02152020",
    "metadata": {
        "merchant_defined": true
    },
    "phone_number": "",
    "type": "person",
    "contact": {
        "phone_number": "+14155551311",
        "email": "johndoe@rapyd.net",
        "first_name": "John",
        "last_name": "Doe",
        "mothers_name": "Jane Smith",
        "contact_type": "personal",
        "address": {
            "name": "John Doe",
            "line_1": "123 Main Street",
            "line_2": "",
            "line_3": "",
            "city": "Anytown",
            "state": "NY",
            "country": "US",
            "zip": "12345",
            "phone_number": "+14155551111",
            "metadata": {},
            "canton": "",
            "district": ""
        },
        "identification_type": "PA",
        "identification_number": "1234567890",
        "date_of_birth": "11/22/2000",
        "country": "US",
        "nationality": "FR",
        "metadata": {
            "merchant_defined": true
        }
    }
}
```

# Show all Items 

```js
// In src/database/Workout.js
const DB = require("./db.json");

const getAllItems = () => {
  return DB;
};

module.exports = { getAllItems };
```

```js
// In src/database/itemService.js
const Item = require("../database/Item");
const getAllItems = () => {
  const allItems = Item.getAllItems();
  return allItems;
};

module.exports = { getAllItems };
```

```js
// In src/controllers/itemControllers.js
const itemService = require("../services/itemService");

const getAllItems = (req, res) => {
  const allItems = itemService.getAllItems();
  res.send({ status: "OK", data: allItems });
};

module.exports = { getAllItems };
```

```js
var express = require('express');
var router = express.Router();
const itemController = require("../../controllers/itemControllers");

router.get("/", itemController.getAllItems);

module.exports = router;

```
#TODO show the results in browser

### Speed up the process
```js

```