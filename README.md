# materiahunter-data

A repository of Final Fantasy Trading Card Game data, formatted for https://www.materiahunter.com

## Data Requirements
When adding new cards, there's a host of other information that needs to change along the way.

1. Card
2. Variants
3. Product Details

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
