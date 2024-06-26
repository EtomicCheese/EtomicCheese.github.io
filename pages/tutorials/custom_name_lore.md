# `custom_name & lore`

## Index

- [`custom_name & lore`](#custom_name--lore)
  - [Index](#index)
    - [Introduction](#introduction)
  - [Custom Name](#custom-name)
    - [Text](#text)
    - [Italic](#italic)
    - [Colors](#colors)
    - [Format](#format)
    - [Styles](#styles)
    - [Multiple Texts](#multiple-texts)
    - [Extra](#extra)
  - [Lore](#lore)
    - [Conclusion](#conclusion)

---

### Introduction

As of Minecraft 1.20.5, the `custom_name` component is to replace the old `display` tag used to change the visual name and lore of the item or block. The following commands will not work in versions of Minecraft older than 1.20.5 on the Java Edition of the game. The same goes with the `lore` component.

---

## Custom Name

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

---

### Text

Now that we have the component set up, we can now add some text.

```json
give @p minecraft:sponge[custom_name='{text: "Cheese"}']
```

First we specify `text`, then we make `text` contain the word `"Cheese"` but putting the word inside quotations `""`.

---

### Italic

Of course we can create additional information to the text. Currently the text is slanted, meaning that by default without any additional information, Minecraft is making the text slanted. This is the default because it inherits the same concept from naming items with the nametag in an anvil. But unlike an anvil, we have a command block, so we are going to change things up a bit.

Let's set `italic` from `true` to `false`.

```json
give @p minecraft:sponge[custom_name='{text: "Cheese",italic: false}']
```

You can see that we added a comma `,` after `"Cheese"`. Usually you have a component, then you have the component's value. In this case, the `text` component contains `"Cheese"`. Since we can add a second component, we add a comma `,` and write down `italic`. Unlike `text`, `italic` doesn't contain text, rather it contains the words `true` or `false`. In this case, `italic` is set to `false` so that the text isn't slanted.

---

### Colors

Since italic is a style, there are many styles like `bold`, `underlined`, `strikethrough` etc. We will do those later but first, let's change the color of the text.

```json
give @p minecraft:sponge[custom_name='{text: "Cheese", italic: false, color: gold}']
```

After adding a comma `,` after `italic: false`, we add `color`, and `color` contains `gold`.

Minecraft comes with many colors you can use. Here is a list of them all:

|Color|Hex|
|---|---|
|black|#000000|
|dark_blue|#0000a8|
|dark_green|#00a800|
|dark_aqua|#00a8a8|
|dark_red|#a80000|
|dark_purple|#a800a8|
|gold|#fca800|
|gray|#a8a8a8|
|dark_gray|#545454|
|blue|#5454fc|
|green|#54fc54|
|aqua|#54fcfc|
|red|#fc5454|
|light_purple|#fc54fc|
|yellow|#fcfc54|
|white|#fcfcfc|

As you can see, there are also hex codes. These codes allow you to not only add colors that Minecraft provides by default, but it allows you to display any color depending on the hex code.

Here is a command with the example of a working color hex code.

```json
give @p minecraft:sponge[custom_name='{text: "Cheese", italic: false, color: "#8cffcb"}']
```

You can simply generate these custom hex codes by simply going to google and searching "color picker", or if you are using Paint\.net, Gimp, or Photoshop, you can copy a hex code there from their built in color pickers.

---

### Format

From this point onwards, the Minecraft commands we are making are all on a single line, and as the command increases in complexity, we won't be able to properly read the code. To increase readability for this documentation, I will instead be using multiple lines to explain the code.

So instead of this:

```json
give @p minecraft:sponge[custom_name='{text: "Cheese", italic: false, color: "#8cffcb"}']
```

I'll do this instead:

```json
give @p minecraft:sponge[
    custom_name='
        {
            text: "Cheese",
            italic: false,
            color: "#8cffcb"
        }
    '
]
```

This doesn't break the code, it simply displays it in a better way.

This will still work inside minecraft's single line of code but there will be many spaces in the lines. So after every example block of code, I'll provide the single line version.

---

### Styles

There are a few styles in Minecraft that can add some variation to the text being displayed.

Here is a list of all the styles you can use.

- italic
- bold
- underlined
- strikethrough
- obfuscated

And the nice thing is, all styles can be enabled all at the same time, you just have to list them all.

So let's add these styles together, except for obfuscated because that wouldn't be very readable.

```json
give @p minecraft:sponge[
    custom_name='
        {
            text: "Cheese",
            italic: true,
            color: "#8cffcb",
            bold: true,
            underlined: true,
            strikethrough: true
        }
    '
]
```

```json
give @p minecraft:sponge[custom_name='{text: "Cheese", italic: true, color: "#8cffcb", bold: true, underlined: true, strikethrough: true}']
```

Now the item contains every style besides `obfuscated`. With `obfuscated` set to `true`, this will make the text cycle through every character in Minecraft from the english letters to letters with accents to numbers and everything else in between. Of course that does imply that you cannot read the text anymore.

Here it is with `obfuscated` added in.

```json
give @p minecraft:sponge[
    custom_name='
        {
            text: "Cheese",
            italic: true,
            color: "#8cffcb",
            bold: true,
            underlined: true,
            strikethrough: true,
            obfuscated: true
        }
    '
]
```

```json
give @p minecraft:sponge[custom_name='{text: "Cheese", italic: true, color: "#8cffcb", bold: true, underlined: true, strikethrough: true, obfuscated: true}']
```

---

### Multiple Texts

As mentioned before, when you add square brackets `[]`, it's telling the game that you can have multiple components and objects `{}`. This means that the object `{}` that contains our text, colors, and styles, can have a neighbor! We can add a second text object `{}` after the first one as long as both objects are surrounded by the square brackets `[]`. Here is an example.

```json
give @p minecraft:sponge[
    custom_name='[
            {
                text: "Cheese",
                italic: true,
                color: "#8cffcb",
                bold: true,
                underlined: true,
                strikethrough: true,
                obfuscated: true
            }
        ]
    '
]
```

```json
give @p minecraft:sponge[custom_name='[{text: "Cheese", italic: true, color: "#8cffcb", bold: true, underlined: true, strikethrough: true, obfuscated: true}]']
```

Just after the component `custom_name`, we can see that within the hyphens `''` that the code starts with a square bracket instead of a curly bracket. With this we can add as many text objects as we want, and so we can add in a second one.

So here is an example with `obfuscated` set to `false` because I would like to read what I write.

```json
give @p minecraft:sponge[
    custom_name='
        [
            {
                text: "Cheese, ",
                italic: true,
                color: "#8cffcb",
                bold: true,
                underlined: true,
                strikethrough: true,
                obfuscated: false
            },
            {
                text: "the greatest thing ever"
            }
        ]
    '
]
```

```json
give @p minecraft:sponge[custom_name='[{text: "Cheese, ", italic: true, color: "#8cffcb", bold: true, underlined: true, strikethrough: true, obfuscated: false},{text: "the greatest thing ever"}]']
```

Here are two text objects. One contains the word `"Cheese, "` with that space and comma to make it look nicer, and the other object contains nothing else but text. This means that since the second text object doesn't specify that it is bold, italic or any other style, it will inherit those values from the first text object. This means that if we want the second text object to have a different color or even a different set of styles, we need to specify them in the second text object.

Let's make the second text object `gold`, and let's set the `strikethrough`, `italic` and `bold` to `false`.

```json
give @p minecraft:sponge[
    custom_name='
        [
            {
                text: "Cheese, ",
                italic: true,
                color: "#8cffcb",
                bold: true,
                underlined: true,
                strikethrough: true,
                obfuscated: false
            },
            {
                text: "the greatest thing ever",
                color: gold,
                italic: false,
                bold: false,
                strikethrough: false
            }
        ]
    '
]
```

```json
give @p minecraft:sponge[custom_name='[{text: "Cheese, ", italic: true, color: "#8cffcb", bold: true, underlined: true, strikethrough: true, obfuscated: false},{text: "the greatest thing ever",color: gold,italic: false,bold: false,strikethrough: false}]']
```

You can see that the underlines are still there because we didn't specify them to be false in the second text object.

---

### Extra

As it is true that you can add as many text objects as you want, you can also have a text object inside another text object instead of having square brackets containing both text objects.

Let's create an entirely new block of code to work with since the last one is getting a little large.

```json
give @p minecraft:paper[
    custom_name='{
        text: "Hello, World!"
    }'
]
```

```json
give @p minecraft:paper[custom_name='{text: "Hello, World!"}']
```

This will simply give you a piece of paper saying `Hello, World!`. Now just like `color` and `bold`, `italic`, `obfuscated` etc. We can add in a new thing called `extra`. This is just like having a second text object, except it's inside another text object. `extra` requires square brackets to work.

```json
give @p minecraft:paper[
    custom_name='{
        text: "Hello, World!",
        extra: [
            {
                text: " Extra Extra!"
            }
        ]
    }'
]
```

```json
give @p minecraft:paper[custom_name='{text: "Hello, World!",extra:[{text: " Extra Extra!"}]}']
```

As you know, there are square brackets, so you are quite able to create another text object inside the initial `extra` piece.

```json
give @p minecraft:paper[
    custom_name='{
        text: "Hello, World!",
        extra: [
            {
                text: " Extra Extra!"
            },
            {
                text: " Even More Extra!"
            }
        ]
    }'
]
```

```json
give @p minecraft:paper[custom_name='{text: "Hello, World!",extra:[{text: " Extra Extra!"},{text: " Even More Extra!"}]}']
```

And since `extra` can contain multiple string objects, and since you have to put `extra` in a string object in order to use it, you can have an extra inside another extra.

```json
give @p minecraft:paper[
    custom_name='{
        text: "Hello, World!",
        extra: [
            {
                text: " Extra Extra!"
            },
            {
                text: " Even More Extra!",
                extra: [
                    {
                        text: " Ok this is getting a little long now"
                    }
                ]
            }
        ]
    }'
]
```

```json
give @p minecraft:paper[custom_name='{text: "Hello, World!",extra:[{text: " Extra Extra!"},{text: " Even More Extra!",extra:[{text: " Ok this is getting a little long now"}]}]}']
```

And just like text objects inheriting the styles from the previous text object, you can define a color at the very top and the rest of the text objects below that will inherit the color.

```json
give @p minecraft:paper[
    custom_name='{
        text: "Hello, World!",
        color: gold,
        extra: [
            {
                text: " Extra Extra!"
            },
            {
                text: " Even More Extra!",
                extra: [
                    {
                        text: " Ok this is getting a little long now"
                    }
                ]
            }
        ]
    }'
]
```

```json
give @p minecraft:paper[custom_name='{text: "Hello, World!",color:gold,extra:[{text: " Extra Extra!"},{text: " Even More Extra!",extra:[{text: " Ok this is getting a little long now"}]}]}']
```

Though it is not recommended to code like this since having nested objects tends to become difficult to comprehend if your not too careful.

---

## Lore

Just like how you can add custom names to your items and blocks with customized colors and styles, you are also able to create custom descriptions for your items and blocks.

But unlike the default `custom_name` component, the `lore` component can contain multiple lines of text rather than just a single line. This is quite useful if you want to add multiline descriptions of your item.

The code in the `lore` component is not too difficult compared to the `custom_name` component as they use the exact same text format with some key differences that aren't too difficult to understand.

Firstly, let's add the lore component to the item.

Since `minecraft:sponge` opens up to square brackets, this implies that you can have multiple components active at the same time. Which means you can have both `custom_name` and `lore` on the same item at once.

```json
minecraft:sponge[custom_name='{}',lore=['{}']]
```

You can see that `custom_name` uses hyphens `''` to indicate that the code inside displays text. Lore however first creates square brackets, then hyphens. This means you can have multiple texts. Specifically multiple lines of text. That means we can have lore on three different lines if we do this.

```json
minecraft:sponge[lore=['{}','{}','{}']]
```

Here we can have three text objects on three different lines!

Now let's make a practical command that functions in the game itself.

```json
give @p minecraft:sponge[
    custom_name='{
        text: "This is a Name"
    }',
    lore=[
        '{
            text: "This is Lore"
        }',
        '{
            text: "This is another line of Lore"
        }'
    ]
]
```

```json
give @p minecraft:sponge[custom_name='{text: "This is a Name"}',lore=['{text: "This is Lore"}','{text: "This is another line of Lore"}']]
```

To break it down, `lore` doesn't seem too different from `custom_name`. You can add styles, your own colors just like `custom_name`.

And just like before where you can have multiple styles and colors on a single line, you use square brackets in between the hyphens in order to have multiple text objects on a single line.

For instance if we had two lines:

```json
lore=['{}','{}']
```

adding more than one text object for a single line is fairly easy:

```json
lore=['[{},{},{}]','[{},{},{}]']
```

So there we go, two lines with three text objects, rather simple.

And that is all there is to it. You can apply all that you have learned in the `custom_name` component and apply it here, except of course, you can have more than one entire line to work with.

---

### Conclusion

And that is everything you need to know, or rather everything you can possibly know about the `custom_name` component! *(And the `lore` component)*. At the time of writing this, no video has been published yet, but one will come soon.

---

*This document was written by [Etomic](https://www.youtube.com/EtomicStudios)*
