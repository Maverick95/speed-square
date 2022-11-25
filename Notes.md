** Speedrunning software plans **

At the moment, these notes don't represent anything concrete.

I've just had a lot of thoughts about starting on this soon. So wanted to write something down first.

The idea is a piece of online software that can be used to plot a speedrun.

It allows you to build a speedrunning plan for a level / game / whatever.

In a crude loose way, it is represented as a (potentially very large) graph algorithm.

Within a plan, there is a start node and a destination node. You begin at the start node.

You reach the destination node by moving from the start node across other nodes, connected by edges

represented as units of time.

For example, you can think of the entire game of Resident Evil 1 on PSX as Jill as -

Node Index      Description
0 (start)       Beginning of game
1               Jill gets control in mansion dining room
2               Leave mansion through 4 crests door
3               Enter guardhouse
4               Leave guardhouse with Helmet Key
5               Enter sewers
6               Take elevator down to laboratory
7               Shoot the rocket launcher at the Tyrant
X               End of game

Each node is clearly defined, e.g. Node 2 is the moment that Jill gains control
in the first room past the 4 crests door (the room with the crank on the shelf).

You can have as many edges as possible between adjacent nodes as you like.

ASSUMPTION - edges are permanently available.
This isn't always true, for example, in Resident Evil, once you get the shotgun and Barry
uses the infamous "Jill Sandwich" line, you can't re-enter the room with the shotgun.
Come back to this later. (concept of state and availability)

As long as there is a possible path to take from Node 0 to Node X, you have a STRAT.

This STRAT is a choice of a route from Node 0 to Node X.
The time taken for the STRAT is the sum of all the times of the edges.

Simple enough really.

One key element to note from the above is that, you can express the Strat in many ways.

You can express it as travelling from...
Node 0 to Node X
or
Node 0 to Node 1 to Node X
or
Node 0 to Node 3 to Node 5 to Node X
or
...

At any point a Node can be collapsed logically.

This is your infamous 2^(N-2) rule.

If there are 2 nodes, there is only one way of expressing the Strat.
If there are 3 nodes, there are 2 ways of expressing the Strat.
Every node in-between is an on-off switch (either its included or not), therefore its 2^(N-2)

2 nodes -> 1
3 nodes -> 2
4 nodes -> 4
0 to X
0 to 2 to X
0 to 1 to X
0 to 1 to 2 to X

I want to get on to talking about STATE.

Effectively a Strat and a Game is just a giant State machine.

The State of a Strat at a particular Node is just that, every data point about the current state
of the game at the least granular level required to calculate whether taking any edge path is possible / impossible.

I don't think the State includes the Node you are currently at.
It is KiNd Of part of the State. 

Every game technically has Node 0 and Node X at least. i.e. a beginning and an end.

But some games don't really fit the pattern very well.

e.g. Minesweeper

Haha. You might think "well don't be ridiculous, of COURSE Minesweeper doesn't fit this", but here's the point,
how do you decide what games fit and which don't?

One of the "obvious" reasons why Minesweeper doesn't fit the pattern, is that,
there is a strong element of randomness. If the game has M mines and S squares,
there are S choose M ways of arranging the board.
So right away there are many many combos.
But again, combos of what? State or Location?


What are Dimensions?

In the example of Resident Evil, some of the Dimensions of State would include -

1) Specific placement of items in the inventory slots,
this itself would be broken up into... item in place 1, item in place 2, etc...

2) Size of the inventory, e.g. in Resident Evil 2 and 3, you get the expansion pack

3) Health, both the physical number and the status (Fine / Caution / Danger)

4) Whether you've grabbed the Chemical or not,

5) Specific placement of items in the chest, ergo also each slot,

Note something else. Some Values of each Dimension are allowed together, some are not.
This should be obvious.

In some games, the player's location seems like a naturally intuitive Dimension to make the main subject
of the Strat, BUT do not assert this.

However it is important to remember that it is just a Dimension.

For example, for computing the fastest Strat, or for exploration given a new bug,
it may be useful to know when States are different, focusing on Dimensions other than Location.

Also, the nature of some Games / Strats mean that Location won't be the primary Dimension within
a certain context.
e.g. if the goal of a level was to collect a certain number of [items], this could mean that
plotting the player's Location isn't that effective (although it could be effective in certain
areas).

So you could need to swap and switch on the dimension? If its useful I guess.


Note that you can reach the end of a Game with different states.
(for example, in Resident Evil, there are game grades based on using First Aid Sprays, Saves etc.
You can finish the Game, while having other States than the intended)

At this point, what is a Node?
Is it a specific Value of State?

I think it is wrong to assume at this point, more than you know to be true.

Therefore don't assume this.
I think Nodes are just arbitrary informal points defined by the User, that have a State,
but make sense to the User in terms of time changes.

The absolute LEAST that you can assume is,
there is a boolean Dimension that indicates IsGameComplete. Initial State is IsGameComplete=false.
The goal is to reach state IsGameComplete=true.

You CANNOT assume anything more than that.

Why not? Because speedrunners are clever and like to break things.
Any iron-cast rule, will be broken.
Rules were made to be broken.

I think apart from this, I wouldn't make any strong assumptions BY DEFAULT about whether
dimensions are one-way / two-way.

For example, your Dimension for Resident Evil.

There's a concept in here I'm moving towards expressing.

It's about how you can break down the Strat for a Game into blocked Segments.

The differences between Tomb Raider 2, and Resident Evil, are perfect for expressing this.


Tomb Raider 2

