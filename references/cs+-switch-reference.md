# CS+KAGE reference

{% hint style="warning" %}
The information on this page regarding the engine's capabilities may be wildly outdated, and only gets more outdated as the years go by.
{% endhint %}

doukutsu-rs has partial support for data files and some of the features included with [2017 Switch-exclusive release of Cave Story+](https://www.nicalis.com/games/cavestory+). Due to multiple technical and gameplay changes this page exists to gather all knowledge about it in one place.&#x20;

At time of writing this the reworked release of CS+ has been only released on Nintendo Switch, so if you want to use it with d-rs you need a hacked console to dump the `data` directory from romfs and transfer it to PC.

We call it "CS+KAGE" version since there's a possibility of future ports appearing and it's likely that they will share the same codebase and data file layout as the currently available Switch version (as seen by Binding of Isaac and other games using the same framework).

![](<../.gitbook/assets/image (11).png>)

![](<../.gitbook/assets/image (16).png>)

![](<../.gitbook/assets/image (7).png>)

### Important notes

* All support for Switch CS+ is based on [clean room reverse engineering](https://en.wikipedia.org/wiki/Clean_room_design) and black-box reverse engineering (modifying data files and looking what happens), based on references created by various people listed below.
* None of doukutsu-rs contributors/developers has seen any code implementing those features in form of sources or disassembly.
* There's some stuff that CS+ Switch adds as well (eg. lighting effects, co-op), but those are implemented using completely original ways (and code), for different purposes and used the Switch release as inspiration at most.

### TSC behavior details - by @periwinkle on Discord

> This is what I was able to gather about the TSC commands used in CS+ Switch that aren't in freeware. I think you already know most of this but I also wanted to double-check that your clean-room observations aren't totally contradictory to what I have, in case I screwed up/misinterpreted something:
>
> ```
> <I+Nxxxx:yyyy   Adds 1 of item xxxx, with a max quantity of yyyy
> <2MVxxxx        Moves the other player to the player that triggered this event. Also generates 4 smoke entities at that location
>                 if xxxx < 11, the other player is moved to one block away from this player.
>                 Otherwise, the other player is moved to int(xxxx / 10) pixels away from this player.
>                 If xxxx ends in 1, the other player is moved to the right side of this player; otherwise they are moved to the left side.
> <HM2            Hides only the player that triggered this event (unlike <HMC, which hides both)
> <FF-xxxx:yyyy   Unsets the first set flag in the range [xxxx:yyyy]
> <KE2            Used in the inventory; sets g_GameFlags |= 0x11:
>                 Flag 0x10 prevents the OK button from restarting the item description event (resets when the cursor is moved)
>                 (it does not prevent the cancel button from exiting the inventory, however)
> <FR2            Sets g_GameFlags &= ~0x11 and g_GameFlags |= 1 (see above)
> <2PJxxxx        Jump to event xxxx if P2 is active
> <INJxxxx:yyyy:zzzz     Jump to event zzzz if player has at least yyyy quantity of item xxxx
> <POP            Event stack pop; restores read position from top of event stack
> <PSHxxxx        Event stack push; saves the current read position (after this command) to a stack and then jumps to event xxxx.
>                 (Note: CS+ Switch supports a max of 32 events on the stack)
> <ACHxxxx        Get achievement xxxx (whatever that means)
> ```
>
> Additionally, there are 3 2 other commands that exist but aren't used anywhere (I think). I could tell you about them but given that they're not used, there's probably no need for you to implement them ![:stuck\_out\_tongue:](https://discord.com/assets/10f25947b6687b5b103e131ca82826ab.svg)

later errata:

> Apparently I had written down at one point that `<2MV` resets the air of the player that movesNot sure if you had found that out already from testing(if not, maybe it's worth double-checking just to be sure)

### @Alula's original TSC notes derived from context analysis of data files.

> ```
> // ---- Cave Story+ (Switch) specific opcodes ----
> /// <HM2, HMC for non-executor player??
> HM2,
> /// <2MVxxxx, Put another player near the player who executed the event.
> /// 0000 - puts player on left side of executor player
> /// 0001 - puts player on right side of executor player
> /// other values - Unknown purpose for now
> #[strum(serialize = "2MV")]
> S2MV,
> /// <INJxxxx:yyyy:zzzz, Jumps to event zzzz if amount of item xxxx equals yyyy
> INJ,
> /// <I+Nxxxx:yyyy, Adds item xxxx with maximum amount of yyyy
> #[strum(serialize = "I+N")]
> IpN,
> /// <FF-xxxx:yyyy, Set flags in range xxxx-yyyy to false
> #[strum(serialize = "FF-")]
> FFm,
> /// <PSHxxxx, Pushes text script state to stack and starts event xxxx
> PSH,
> /// <POP, Restores text script state from stack and resumes previous event.
> POP,
> /// <KEY related to player 2?
> KE2,
> /// <FRE related to player 2?
> FR2,
> ```

### New background types

* 8 - variant of Outside - doesn't seem to be used anywhere in stage.tbl or any mod but we suspect it's a special type for menu background. Peri mentioned the only difference is some lighting setup code but lighting is disabled on every outside background type so we dunno.
* 9 - variant of type 2 (tiled background with background scrolling with tilemap, without parallax) - the only difference is that `bkCircle2` texture is drawn behind the water.

![](<../.gitbook/assets/image (12).png>)

![](<../.gitbook/assets/image (22).png>)

![](<../.gitbook/assets/image (5).png>)

![](<../.gitbook/assets/image (4).png>)

![](<../.gitbook/assets/image (10).png>)

### Water notes

Judging by behavior, the technique used to implement water seems to be something similar to technique described there: [https://prime31.github.io/water2d-part1/](https://prime31.github.io/water2d-part1/)

CS+ renders the water on entire area spanned by tiles with water attribute set, there's no clipping to shape of actual water tilemap.

![](<../.gitbook/assets/image (25).png>)

![](<../.gitbook/assets/image (21).png>)

![](<../.gitbook/assets/image (24).png>)

### .pxw file format

Reworked CS+ added a new "water attribute" file as one of tileset metadata files.&#x20;

Every tileset, except the Last Cave one (it has lava / blood water pools) seems to use the same values.

The format seems to be something like this, can be specified multiple times on separate lines:

```
0:255:[255, 0, 0, 150]:[0, 255, 0, 75]:[0, 0, 255, 75]
```

* First and second fields specify the range of tiles the color should be applied to.
* 3rd field is the color of top water edge.
* 4th field is the middle color of water gradient
* 5th field is the color of bottom water edge.

Putting above example data in .pxw file results in something like:

![](<../.gitbook/assets/image (17).png>)
