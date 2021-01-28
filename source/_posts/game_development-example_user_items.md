---
title: Example for items of a game user.
date: 2021-01-28 09:00:00
updated: 2021-01-28 10:00:00
categories:
- Game Development
tags:
- Game Development
- Entity Relationship
- Typescript
---

## Basics

First, the game should has some basic types. I use typescript language to describe these types.
The game has a root item types: money, cloth and clothes.

```ts
//ItemType is a top type of item.
enum ItemType {
    UNDEFINED,
    MONEY,
    CLOTH,
    CLOTHES,
}

//Item is a base type of item
interface Item {
    id: string, //The property id of item should be unique to every item instances.
    typeId: string, //The property typeId of item is string composed of all levels of the hierarchy of item type.
    type: ItemType, // The property type of item indicate a item is money, cloth or clothes.
    num: number, // The property num of item is a quantity of item.
}

//User is type of user
interface User {
    id: string, // A user owns a unique id too.
    name: string, // A user has a name.
    items: Item[], // This is a array of items user owns.
}

//This constant is a user object
const user: User = {
    id: ...,
    name: ...,
    items: [],
};

```

### Money

Money is a single instance, so it can be created directly in code.

```ts
const user: User = {

    ... 

    items: [ 
        {
            id: ...,
            typeId: "1", //Money has only one level type of 1.
            type: Item.MONEY,
            num: ...,
        }

        ...
    ]
}
```

### Cloth

There are many kind of cloth. Same kind of cloth has same properties and its value, so they can put into a single object.  

Config:

| type_id:string (auto generated) | item_type:int32 | cloth_type:int32 | name:string  |
| ---                             | ---             | ---              | ---          |
| 2-1                             | 2               | 1                | White Cloth  |
| 2-2                             | 2               | 2                | Black Cloth  |
| 2-3                             | 2               | 3                | Red Cloth    |

```ts

enum ClothType {
    UNDEFINED,
    WHITE,
    BLACK,
    RED,
}

interface ClothItem extends Item {
    clothType: ClothType, 
}

const user: User = {

    ... 

    items: [

        ...

        {
            id: ...,
            typeId: "2-1", //Cloth has two level of types, they connect with "ItemType-ClothType".
            type: ItemType.Cloth,
            clothType: ClothType.WHITE,
            num: ...,
        },

        {
            id: ...,
            typeId: "2-2", //Cloth has two level of types, they connect with "ItemType-ClothType".
            type: ItemType.Cloth,
            clothType: ClothType.BLACK,
            num: ...,
        }

        ...
    ]
}

```

### Clothes

There are many kind of clothes. Same properties of same kind of clothes can own different value, so every instance of clothes should be a object alone.  

Config:

| type_id:string (auto generated) | item_type:int32 | clothes_type:int32 | name:string |durability:int32 (unit: day) |
| ---                             | ---             | ---                | ---         | --- |
| 3-1                             | 3               | 1                  | Pure White  |  2  |
| 3-2                             | 3               | 2                  | Pinto       |  3  |

```ts

enum ClothesType {
    UNDEFINED,
    PURE_WHITE,
    PINTO,
}

interface ClothesItem extends Item {
    clothesType: ClothesType,
    remainDay: number, //Remain time (uint: day)
}

const user: User = {

    ... 

    items: [

        ...

        {
            id: ...,
            typeId: "3-1", //Clothes has two level of types, they connect with "ItemType-ClothesType".
            type: ItemType.Clothes,
            clothesType: ClothesType.PURE_WHITE,
            num: 1, //Clothes num is always one.
            remainDay: ..., //Different clothes has different ramain day
        },

        {
            id: ...,
            typeId: "3-2", //Clothes has two level of types, they connect with "ItemType-ClothesType".
            type: ItemType.Clothes,
            clothesType: ClothesType.PINTO,
            num: 1, //Clothes num is always one.
            remainDay: ..., //Different clothes has different ramain day
        },

        ...
    ]
}

```
