# UE4 FText Localization

## Plural Forms
```
"There {NumCats}|plural(one=is,other=are) {NumCats} {NumCats}|plural(one=cat,other=cats)"
```
Will output: "There is 1 cat" or "There are 4 cats"

## Ordinal
```
"You came {Place}{Place}|ordinal(one=st,two=nd,few=rd,other=th)!"
```
Will output: "You finished 1st!" or "You finished 2nd!"

## More FText formatting examples [here](https://docs.unrealengine.com/en-US/ProductionPipelines/Localization/Formatting/index.html#pluralforms)

## Cool editor stuff (from [@_benui](https://twitter.com/_benui/status/1361197096276123651))
Easy way to find strings missing from localization in the editor:
Editor Prefs > Level Editor - Play > Additional Launch Parameters > "-leet"

All localized strings are changed to "l33t", unlocalized strings will look the same!

## Resources
- https://docs.unrealengine.com/en-US/ProductionPipelines/Localization/Formatting/index.html#pluralforms
