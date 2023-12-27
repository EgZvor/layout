A keymap for 46 keys without mod-tap inspired by [Callum's layout](https://github.com/callum-oakley/qmk_firmware/tree/master/users/callum).

![](https://github.com/vim/vim/assets/11237935/f7e5e5b4-a7f9-42f0-82fa-c1973e78af68)

## Level layers

There are two layer keys: `SYMFN` (symbol + functional) and `NAVNUM` (navigation + numbers).
Pressing a key once activates the first layer.
Pressing the same key again (in another position on the keyboard) activates the second layer.
You can add more levels.
Pressing the same key more times than there are layers leaves you at the last layer.
Releasing one of those keys does **not** change the layer.
After you've released **all** keys the layers are cleared.
This builds on the idea in Callum's layout
that in order to save a key on a default layer
you need to go through a layer to get to the `NUM` one.

### Examples

1. Entering numbers

- Press `NAVNUM` with a left thumb
- Tap `NAVNUM` with a right thumb
- Use right hand for entering numbers
- Release `NAVNUM` with a left thumb

2. Shift+F3

- Press `SYMFN` with a right thumb
- Tap one-shot shift with a right middle finger
- Tap `SYMFN` with a left thumb
- Tap F3 with a left ring finger
- Release `SYMFN` with a right thumb

I don't usually hold shift.
If I need to press shift+f3 multiple times I use the `REPEAT` key.
When I need to repeat something a lot of times I alternate `REPEAT` between two hands.

### Time window for switching hands

This is a newer feature I've added
and it probably only makes sense with this exact layer configuration.

Since you only ever have to hold 1 of 2 layer keys for any of the 4 layers,
it means the following situation occurs often

- Press `SYMFN` with a right thumb
- Release `SYMFN` with a right thumb
- Press `NAVNUM` with a left thumb, **expecting a second `SYMFN`**
- Get recked

So I made it so that if you press `NAVNUM` fast enough after a last `SYMFN` press
(I use 50ms)
it is treated as `SYMFN` instead.

This, as any timer-based solution, has a downside.
Whenever I accidentally use a wrong thumb to activate a layer
or quickly decide that I need another layer
(`SYM` instead of `NUM`, for example).
This can happen

- Press `NAVNUM` (time: 0)
- Rethink your life choices
- Release `NAVNUM`
- Press `SYMFN`! (time: 0-50ms)
- It is treated as another `NAVNUM`, taking me to `NUM` instead of `SYM`

This doesn't seem like it happens too often, but I do encounter it
(or maybe another side-effect I'm not aware of).

### Switching hands keeping layer

Alternative idea was that jumping from one hand to another would **not** "level up" the layer.
This way you could stay on the same layer
and use a hand that's more comfortable for the next key to type (opposite one).
Immediate problem was that now there were two different behaviours attached to very similar movements:

1. left press, right press, left release (num)
2. left press, left release, right press (nav)

And I couldn't get rid of the first behaviour since then I would have no way to "level up" the layer.

## QWERTY default layer

I need it to type Cyrillic without messing with software layouts.
The macro `LANG` toggles between default layers
*and* taps software layout switching combination.
