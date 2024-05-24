# `custom_name`

As of Minecraft 1.20.5, the `custom_name` component is to replace the old `display` tag used to change the visual name and lore of the item or block.

First you must give yourself an item or block to store into your inventory.

```json
give @p minecraft:sponge
```

This will give you a single sponge block.
In order to add the `custom_name` component to the sponge, we must put it inside square brackets just after the sponge.

```json
give @p minecraft:sponge[]
```

The square brackets `[]` are typically known for telling the game that there can be more than one component.

```json
give @p minecraft:sponge[custom_name='{}']
```

Unlike other components, the `custom_name` component doesn't just open up to curly brackets `{}`, but instead it first opens to hyphens `''` and then it opens to the curly brackets `{}`. The hyphens tell minecraft that the information contained inside the `custom_name` component is going to display text.

Just for some additional information regarding the curly brackets `{}`, we call those objects. If you have square brackets `[]`, then you can have multiple objects `{}`.

Now that we have the component set up, we can now add some text.

```json
give @p minecraft:sponge[custom_name='{text: "Cheese"}']
```

First we specify `text`, then we make `text` contain the word `"Cheese"` but putting the word inside quotations `""`.

Of course we can create additional information to the text. Currently the text is slanted, meaning that by default without any additional information, Minecraft is making the text slanted. This is the default because it inherits the same concept from naming items with the nametag in an anvil. But unlike an anvil, we have a command block, so we are going to change things up a bit.

Let's set `italic` from `true` to `false`.

```json
give @p minecraft:sponge[custom_name='{text:"Cheese",italic:false}']
```

You can see that we added a comma `,` after `"Cheese"`. Usually you have a component, then you have the component's value. In this case, the `text` component contains `"Cheese"`. Since we can add a second component, we add a comma `,` and write down `italic`. Unlike `text`, `italic` doesn't contain text, rather it contains the words `true` or `false`. In this case, `italic` is set to `false` so that the text isn't slanted.

Since italic is a style, there are many styles like `bold`, `underlined`, `strikethrough` etc. We will do those later but first, let's change the color of the text.

