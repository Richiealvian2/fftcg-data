# materiahunter-data

A repository of Final Fantasy Trading Card Game data, formatted for https://www.materiahunter.com

## Folder / File / Data Structure
Data on cards, card variants, and products are all separated into their own folders.

```
/cards
/card-variants
/products
```

Cards should be separated into subfolders by opus. If the card displays multiple opus (`10-001/4-002`), the opus that comes second should be used (`04` in this example).

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

```
/card-variants/01/1-001H_F.json
/card-variants/01/1-001H_NF.json
/card-variants/Noir_Collection/15-138S_F_FA.json
```

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
    categories: string[] | undefined,
    jobs: string[] | undefined,
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
|opus|The opus of the card. If there are two serial numbers listed, use the opus of the second serial number.|For a card with serial number `10-001/4-002`, the opus would be `"opus": 4`.|
|number|Ths number of the card as seen on the serial. If there are two serial numbers listed, use the number of the second serial number.|For a card with the serial number `10-001/4-002`, the number would be `"number": 2`.|
|abilities|An array of strings with the cards ability text. Each new paragraph on the cards ability text is a new element in the array. **SEE ABILITY TEXT SECTION BELOW FOR MORE INFO**||
|power|The power listed on the card. Leave this out if no power is present.||
|categories|An array of categories as listed on the card.|`"categories": ["X", "DFF"]`|
|jobs|An array of jobs as listed on the card.|`"jobs": ["Sky Pirate", "Viking"]`|
|rarity|The rarity as listed on the serial "C", "R", "H", "L", "S"|`"rarity": "H"`|
|cost|The cost to cast the card as displayed on the crystal of the card.|`"cost": 5`|
|elements|An array of elements of the card.|`"elements": ["Wind", "Fire"]`|
|type|The card type. "Forward", "Backup", "Monster", "Summon".|`"type": "Monster"`|
|isExBurst|`true` if the card is an ex burst. `false` if not.|`"isExBurst": false`|
|isMultiPlayable|`true` if the card is multiplayable. `false` if not.|`"isMultiPlayable": true`|
|isSpecial|`true` if the card has a special. `false` if not.|`"isSpecial": false`|

