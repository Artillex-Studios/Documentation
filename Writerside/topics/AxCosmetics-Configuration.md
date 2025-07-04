# Configuration

## Armor cosmetics

An armor cosmetic's configuration looks like this by default. We'll go over what each of them do, and how you can
configure them.

```yaml
helmet:
  slot: "helmet"
  type: "armor"
  item-stack:
    material: "paper"
    custom-model-data: 1002

```

`helmet`: the name of the cosmetic, only one cosmetic is allowed by a name

`slot`: the slot of the armor cosmetic, can be helmet, chest_plate, leggings, boots, off_hand, main_hand

`type`: the type of the cosmetic, this is how we know which cosmetic type we need to use

`item-stack`: the item of the cosmetic, this can have all the different settings from
our [item builder](Item-Builder.md)

## Backpack cosmetics

A backpack cosmetic's configuration looks like this by default. We'll go over what each of them do, and how you can
configure them.

```yaml
backpack1:
  slot: "backpack"
  type: "backpack"
  item-stack:
    material: "paper"
    custom-model-data: 1002

```

`backpack1`: the name of the cosmetic, only one cosmetic is allowed by a name

`slot`: the slot of the armor cosmetic, can be backpack

`type`: the type of the cosmetic, this is how we know which cosmetic type we need to use

`item-stack`: the item of the cosmetic, this can have all the different settings from
our [item builder](Item-Builder.md)

## First-person backpack cosmetics

A first-person backpack cosmetic's configuration looks like this by default. We'll go over what each of them do, and how
you can configure them.

```yaml
backpack2:
  slot: "backpack"
  type: "first-person-backpack"
  height: 1.5
  item-stack:
    material: "paper"
    custom-model-data: 1000
  first-person-item-stack:
    material: "paper"
    custom-model-data: 11000

```

`backpack2`: the name of the cosmetic, only one cosmetic is allowed by a name

`slot`: the slot of the armor cosmetic, can be backpack

`type`: the type of the cosmetic, can be `first-person-backpack` or `legacy-first-person-backpack`, where
`first-person-backpack` uses interaction display entities
for elevating the cosmetic (not recommended if you allow users from versions older than 1.20.4), while
`legacy-first-person-backpack` uses area effect clouds

`height`: the height of the first-person backpack, this is limited to a whole number with `legacy-first-person-backpack`

`item-stack`: the item of the cosmetic, this can have all the different settings from
our [item builder](Item-Builder.md)

`first-person-item-stack`: the first-person item of the cosmetic, this is shown for the equipper, this can have all the
different settings from our [item builder](Item-Builder.md)