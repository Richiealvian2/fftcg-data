# materiahunter-data

A repository of Final Fantasy Trading Card Game data, formatted for https://www.materiahunter.com

# Creating Cards
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


### Ability Text
Ability text has special markup that gets replaced when it's rendered on materiahunter.

|style|example|
|-|-|
|bold text|`*this is bold text*`|
|italic text|`~this is italic text~`|
|ex burst label|`{x}`|
|special icon|`{s}`|
|special text|`%kamehameha%`|
|crystal|`{c}`|
|elementless cp cost|`{0-10}`|
|fire cp|`{f}`|
|ice cp|`{i}`|
|wind cp|`{w}`|
|earth cp|`{e}`|
|lightning cp|`{l}`|
|water cp|`{a}`|
|dull icon|`{d}`|


