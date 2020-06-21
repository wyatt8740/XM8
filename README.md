# XM8

Personal fork of the real XM8 from [the author's site](http://retropc.net/pi/).

I have done little to alter the original code, except that my Linux machines
have a few peculiarities relating to SDL2 joysticks such that I had to modify
the original source to let me force using only a single attached controller.
I also had to make it choose my audio device differently - it was defaulting
to whatever the first audio device it enumerated was, but on my desktop
I have a sound card in addition to onboard audio, and the sound card is
enumerated after onboard is. I made SDL2 choose a reasonable default as
per its documentation instead of trying to do it manually (by passing NULL
as the device name). Now it plays nicely with other software and outputs to
the correct sound card.

I did this by making it so the environment variable `XM8_JOYSTICK` can be set
to an integer representing the number SDL2 assigns to a given pad. If my
controller is number 4 in SDL2 (I used [sdl-jstest](https://gitlab.com/sdl-jstest/sdl-jstest.git)
to check), then I'd set `XM8_JOYSTICK=4` when launching the emulator. All
other detected SDL pads will then be ignored. I think my screen's touch/pen
digitizer was interfering and making XM8 always detect d-pad presses.

The other change I made is to change the button ID's in XM8 so that my
Logitech "Dual Action" USB gamepad is seen with the buttons in the traditional
SNES-style layout, instead of being A/B swapped and then rotated 90 degrees.

Now I think I should be able to play "Ys: Ancient Ys Vanished Omen" in peace!

