# Datapacks

## **Note, this is a brief overview of datapacks. It will help you get started, but there are many, many more features and much is omitted in this question.**

> How do I create a datapack?

## What is a datapack?
A datapack is a collection of files that act as a sort of "vanilla mod", so to speak. These contain many useful features, one being **functions**. Functions are files that are literally lists of commands. But they're much easier than making a chain of command blocks, because, well, let's just say adding a new line in a text editor is easier than moving a whole 50 block chain. They also have a host of other advantages.

## How to make a datapack
Firstly, you'll need to find your world folder (datapacks are stored in each world separately). It's in `.minecraft/saves`. (If you don't know where your `.minecraft` is, look it up for your operating system). There's a folder in it called `datapacks`; this is where datapacks go. Create your datapack folder in here, call it whatever you like.

Next, we need to tell minecraft "THIS IS A DATAPACK". Create a file called `pack.mcmeta`, which will do this. It uses a json format, and quite a simple structure (you can copy-paste the following):
```json
{
    "pack": {
        "pack_format": 7,
        "description": "Insert description here"
    }
}
```
\* The pack format here is 7 which represents 1.17. If you're using 1.16, use 6. (Or even 1.18, hello future person, probably 8)

Great. Now create a folder called `data` inside the pack. This is where everything goes. Inside that, make another folder which is called the same as your namespace. Namespaces are used in identifiers; call it something relevant. Note it has to be in `snake_case`, so `cookie_pack` is okay, `cookiepack` is okay, `Cookie Pack` is definitely not okay.

Inside your namespace is where various different folders go. One of these is `functions`. Make this folder. Finally, we can make a function. Functions are files with a `.mcfunction` extension. Make your file, add some commands, and you're ready to go!

> Note that commands in a function **cannot be written with a slash in front**

## Loading the datapack
Go into your world, and run `/reload`. Great! You can now run `/function namespace:function`.

## I'm still confused.
I'm not the best at wording, but there are plenty things you can do. Check [the wiki](https://minecraft.gamepedia.com/Datapack) which contains everything you need to know about datapacks. You can also find generators online, like [Misode's](https://misode.github.io).

And of course, ask away in discord!