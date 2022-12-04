04/12/2022

What I've done is recorded myself playing through the 1st section of The Great Wall.
This is SPECIFICALLY the section of the level where -
Node 0 = beginning of level
Node X = the "splash" sound of Lara hitting the water, once she has dropped through the grate
at the top of the first climb

Right away there's something very key.
I have had to choose Node X, in a manner that relates to a specific game event.
This could also have been "the grate popping open with the correct sound".

However, I should keep this in mind, and see whether other Nodes need to adhere to the same
principle, of a clearly marked "game event".

So the happy route through this part is (without defining any nodes)

0) Begin,
1) Jump twice on the slidey ledges,
2) Kick-flip up onto the block,
3) Jump across and hitch up,
4) Turn around, jump across, hitch up,
5) Banana-jump, grab and lift,
6) Slidey banana-jump straight onto the top ledge,
7) Jump to the grate and bonk the wall, fall down.

Make notes about each attempt, did it diverge? Is it valid? If so, which parts and why?

Also the total time.

Summary of below here!

33      total runs
2       scrapped due to me losing patience and killing the tiger
16      HPs
8       SUs at Point 5
10      SUs at Point 6 type 1 (slide down forwards)
4       SUs at Point 6 type 2 (got to try jump again)

What do you think you should do with these stats?

It seems like there are 2 major SUs and 1 minor SU to consider.
How about just the 1st 2?

SUs at Point 5
Earliest good place to "rejoin" the initial path would be when you finish Point 3
(because you can coordinate based on sounds of e.g. Lara pulling up)

SUs at Point 6 type 1
Using the fix to jump forwards and right, you land back on the finish of Point 3,
but it's difficult to coordinate

Using these 2 points, the "best" rejoin point would be when Lara's feet touch the
platform on the "Jump across" of Point 4

Before I go any further (stick with this for now), I think I've had an idea that
could work out well.

This idea you're having, about nodes and paths, it's good, BUT I can see it getting
incredibly messy very quickly.

For example, here you are modelling the results of errors, which involve you
having to "partition" the routes in particular ways.
But then, what if say, another route appears, that requires you to "re-partition"?
Well then I guess you would have to re-run simulations and recalculate.

So yes, in other words, it COULD get very messy.
New partitions could be sub-classes of existing partitions, or they could completely
scrap existing partitions.

Your choice of partitions needs to be clever and in some-way "future proofed".
Where possible. Hmm.

Its your choice of node really.

Candidates are...

1) where Lara jumps across again on Point 4 (covers all failure paths), BUT
it is likely you'll be exploring alternate ways of getting to the "hitch up" at
the end of Point 4
This means you should look for a further point that encompasses this and all these.
2) The banana-jump on Point 5
I think this is good.

Attempt #   File Name     Video start time      Total time
1           GOPRO290      01:08                 01:34:02            DONE
2                         03:09                 00:42:34            DONE
3                         04:16                 00:49:76            DONE
4                         05:31                 00:40:00            DONE
5                         06:30                 00:44:74            DONE
6                         07:40                 01:04:80            DONE
7           GOPRO291      00:00                 00:37:80
8                         01:10                 01:13:08    
9                         02:47                 01:46:04  
10                        04:58                 00:37:92
11                        06:00                 00:37:78 
12                        07:00                 00:38:52   
13                        08:10                 00:41:00 + 00:14:00 = 00:55      * spreads into file GP010291
14          GP010291      00:31                 01:42:21
15                        02:40                 00:38:08
16                        03:50                 00:39:05
17                        04:50                 00:40:83
18                        05:55                 00:38:92
19                        07:00                 00:39:94
20                        08:05                 00:38:87
21          GP020291      00:20                 01:14:38
22                        02:05                 01:02:21
23                        03:30                 X
24                        05:45                 00:40:35
25                        06:50                 01:01:37
26                        08:24                 00:28:00 + 00:15:00 = 00:43                  * spreads into file GP030291
27          GP030291      00:35                 01:22:48  
28                        02:20                 00:37:21
29                        03:20                 01:10:24
30          GP010290      00:15                 00:39:57
31                        01:16                 00:38:32
32                        02:22                 00:38:84
33                        03:23                 X

#1
You messed up a few times.
X 1) Point 5, you failed to banana-jump and fell down instead.
Ended up back on the ledge in the middle of Point 3.
Had to hitch up again. (sound of hitch a node?)
X 2) Point 5, you failed to grab the ledge (too far away).
Ended up back on the ledge in the middle of Point 3 again.
X 3) Point 6, failed to banana-jump up and slid down instead forwards.
Interestingly, this error path has a come-back.
But it is based on whether you slide down backwards or forwards.
Because the error path diverges based on this.

#2
X Messed up Point 6, but didn't slide down, just fell back down to the ledge.
Got to re-attempt the slidey banana-jump, got it 2nd try.

#3
X Screw-up at a weird place, Point 4, instead of hitching up, you accidentally
jumped sideways. Concept of unforced error?

#4 HP (happy path)

#5
Screw-up at Point 2, you fell off the block after kick-flipping up.
Had to re-position and jump again.

#6
Screw-up at Point 6, missed the ledge and slid down backwards.

#7 HP

#8
X SU at Point 5 TWICE, both times slid down.

#9
4 SUs
X 1) Point 6 failed to make ledge and slid down forwards, rejoined
(you should describe your recovery method with the right-jump)
X 2) Point 5 failed to make jump, slid down and rejoined.
X 3) Repeat of 1)
X 4) Point 6 failed to make ledge, but didn't slide down, just
got to try again.

#10 HP
#11 HP
#12 HP

#13
X SU at Point 5, failed to make jump, slid back down and tried again.

#14
3 SUs
X 1) Point 6 failed to make ledge, slid down forwards
X 2) Point 5 failed to grab ledge, slid down
X 3) Point 6 failed to make ledge, slid down forwards

#15 HP
#16 HP
#17 HP
#18 HP
#19 HP
#20 HP

#21
You messed up a few times jumping to the block on Point 2.
But I'm loathe to make this an error point, frequency is too low.
X SU at Point 6, slid down forwards, jumped to right and rejoined.

#22
X 1 SU at Point 6, failed to make ledge, slid down forwards,
made right-jump and rejoined.

#24 HP

#25
X 1 SU, didn't make Point 6, slid-down forwards,
right-jump to rejoin.

#26
X 1 SU, didn't make Point 6, but just fell back down to try again.

#27
3 SUs
X 1) Point 6, missed ledge, slid forwards and jumped right to rejoin.
X 2) Point 5, missed jump and slid down, rejoined,
X 3) Point 6, missed ledge, but got another try.

#28 HP

#29
X 1) Point 2, twice failed to make jump, try again.
X 2) Point 6, missed ledge, slid down forwards, jump right to recover.

#30 HP
#31 HP
#32 HP



Now we're re-routing, what do we need to map out?
Can we also future-proof slightly and also calculate for 2 alternate route ideas?

1) Time when jump happens at Point 3,
2) Time when Lara's feet hit the "jump across" of Point 4,
3) Time when jump happens of Point 5.
4) Fix to SU5 (getting back to 2 above)
5) Fix to SU6 (getting back to 2 above)

Re-run through each # with respect to this.
