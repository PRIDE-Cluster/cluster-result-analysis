# cluster-result-analysis

 - cmp_cr 

      - cmp_cr is short for compare the cluster results.
   
      - Usage:
         ```
         ./cmp_cr result1.clustering result2.clustering
         ```
   
      - the main idea
      
        We assume the clusters in smaller list, which are bigger clusters, are divided to be the smaller clusters in the bigger list.
        
        Then we calculate statistics of the division.
        
        We call the bigger cluster from small List as "Star", and the cluster outside as "outter"(please suggest a better name).
        
                            
                                  outer1(5) <---------Star1(30)----->outter2(5)<---------Star2(10)--------->outter3(5)
                                                         |
                                                         |
                                                         |
                                                         |
                                                         |
                                                      outter4(10)
         For Star1, who has 30 spectra in the cluster, but only share 20 spectra with outter1/2/4, we call it lost 10 spectra.
         Then we define the "divid factor" of Star1 is 13, 3 outters in the network, plus 10 singleton clusters. 
         
         The connection of Stars: Star1 and Star2 is connected by outter2, and outter2 has 2 lines out here.
         
         
         
###Example output

```
start reading file 1: cli_clustering.example_2.clustering_0.5_4
end of file 1
start reading file 2: hadoop_1/clustering_results/all.clustering
end of reading file 2



the statistics of the files
----------------------------------------
3711	 clusters in file 1: cli_clustering.example_2.clustering_0.5_4
459	 clusters in file 2: hadoop_1/clustering_results/all.clustering
40	 same clusters between them
0.999723849537x50697=50683 shared spectra from cli_clustering.example_2.clustering_0.5_4
0.986031400167x51401=50683 shared spectra from filehadoop_1/clustering_results/all.clustering
----------------------------------------



the distribution of cluster size in file 1 cli_clustering.example_2.clustering_0.5_4
----------------------------------------
cluster size	No.
----------------------------------------
2		566
3		485
4		328
5		250
6		241
7		186
8		148
9		119
10		117
11		125
12		94
13		70
14		86
15		70
16		50
17		55
18		47
19		39
20		44
21		31
22		32
23		36
24		29
25		16
26		19
27		18
28		12
29		19
30		20
31		20
32		12
33		11
34		13
35		12
36		7
37		18
38		6
39		10
40		13
41		7
42		6
43		6
44		6
45		12
46		6
47		5
48		4
49		4
50		6
51		3
52		10
53		2
54		6
55		6
56		4
57		3
58		3
59		5
60		3
61		3
62		3
63		4
64		3
65		2
66		4
67		2
68		2
69		5
71		3
72		2
73		4
74		1

----------------------------------------



the distribution of cluster size in file 2 hadoop_1/clustering_results/all.clustering
----------------------------------------
cluster size	No.
----------------------------------------
2		28
3		27
4		16
5		10
6		16
7		14
8		5
9		7
10		8
11		7
12		8
13		8
14		5
15		8
16		6
17		3
18		3
19		5
20		3
21		3
22		1
23		5
24		4
25		3
26		1
27		4
28		3
29		2
30		5
31		3
32		3
33		1
34		3
35		1
37		3
38		1
39		3
40		2
267		1
268		1
271		1
280		1

----------------------------------------



the distribution of similarity between them(similarity=10 is identical)
----------------------------------------
similarity	No.
----------------------------------------
0		1701840
1		679
2		307
3		159
4		92
5		76
6		56
7		30
8		53
9		17
10		40
----------------------------------------


----------------------------------------
totally lost 718(1.39685998327%)spectra in Stars
totally lost 14(0.0276150462552%)spectra in Outters
----------------------------------------



average dividing factor ---(each of a losted spectrum will be considered as one singleton cluster, which contribute equelly to the normal clusters)
----------------------------------------
13.559912854
----------------------------------------



the distribution of dividing factors
----------------------------------------
Divide Factors 	 No.
----------------------------------------
1		74
2		60
3		31
4		29
5		13
6		16
7		13
8		14
9		12
10		15
11		3
12		11
13		8
14		5
15		5
16		7
17		6
18		9
19		4
20		4
21		2
22		7
23		3
24		5
25		4
26		3
27		5
28		4
29		3
30		2
31		4
32		4
33		4
34		6
35		4
36		5
37		6
38		5
39		3
40		5
41		6
42		5
43		5
44		1
45		4
46		1
47		3
48		1
49		1
50		1
51		2
52		1
54		3
55		1
59		1
----------------------------------------



No of stand alone clusters
----------------------------------------
small group	big group
----------------------------------------
1		0



some stars are connected by these outters
----------------------------------------
outter 12has 3 lines out(>1), should be careful 
outter 51has 3 lines out(>1), should be careful 
outter 158has 3 lines out(>1), should be careful 
outter 166has 3 lines out(>1), should be careful 
outter 2317has 3 lines out(>1), should be careful 
outter 2326has 3 lines out(>1), should be careful 
outter 2353has 3 lines out(>1), should be careful 
outter 2362has 3 lines out(>1), should be careful 
outter 2379has 3 lines out(>1), should be careful 
outter 2384has 3 lines out(>1), should be careful 
outter 2390has 3 lines out(>1), should be careful 
outter 2402has 3 lines out(>1), should be careful 
outter 2410has 3 lines out(>1), should be careful 
total No.
----------------------------------------
1454
----------------------------------------

```
