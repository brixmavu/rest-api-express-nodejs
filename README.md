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
├── routes
│   ├── index.js
│   └── users.js
└── services
      └── apiService.js
 

6 directories, 7 files

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

}
```

# Show all Items 

```js
// In src/database/Workout.js

const getAllItems = () => {
  return DB;
};
```

```js
// In src/database/itemService.js

const getAllItems = () => {
  const allItems = Item.getAllItems();
  return allItems;
};

```

```js
// In src/controllers/itemControllers.js

const getAllItems = (req, res) => {
  const allItems = itemService.getAllItems();
  res.send({ status: "OK", data: allItems });
};

```

#TODO show the results in browser

# Create single item collection
```js

```
