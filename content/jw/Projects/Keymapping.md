---
tags:
  - Customize
---


## Using Karbiner <- Current Using (macOS)


- https://karabiner-elements.pqrs.org
- https://ke-complex-modifications.pqrs.org/?q=caps%20lock%20command

## Using Keyd <- Current Using (Ubuntu)


### Starting Command lines
sudo systemctl enable keyd
sudo systemctl start keyd

### Config File
Location = /etc/keyd/default.conf

```conf
[ids]

*

[main]
# escape enter
# Maps capslock to escape when pressed and control when held.
capslock = overload(control, esc)

leftalt = overload(meta_mac, down)
rightalt = overload(meta_mac, up)

# Swap meta/alt
leftmeta = alt

space = overload(custom_space, space)

leftshift = overload(leftshift, left)
rightshift = overload(rightshift, right)


# Remaps the escape key to capslock
# esc = capslock

tab = overload(nav, tab)


[leftshift:S]
space = backspace
c = C

[rightshift:S]
space = delete


[nav]

h = left
k = up
j = down
l = right
# forward word
w = C-right
b = C-left



[control:C]
space = M-/

# Switch directly to an open tab (e.g. Firefox, VS code)
1 = A-1
2 = A-2
3 = A-3
4 = A-4
5 = A-5
6 = A-6
7 = A-7
8 = A-8
9 = A-9

# Copy
c = C-insert
# Paste
v = S-insert
# Cut
x = S-delete

# Move cursor to beginning of line
left = home
# Move cursor to end of Line
right = end

# As soon as tab is pressed (but not yet released), we switch to the
# "app_switch_state" overlay where we can handle Meta-Backtick differently.
# Also, send a 'M-tab' key tab before entering app_switch_state. 
tab = swapm(app_switch_state, M-tab)

` = A-f6

# app_switch_state modifier; inherits from 'Meta' modifier layer
[app_switch_state:M]
tab = M-tab
right = M-tab
` = M-S-tab
left = M-S-tab


[custom_space]
a = 1
s = 2
d = 3
f = 4
g = 5
h = 6
j = 7
k = 8
l = 9
; = 0

q = !
w = @
e = #
r = $
t = %
y = ^
u = &
i = *
o = (
p = )
n = _
m = =
, = -
. = +
```

### Keyd See More
- https://github.com/rvaiya/keyd