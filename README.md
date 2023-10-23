# materiahunter-data

A repository of Final Fantasy Trading Card Game data, formatted for https://www.materiahunter.com

## Folder / File / Data Structure
Data on cards, card variants, and products are all separated into their own folders.

```
/cards
/card-variants
/products
```

Cards should be separated into subfolders by opus.

```
/cards/01/
/cards/02/
/cards/03/
/cards/PR/
```

Each card should be in it's own `.json` file with the serial number as the name of the file.
```
/cards/01/1-001H.json
```

Card variants should be separated into subfolders by opus, or by product if the variant wasn't released in the print run of that opus.

```
/card-variants/01/
/card-variants/02/
/card-variants/03/
/card-variants/PR/
/card-variants/Noir_Collection/
```

Each card variant should be in it's own `.json` file. The name of the file should be in the following format:

`{serial}_{secondary_serial}_{F/NF}_{FA}`

|part|description|optional|
|-|-|-|
|serial|The first serial listed on the card|no|
|secondary_serial|The second serial listed on the card.|yes. If no second serial exists, leave out this field, and the `_` that proceeds it.|
|F/NF|`F` if the card is foil. `NF` if the card is non-foil|no|
|FA|`_FA` if the card is full art.|yes. If the card is not full art, leave out this field, and the `_` that proceeds it.|

## Adding New Cards

### Schema
```
{
    serial: string,
    name: string | undefined,
    opus: number,
    number: number,
    abilities: string[] | undefined,
    power: number | undefined,
    categoryIds: number[] | undefined,
    jobs: number[] | undefined,
    rarity: string | undefined,
    cost: number | undefined,
    elements: CardElementName[] | undefined,
    type: CardType | undefined,
    isExBurst: boolean | undefined,
    isMultiPlayable: boolean | undefined,
    isSpecial: boolean | undefined
}
```

|property|description|examples|
|-|-|-|
|serial|The second serial number displayed on the card. For instance, if the serial displays `PR-999/21-091`, the value for `serial` would be `21-091`. |`"serial": "21-091"`|
|name|The name displayed on the card.|`"name": "Locke"`|
|opus|||
|number|||
|abilities|||
|power|||
||||
