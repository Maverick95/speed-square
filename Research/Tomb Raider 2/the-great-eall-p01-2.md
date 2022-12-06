1) Time when jump happens at Point 3,
2) Time when Lara's feet hit the "jump across" of Point 4,
3) Time when jump happens of Point 5.
4) Time when first jump happens of Point 6.
5) Fix to SU5 (getting back to 2 above)
6) Fix to SU6 (getting back to 2 above)
7) 4 to END


                Point # (see notes)

Attempt #       1       2       3       4         5       6       7
1               11.65   08.54   05.48             10.80       
                                05.48             10.62
                                06.36   06.25             09.40
                                06.01   06.45                     06.52
2               11.62   08.66   05.40   06.15                     10.28
3               11.91   08.60   06.34   06.52                     05.13
4               12.55   08.76   06.24   06.48                     05.27
5                       08.84   06.21   06.67                     05.57
6               11.96   08.91   06.46   06.27
                                06.00   06.46                     05.85
7               11.87   08.76   05.26   06.71                     05.02
8               12.03   08.76   05.57             10.52
                                06.22             11.49
                                05.94   06.63                     05.97
9               11.98   08.70   05.55   06.43             09.57
                                05.45             10.86
                                06.40   06.41             10.57
                                05.78   06.42                     11.73
10              11.98   08.84   05.42   06.46                     05.24
11              12.16   08.83   05.52   06.50                     05.02
12              11.92   08.69   05.57   06.43                     05.94
13              scrap due to file crossover
14              11.96   08.72   05.39   08.22             11.37
                                05.73             10.57
                                05.38   06.52             10.93
                                05.52   06.40                     05.59
15              11.95   08.69   05.51   06.41                     05.50
16              11.80   08.87   05.32   07.59                     05.45
17              11.90   08.81   05.37   09.63                     05.18
18              12.10   08.82   06.23   06.50                     05.39
19              11.75   10.64   05.53   06.55                     05.19
20              11.97   08.98   06.22   06.60                     04.95
21                      08.93   05.38   07.63             10.52
                                05.56   06.43                     05.42
22              11.73   08.83   05.32   06.46             10.45
                                07.98   06.50                     05.00
24              12.00   08.92   05.63   07.11                     06.86
25              12.01   08.72   05.52   06.94             10.77
                                05.50   06.69                     05.37
26              scrap due to file crossover
27              12.13   08.81   05.60   06.89             10.27
                                05.64             10.33
                                05.46   06.61                     10.79
28              11.78   08.85   05.30   06.38                     05.00
29              20.48   08.86   05.40   06.20             11.31
                                05.42   07.02                     05.45
30              12.41   08.81   06.87   06.65                     04.91
31              12.36   08.91   05.70   06.45                     05.09
32              11.88   08.80   05.86   06.50                     05.81

Damn, well here we go.

Need to find averages of each.

And the probabilities.

1st % is at 3, either you go to 4, or back to 2
2nd % is at 4, either you go to 7, or back to 2

1st % is therefore #5/(#5 + #4) = 7 / (7 + 40) = 7 / 47 = 14.89%
2nd % is therefore #6/(#6 + #7) = 10 / (10 + 29) = 10 / 39 = 25.64%

Weird thing about the probabilities... each run must have contributed to a success.
Like in each case, you were guaranteed to have one success per run.
I don't THINK this is an issue.


Okay, so are we ready to set out the nodes?


Node 0
          12.29
Node 1
          8.86
Node 2
          5.77
Node 3
          14.89% of incurring 10.74 and back to Node 2
          o/w 6.7
Node 4
          25.64% of incurring 10.52 and back to Node 2
          o/w 6.02
Node X

Right then.

Calculating expected time of Node 2 to Node X

a1 = 5.77
a2 = 10.74
a3 = 6.7
a4 = 10.52
a5 = 6.02

b1 = 0.1489
b2 = 0.2564

a1 = 5.77
b1a2 = 1.599
(1-b1)a3 = 5.70237
(1-b1)b2a4 = 2.2957
(1-b1)(1-b2)a5 = 3.8099

SUM = 19.17697

1 - b1 - (1-b1)b2 = 0.6329

Expected from Node 2 to Node X = 19.17697 / 0.6329 = 30.3

Total = 30.3 + 12.29 + 8.86 = 51.45

51.45 is the final expected number.




