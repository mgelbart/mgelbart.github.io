<div id="text"></div>
 
<script>
document.getElementById("text").innerHTML = "Text added by JavaScript code";
</script>
 
<script>
require('puzzlescript@3.0/lib/webpack-output')
</script>

<script>
engine = {
  // resize the table entry every time the level changes
  const eventHandler = {
    onLevelComplete: () => table.dispatchEvent(new CustomEvent("level-change"))
  }

  const engine = new PuzzleScript.TableEngine(table, eventHandler)
  engine.setGame(gameSource, 0)
  engine.start()
  
  eventHandler.onLevelComplete() // resize the table cell
  yield engine
}
</script>

<script>
gameSource = `title Line of Sight
author Joel Fox and Mike Gelbart
homepage www.puzzlescript.net

again_interval 0

========
OBJECTS
========

Background
LIGHTGREEN GREEN
11111
01111
11101
11111
10111

Wall
BROWN DARKBROWN
00010
11111
01000
11111
00010

Player
Black Orange White Purple
.000.
.111.
22222
.333.
.3.3.

Crate
Orange Yellow
00000
01110
01110
01110
00000

Glass
LightGray
00000
0...0
0...0
0...0
00000

MirrorForwardSlashFixed
DarkGray Lightgray
...01
..010
.010.
010..
10...

MirrorBackSlashFixed
DarkGray Lightgray
10...
010..
.010.
..010
...01

MirrorHorizontalFixed
DarkGray Lightgray
.....
00000
11111
00000
.....

MirrorVerticalFixed
DarkGray Lightgray
.010.
.010.
.010.
.010.
.010.


MirrorForwardSlashCanRotate
DarkGray Pink
...01
..010
.010.
010..
10...

MirrorBackSlashCanRotate
DarkGray Pink
10...
010..
.010.
..010
...01

MirrorHorizontalCanRotate
DarkGray Pink
.....
00000
11111
00000
.....

MirrorVerticalCanRotate
DarkGray Pink
.010.
.010.
.010.
.010.
.010.


Dude
white
.....
.....
.....
.....
.....

Checking
white
.....
.....
.....
.....
.....

Checked
white
.....
.....
.....
.....
.....

RayTracer
white
.....
.....
.....
.....
.....

Temp
white
.....
.....
.....
.....
.....

Gray
Gray
00000
0...0
0...0
0...0
00000

CanRotate
Pink
00000
0...0
0...0
0...0
00000

SeeLeftFixed
Black
.....
.....
000..
.....
.....


SeeRightFixed
Black
.....
.....
..000
.....
.....

SeeUpFixed
Black
..0..
..0..
..0..
.....
.....

SeeDownFixed
Black
.....
.....
..0..
..0..
..0..

SeeLeftCanRotate
Pink
.....
.....
000..
.....
.....


SeeRightCanRotate
Pink
.....
.....
..000
.....
.....

SeeUpCanRotate
Pink
..0..
..0..
..0..
.....
.....

SeeDownCanRotate
Pink
.....
.....
..0..
..0..
..0..


Satisfied
Blue
.....
.000.
.000.
.000.
.....

Unsatisfied
Red
.....
.000.
.000.
.000.
.....

=======
LEGEND
=======

. = Background
# = Wall
P = Player
* = Crate
G = Glass

SatisfiedDude = Dude and Satisfied
UnsatisfiedDude = Dude and Unsatisfied


Horiz = SeeLeftFixed and SeeRightFixed
Verti = SeeUpFixed and SeeDownFixed

Omni = Horiz and Verti

U = UnsatisfiedDude and Omni  (OmniDudeUnsatisfied)
S =   SatisfiedDude and Omni  (OmniDudeSatisfied)
H = UnsatisfiedDude and Horiz (HorizontalDudeUnsatisfied)
O =   SatisfiedDude and Horiz (HorizontalDudeSatisfied)
W = UnsatisfiedDude and Verti (VerticalDudeUnsatisfied)
E =   SatisfiedDude and Verti (VerticalDudeSatisfied)


1 = Gray and U (GrayOmniDudeUnsatisfied)
2 = Gray and S (GrayOmniDudeSatisfied)
3 = Gray and H (GrayHorizontalDudeUnsatisfied)
4 = Gray and O (GrayHorizontalDudeSatisfied)
5 = Gray and W (GrayVerticalDudeUnsatisfied)
6 = Gray and E (GrayVerticalDudeSatisfied)

HorizCanRotate = SeeLeftCanRotate and SeeRightCanRotate
VertiCanRotate = SeeUpCanRotate and SeeDownCanRotate


$ = UnsatisfiedDude and HorizCanRotate (CanRotateHorizontalDudeUnsatisfied)
% = Satisfied and HorizCanRotate (CanRotateHorizontalDudeSatisfied)
& = UnsatisfiedDude and VertiCanRotate (CanRotateVerticalDudeUnsatisfied)
+ = SatisfiedDude and VertiCanRotate (CanRotateVerticalDudeSatisfied)


r = UnsatisfiedDude and SeeRightFixed
i = satisfiedDude and SeeRightFixed
z = UnsatisfiedDude and SeeUpFixed
x = satisfiedDude and SeeUpFixed
d = UnsatisfiedDude and SeeDownFixed
n = satisfiedDude and SeeDownFixed
l = UnsatisfiedDude and SeeLeftFixed
f = satisfiedDude and SeeLeftFixed


0 = UnsatisfiedDude and SeeRightCanRotate
7 = satisfiedDude and SeeRightCanRotate
8 = UnsatisfiedDude and SeeUpCanRotate
9 = satisfiedDude and SeeUpCanRotate
£ = UnsatisfiedDude and SeeDownCanRotate
@ = satisfiedDude and SeeDownCanRotate
_ = UnsatisfiedDude and SeeLeftCanRotate
¢ = satisfiedDude and SeeLeftCanRotate


a = UnsatisfiedDude and SeeRightFixed and Gray
b = satisfiedDude and SeeRightFixed and Gray
c = UnsatisfiedDude and SeeUpFixed and Gray
j = satisfiedDude and SeeUpFixed and Gray
k = UnsatisfiedDude and SeeDownFixed and Gray
m = satisfiedDude and SeeDownFixed and Gray
q = UnsatisfiedDude and SeeLeftFixed and Gray
t = satisfiedDude and SeeLeftFixed and Gray

y = unsatisfieddude and SeeUpCanRotate and SeeDownCanRotate and gray
¡ = UnsatisfiedDude and SeeUpCanRotate and SeeDownCanRotate and SeeLeftCanRotate and gray


/ = MirrorForwardSlashFixed
\ = MirrorBackSlashFixed
- = MirrorHorizontalFixed
! = MirrorVerticalFixed

MirrorFixed = MirrorForwardSlashFixed or MirrorBackSlashFixed or MirrorHorizontalFixed or MirrorVerticalFixed
MirrorCanRotate = MirrorForwardSlashCanRotate or MirrorBackSlashCanRotate or MirrorHorizontalCanRotate or MirrorVerticalCanRotate

MirrorForwardSlash = MirrorForwardSlashFixed or MirrorForwardSlashCanRotate
MirrorBackSlash = MirrorBackSlashFixed or MirrorBackSlashCanRotate
MirrorHorizontal = MirrorHorizontalFixed or MirrorHorizontalCanRotate
MirrorVertical = MirrorVerticalFixed or MirrorVerticalCanRotate

Mirror = MirrorFixed or MirrorCanRotate

¤ = MirrorForwardSlashCanRotate
¥ = MirrorBackSlashCanRotate
¦ = MirrorHorizontalCanRotate
§ = MirrorVerticalCanRotate

Movable = Crate or Dude or Glass or Mirror
Opaque = Crate or Dude or Player or Wall

SeeUp = SeeUpFixed or SeeUpCanRotate
SeeDown = SeeDownFixed or SeeDownCanRotate
SeeLeft = SeeLeftFixed or SeeLeftCanRotate
SeeRight = SeeRightFixed or SeeRightCanRotate

HVMarker = SeeUp or SeeDown or SeeRight or SeeLeft
Marker = HVMarker or Unsatisfied or Satisfied or Gray or CanRotate


DudeCollision = Player or Wall or Crate or Glass or Dude or Mirror

=======
SOUNDS
=======

startgame 26858107
startlevel 34443107
endlevel 34292905

glass move 89482506
crate move 92869307
dude move 38810307
mirror move 96061307
Sfx0 8609109

================
COLLISIONLAYERS
================

Background
Player, Wall, Crate, Dude, Glass, Mirror

Checking
Checked
RayTracer
Temp

Satisfied, Unsatisfied
Gray
CanRotate
SeeLeft
SeeRight
SeeUp
SeeDown

======
RULES
======

[ > Player | Movable ] -> [ > Player | > Movable ]
[> Movable Marker | no DudeCollision] -> [> Movable > Marker | no DudeCollision]

(below: satisfied grey Towers cannot be moved) 
[> Gray > Satisfied > Dude > HVMarker] -> [> Gray > Satisfied > Dude HVMarker]
[> Gray > Satisfied > Dude HVMarker] -> [Gray Satisfied Dude HVMarker]


[action Player | Dude SeeUpCanRotate] -> [action Player | Dude Temp] Sfx0
[action Player | Dude SeeLeftCanRotate] -> [action Player | Dude SeeUpCanRotate] Sfx0
[action Player | Dude SeeDownCanRotate] -> [action Player | Dude SeeLeftCanRotate] Sfx0
[action Player | Dude SeeRightCanRotate] -> [action Player | Dude SeeDownCanRotate] Sfx0
[action Player | Dude Temp] -> [action Player | Dude SeeRightCanRotate] Sfx0


[action Player | MirrorHorizontalCanRotate] -> [action Player | Temp] Sfx0
[action Player | MirrorForwardSlashCanRotate] -> [action Player | MirrorHorizontalCanRotate] Sfx0
[action Player | MirrorVerticalCanRotate] -> [action Player | MirrorForwardSlashCanRotate] Sfx0
[action Player | MirrorBackSlashCanRotate] -> [action Player | MirrorVerticalCanRotate] Sfx0
[action Player | Temp] -> [action Player | MirrorBackSlashCanRotate] Sfx0



[moving Player] -> again (do another turn)
(reason for needing this instead of using "late": no movement allowed in late. and need movement to keep track of directionality of ray tracers. alternatively i guess one could have 4 types of ray tracers, one for each direction, but this is nicer.)

[Satisfied] -> [Unsatisfied]
startloop 
random [Dude no Checked] -> [Dude Checking]
left [SeeLeft Dude Checking | ] -> [SeeLeft Dude Checking | > RayTracer]
right [SeeRight Dude Checking | ] -> [SeeRight Dude Checking | > RayTracer]
up [SeeUp Dude Checking | ] -> [SeeUp Dude Checking | > RayTracer]
down [SeeDown Dude Checking | ] -> [SeeDown Dude Checking | > RayTracer]

(below: 6 lines for mirrors, one line for movement)
[up RayTracer MirrorForwardSlash] -> [RayTracer MirrorForwardSlash]
+[right RayTracer MirrorForwardSlash] -> [up RayTracer MirrorForwardSlash]
+[stationary RayTracer MirrorForwardSlash] -> [right RayTracer MirrorForwardSlash]
+[down RayTracer MirrorForwardSlash] -> [RayTracer MirrorForwardSlash]
+[left RayTracer MirrorForwardSlash] -> [down RayTracer MirrorForwardSlash]
+[stationary RayTracer MirrorForwardSlash] -> [left RayTracer MirrorForwardSlash]
+[up RayTracer MirrorBackSlash] -> [RayTracer MirrorBackSlash]
+[left RayTracer MirrorBackSlash] -> [up RayTracer MirrorBackSlash]
+[stationary RayTracer MirrorBackSlash] -> [left RayTracer MirrorBackSlash]
+[down RayTracer MirrorBackSlash] -> [RayTracer MirrorBackSlash]
+[right RayTracer MirrorBackSlash] -> [down RayTracer MirrorBackSlash]
+[stationary RayTracer MirrorBackSlash] -> [right RayTracer MirrorBackSlash]
+[up RayTracer MirrorHorizontal] -> [RayTracer MirrorHorizontal]
+[down RayTracer MirrorHorizontal] -> [up RayTracer MirrorHorizontal]
+[stationary RayTracer MirrorHorizontal] -> [down RayTracer MirrorHorizontal]
+[left RayTracer MirrorVertical] -> [RayTracer MirrorVertical]
+[right RayTracer MirrorVertical] -> [left RayTracer MirrorVertical]
+[stationary RayTracer MirrorVertical] -> [right RayTracer MirrorVertical]
+[> RayTracer no Opaque | no RayTracer ] -> [ | > RayTracer]
+[Raytracer Opaque no Dude] -> [Opaque no Dude]
+[Dude Unsatisfied Checking][RayTracer Dude] -> [Dude Satisfied Checked][Dude]
(
+[> RayTracer no Opaque | ] -> [> Temp no Opaque | ] 
+[RayTracer] -> []
+[> Temp] -> [> RayTracer]

note: the last 3 lines are for an insane corner case:
one ray stops at the edge of the level
and then another ray _from the same dude_ tries to pass through that ray in the orthogonal direction and 
the stationary one "wins" the collision, thus the other ray stops moving in
the direction it should be moving.
the fix works because when you move something into the edge of the level,
the movement token drops off.
how the fix works: the 3rd last line does not apply if you try to move off the level. So those ones don't get reborn.



another bug is that 2 rays hit a diagonal mirror at the same time from different angles, and one would get obliterated. this is fixed by the "no Raytracer" in the last line above that's not commented
)

(extra line above to kill off rays on opaque squares is only needed
because of the previous "no Raytracer" which is itself the bugfix descripbed above
-- without mirrors it's not needed
the fact that the last line is in the "+" instead of outside is for the same reason... otherwise it could be below ...
)


[Dude Checking] -> [Dude Checked]
[RayTracer] -> []
endloop 
[Checked] -> []

==============
WINCONDITIONS
==============

All Dude on Satisfied

=======	
LEVELS
=======

message A Tower turns blue if it has at least one other Tower in its line of sight (either vertical or horizontal). Goal: turn all red Towers blue.

message Level 1/30

######
#U...#
#..P.#
#..U.#
#.U..#
######
(difficulty: 1/5)

message Crates break the line of sight. Luckily they can be moved out of the way.
message Level 2/30

######
##U..#
U.*P.U
#....#
#.U..#
#U...#
######
(difficulty: 1/5)


message Level 3/30


######
#.U..#
#.*..#
#.PU.#
#.**.#
#.U###
######
(difficulty: 1/5)



message Level 4/20

#######
#.*...#
#.up#u#
#*#*..#
#.u.#.#
#.....#
#######
(difficulty: 2/5)


message Level 5/30

#######
#.U..##
#..UP.#
#..##.#
#.*U#.#
#.....#
#######
(difficulty: 2/5)`
</script>
