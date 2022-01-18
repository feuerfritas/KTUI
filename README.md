# KT Command Node UI Extender
Kill Team Command Node UI Extender - A tool to improve KT Command Node UI experience

## Credits
* [MoonkeyMod](https://steamcommunity.com/id/moonkey2010) for creating the [KT Map Base Table](https://steamcommunity.com/sharedfiles/filedetails/?id=2574389665)
* [Focks](https://steamcommunity.com/id/zeuglinredux) for creating [KT Command Node](https://steamcommunity.com/sharedfiles/filedetails/?id=2614731381&searchtext=Command+node)
* [Rebelson666](https://discordapp.com/users/330047329988116480) for making the graphics

## How to create
* [One-sided tokens](#one-sided-tokens)
* [One-sided advanced tokens](#one-sided-advanced-tokens)
* [Simple equipment tokens](#simple-equipment-tokens)
* [Two-sided tokens](#two-sided-tokens)
* [Bundling tokens together](#bundling-tokens-together)
* [Reserved names](#reserved-names)

The following are instructions for mod makers, please simply ignore these instructions:
* [Order tokens](#order-tokens)

## One-sided tokens
* Spawn a `Token` item (`Objects > Components > Custom > Token`)
* If you want the miniature to count how many tokens of the same kind have been applied to it, check the `Stackable` option
* Add the url of the token's `Image` and click on `Import`
* Right click on the newly created token then access the `Tags` menu voice and add a new tag called `KTUITokenSimple` or highlight it from the list if already present
* Right click on the token add give it a unique description that doesn't contain any spaces or new lines and nothing else. Please refer to [Reserved names](#reserved-names) to check a list of already reserved names
* You can also give it a fancy name but it's not mandatory
```
Name: Minus 1
Description: Minus_1_blue
```

## One-sided advanced tokens
* Spawn a `Token` item (`Objects > Components > Custom > Token`)
* If you want the miniature to count how many tokens of the same kind have been applied to it, check the `Stackable` option
* Add the url of the token's `Image` and click on `Import`
* Right click on the newly created token then access the `Tags` menu voice and add a new tag called `KTUITokenAdvanced` or highlight it from the list if already present
* Right click on the token and go under `Scripting > Scripting Editor`, then copy the whole [SingleSidedAdvancedToken.lua](https://github.com/nyirsh/KTUI/blob/main/Scripts/SingleSidedAdvancedToken.lua) and paste it into your model's script.
* In the first lines of the script change the values of both `face_settings` to match your token's visuals

`name`: a unique description that doesn't contain any spaces or new lines and nothing else. Please refer to [Reserved names](#reserved-names) to check a list of already reserved names

`url`: url of the image used to represent the token's face

`removable`: if set to `false`, after being attached to the miniature it can't be removed by any means (useful for permanent equipments)

`stackable`: if set to `true`, the miniature will count how many tokens of the same kind have been applied to it

`secret`: if set to `true` makes the token only visible to the miniature's owner, after being applied to it, until it is clicked on. Useful for secret roles specific tokens (ie. Interloper). It will also override `removable`, `stackable` and `equipment` to `false`.

`equipment`: if set to `true` makes the token will be considered as an equipment one. It will also override `stackable` to `false`.

## Simple equipment tokens
* Spawn a `Token` item (`Objects > Components > Custom > Token`)
* Add the url of the token's `Image` and click on `Import`
* Right click on the newly created token then access the `Tags` menu voice and add a new tag called `KTUITokenEquipment` or highlight it from the list if already present
* Right click on the token add give it a unique description that doesn't contain any spaces or new lines and nothing else. Please refer to [Reserved names](#reserved-names) to check a list of already reserved names
* You can also give it a fancy name but it's not mandatory
```
Name: Climbing Rope
Description: Kommando_EQ_Climbing_Rope
```
Please be aware that any token created with this method will have the `removable` parameter automatically set to `false`, it is therefore better to use an [One-sided advanced tokens](#one-sided-advanced-tokens) if you're creating a "Limited" kind of equipment.

## Two-sided tokens
Please refrain from creating tokens this way if you're not familiar on how to import custom models or how the TTS scripts work
* Import your token's `Custom Model` to TTS (please refer to guides on how to create and import your own custom models)
* Right click on the newly created token then access the `Tags` menu voice and add a new tag called `KTUITokenAdvanced` or highlight it from the list if already present
* Right click on the token and go under `Scripting > Scripting Editor`, then copy the whole [TwoSidedToken.lua](https://github.com/nyirsh/KTUI/blob/main/Scripts/TwoSidedToken.lua) and paste it into your model's script.
* In the first lines of the script change the values of both `face_up_settings` and `face_down_settings` to match your token's visuals

`name`: a unique description that doesn't contain any spaces or new lines and nothing else. Please refer to [Reserved names](#reserved-names) to check a list of already reserved names

`url`: url of the image used to represent the token's face

`removable`: if set to `false`, after being attached to the miniature it can't be removed by any means (useful for permanent equipments)

`stackable`: if set to `true`, the miniature will count how many tokens of the same kind have been applied to it

`secret`: if set to `true` makes the token only visible to the miniature's owner, after being applied to it, until it is clicked on. Useful for secret roles specific tokens (ie. Interloper). It will also override `removable`, `stackable` and `equipment` to `false`.

`equipment`: if set to `true` makes the token will be considered as an equipment one. It will also override `stackable` to `false`.

* If the token is not recognizing the right face completely (so it's not like face up and face down are mixed up), try to re-import your model from scratch and change the value of `face_coordinate` to a different one before experimenting with `face_up_limit` too

## Bundling tokens together
If you wish it is also possible to bundle all the tokens up into a single state-driven token. To do so, make sure that all the tokens you're about to bundle up together have the proper tags / scripts / descriptions before merging them all together in the same state

## Reserved names
Please do not use, under any circumstances, the following names/descriptions for your tokens:
* Engage_ready
* Engage_activated
* Conceal_ready
* Conceal_activated
* wound
* Minus_1_blue
* Minus_1_red
* Plus_1_blue
* Plus_1_red
* Exclamation_blue
* Exclamation_red
* Crosshair_blue
* Crosshair_red

--------------------------------------

## Order tokens
* Spawn a non-stackable `Token` item (`Objects > Components > Custom > Token`)
* Add the url of the token's `Image` and click on `Import`
* Right click on the newly created token then access the `Tags` menu voice and add a new tag called `KTUITokenOrder` or highlight it from the list if already present
* Right click on the token add give it any of these descriptions: `Engage_ready`, `Engage_activated`, `Conceal_ready`, `Conceal_activated`
* You can also give it a fancy name but it's not mandatory