Tomb Raider 2 has an obvious Dimension, CurrentLevel.

The Values of CurrentLevel are 1 (Great Wall), 2 (Venice), ..., 18? (Home Sweet Home).

In addition, you can combine this with ANOTHER Dimension, IsCurrentLevelComplete (boolean).

And therefore, the Dimension IsGameComplete is derived as...

CurrentLevel=18 AND IsCurrentLevelComplete=true => true
otherwise => false

This is one way of expressing it.
Another way is to have a 19th Value of CurrentLevel known as "Ending Credits".

This may be more useful, because in certain games you can ACE (Arbitrary Code Execute) your way
to the end credits. e.g. Ocarina of Time.

I would say Level is one of the most common Dimensions you see on the screen.

This raises an interesting question. You have to specify here, the different nodes shown on the screen
to the user,
CAN represent States that differ based on > 1 Dimension.

And this raises a point you should take into account now. DO NOT assume more than you know.
For example, don't lock the user view into a single dimension.

The Nodes on the View are completely defined by the User. The User must set the State that they refer to.
Note for later, right away, there should be a feature that allows you to copy the State of a Node to a new
subsequent Node (since it is likely the State will only change from Node-to-Node by Values across a small
number of Dimensions).

In terms of Strats and Segments...

the current best Strat for Tomb Raider 2 involves progressing one-way from Level 1 to Level 2 to.... to Level 18
to Ending Credits.

You can't go "back" a level.
You can Load previous levels, but there's no benefit to this.

However, this is not a 100% assumption about the Game. Remember, rules are made to be broken.
2 examples in Tomb Raider of this being broken are -
1) Offshore Rig, what happened if somebody got through the closing door into Diving Area?
2) Catacombs of the Talion, what happened if somebody got under the ice into Ice Palace?


Resident Evil

Resident Evil has a less obvious dimension, CurrentLocation.

You can define this as the room on the map(s) they are currently in.

You can move backwards and forwards in this way (you can always go back a room).
Sometimes you can't though, paths can become cut off.

CurrentLocation is one obvious indicator of game progression.

BUT, in speedrunning, the point at which "time" is called, isn't really when CurrentLocation changes.
It's when you shoot the Tyrant with the rocket launcher.

I think its a mistake to try and enforce a definition of IsGameComplete, based on subsequent Dimensions.
You can do it if you want. But don't ENFORCE it.

In Resident Evil, it doesn't really make sense to define the steps at the end of the game, in terms of CurrentLocation
entirely. Or in terms of a value of another dimension.

The final step is a change in State that can't rigidly be defined, but would be understood by anybody who played the game.

Node Y
CurrentLocation = Escape Corridor

->

Node Y + 1
CurrentLocation = Helipad
InventoryHasFlare = False

->

Node Y + 2
CurrentLocation = Helipad
InventoryHasFlare = True

->                                  

either
Tyrant ending                           No Tyrant ending
Node Y + 3                              Node X
CurrentLocation = Helipad               IsGameComplete = True (you just fire the flare)
InventoryHasFlare = False
InventoryHasRocketLauncher = True

->
Node X
IsGameComplete = True (Tyrant gets blown up)


The last step is when you shoot the Tyrant.
There isn't really an effective State you can set here.
It's just... you've shot the Tyrant. That's it.

This MIGHT be a case for thinking about defining Events in addition to State
(the Event of shooting the Tyrant), but this seems a bit stupid.

This Event is best understood subjectively as a label when switching between Nodes.



I think I've said enough about State at this point.

There is definitely the idea of derived Dimensions (one Dimension maps to another Dimension),
but this isn't groundbreaking, its just a re-expression of a Dimension.

NOTE - something about Nodes having identical States. Nodes can be replicated in this way
(different Nodes can have same State), but maybe these should be identified to the User?
A thought for later.

Something mentioned earlier to build on.
State consists of the minimum span of Dimensions / Values to cover cases where edges become available / unavailable.
This is one of the key ideas behind the software.
Edges can be specifically INCLUDED or EXCLUDED based on State.

Or is Included just a case of Not Excluded?
Whichever is easier for the User to express, or makes sense to them.

Oh. Actually, now there is something fairly big I want to think about.

Something you mentioned earlier, "Nodes having a value of State attached to them".
This now seems unwise. Or suspect. One of the two.
Why? Well.

Take Tomb Raider 2 as an example.

Say you wanted to represent a Node for "falling through the grate at the top of The Great Wall".
You can reach this Node and either have picked up the grey secret, or not.
Should you define 2 separate Nodes for these States? Seems ridiculous.

So again, I don't think tying a Node to a State is valid.
Or even saying what the State definitely is at a Node.

In this example, it makes more sense to define 2 separate Strats that reach the same Node,
but with different States.

A lot of situations seem to fit this. Especially when you consider ammunition / items / health packs / current health.

So is it more accurate to say, State can be CALCULATED at a given Node, for a given Strat, but not defined?

In this sense, it is defined through the Edges.
And the Edges defined a State Change.
This can be either increasing / decreasing a Value, or setting a Value. Maybe even multiplying? Dividing? Maybe.
Some transformation of a Value.

In this way, the State Change for an Edge creates a requirement.
For example, if travelling a certain route means your health goes down by X units, in order to use this Edge,
your State at the previous Node must include a Health value > X. Otherwise you'd die.

Requirements can also be defined by the User, for example, a door being locked/unlocked, or the player
having a key in their inventory.



Now I'm getting confused. What is a Node, if not a State?







