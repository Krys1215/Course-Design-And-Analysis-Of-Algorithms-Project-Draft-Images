
**1. Original Scenario**

As all our team members are international students living outside the campus and do not own any car. Therefore, the school bus has been our main transportation tool, the bus line which is called “South City Line”. The original route of the “South City Line” is from the campus to Mutiara Residence, Univ360 Residence, South City Plaza, East Lake Residence, Sky Villa Residence, KTM Serdang, and turn back to the campus. It is believed that all the bus takers have experienced the traffic jam during the route around South City Plaza. Generally, there are certain number of international students are living near to the KTM Serdang, The Mines Resort, the traffic jam of the route from the campus to KTM Serdang is not heavy, and we can find it when we take the Grab ride. Moreover, there is a Free Bus line of Rapid KL called “SJ04”, which is covering the route from KTM Serdang to our campus, and it is our second plan to travel from home to campus, the passengers can tell the driver what their destinations are, and the driver can adjust the route by themselves. The drivers would love to avoid the route around South City Plaza to avoid the terrible traffic jam. The action the drivers took really inspired us, and we decide to do some improvements.

![](https://github.com/Krys1215/Course-Design-And-Analysis-Of-Algorithms-Project/blob/main/1.png)

*Figure 1 “South City” bus line schedule*

As Figure 1 shown above, we were thinking about developing an application base on the timetable; Assuming that the bus is going to departure at 7:15am for the first roll, the reservation function will be activated 1 hour before the departure of the bus. The application will store the information of the “calling” stations and only travel around the “called” stations. It is not guaranteed that the traffic jam will be avoided every roll, but it is optimistic to avoid it some of the times.

**2. Optimal Solution**

Finding an optimal solution for this scenario is important for several reasons.

Improved punctuality: By allowing users to schedule appointments for their bus rides, the bus routes can be optimized to reduce the amount of time spent in traffic. This means that students and staff will be able to arrive on campus in a timelier manner.

*Increased efficiency*: By optimizing the bus routes, the number of buses needed to transport students and staff can be reduced, which will save time, fuel, and money.

*Increased safety*: By reducing the amount of time spent in traffic, the risk of accidents caused by traffic congestion is also reduced.

*Enhanced student* *and staff satisfaction*: When students and staff can arrive on campus in a timely manner, they will be more satisfied with the bus service. This can lead to improved morale and motivation among students and staff.

*Better university image*: When the bus service is efficient, punctual, and safe, the university will be viewed more favorably by prospective students and their parents, as well as by staff and faculty members.

*Cost Savings*: The bus service is a major cost for the university and making it more efficient, can also reduce the cost of the service.

In summary, finding an optimal solution for this scenario is crucial to improve the overall transportation experience for the university community and to enhance the university's image.

**3. Review of the solution paradigm (Sorting, DAC, DP, Greedy, and Graph)**

*Sorting algorithm*:

*Strengths*: efficient for small data sets and able to handle simple data structures

Weaknesses: Not suitable for solving the problem of optimizing bus routes as it does not guarantee the shortest route and not designed to solve the traveling salesman problem.

*Divide and Conquer (DAC)*:

*Strengths*: Can be used to divide the problem into smaller subproblems and solve them independently, which can make the problem more manageable.

Weaknesses: It may not be able to find the optimal solution for the entire problem, due to the nature of the problem it might become computationally expensive and can lead to a high time complexity.

*Dynamic Programming* (DP):

Strengths: Can be used to find the optimal solution for the problem by breaking it down into smaller subproblems and storing the solutions for future use.

Weaknesses: It can be computationally expensive for large data sets and can lead to a high time complexity.

*Greedy Algorithm*:

*Strengths*: Can be used to find a solution by making locally optimal choices at each step, which can make the problem more manageable.

*Weaknesses*: It may not guarantee a globally optimal solution, and the solution can be heavily influenced by the initial state.

*Graph* *Algorithm*:

*Strengths*: Graph algorithms such as Dijkstra's algorithm or Bellman-Ford algorithm can be used to find the shortest path between two stops.

*Weaknesses*: They are not well suited for solving the TSP problem, they are designed to solve a single-source shortest path problem and not the problem of finding the shortest route that visits a set of locations and returns to the starting point.

In conclusion, TSP algorithm is the most appropriate solution paradigm for this problem as it is specifically designed to solve the problem of finding the shortest route that visits a set of locations and returns to the starting point. Other algorithms such as sorting, DAC, DP, greedy and graph algorithms can also be considered but they may not be able to find the optimal solution for this problem and may come with computational limitations.

**4. Designing Algorithm, and Idea.**

The algorithm that we have chosen to solve this problem is the classical TSP algorithm also known as the "brute-force" algorithm. The idea behind this algorithm is to generate all possible routes and then select the one with the shortest distance.

The algorithm can be broken down into the following steps:

1\. Initialize an empty list to store all possible routes

2\. Generate all possible routes starting from the first bus stop and visiting all other bus stops exactly once.

3\. For each route, calculate the total distance traveled.

4\. Select the route with the shortest distance as the optimal route.

The algorithm is a recursive one and it is based on the concept of backtracking.

1\. Recursive function is called with the current vertex and the remaining set of vertices to be visited.

2\. The function generates all possible routes by visiting the remaining vertices and for each route, it calculates the total distance traveled.

3\. If all the vertices have been visited, the function returns the route with the shortest distance as the optimal route.

The optimization function of this algorithm is the calculation of the total distance traveled for each route. This function is used to compare the different routes and select the one with the shortest distance.

**5. Algorithm Specification**

**5.1 Problem definition**

Given a set of bus stops, find the shortest route that visits all the stops and returns to the starting point.

*Input*: A list of bus stops, including their coordinates and the distances between each pair of stops.

*Output*: A list of bus stops in the order they should be visited to form the shortest route.

*Constraints*: The bus must visit all stops exactly once and return to the starting point.

This problem definition provides a clear and precise understanding of the problem that the algorithm is meant to solve, and what the inputs and outputs of the algorithm should be. It also lays out the constraints that the algorithm needs to consider when finding a solution.

**5.2 Development of model**

![](https://github.com/Krys1215/Course-Design-And-Analysis-Of-Algorithms-Project/blob/main/2.png)

*Figure 2 The stations stated on the Google Maps*

As the Figure 2 shown above, are the stations that the settled bus line will travel. Since the algorithm that we decided to implement is TSP, therefore we need to collect the distances of every destination to each destination. Then, we extract the abstract graph with the distances that calculated by the Google Maps stated as the figure shown below.

![](https://github.com/Krys1215/Course-Design-And-Analysis-Of-Algorithms-Project/blob/main/3.png)

*Figure 3 The extracted graph with the distance in meter*

The default starting point is setting as FSKTM and be the ending point. The core thought of TSP algorithm is to travel all the node and finally go back to the starting point. The red lines indicate that the route between the 2 stations is likely to experience the traffic jam. The green lines denotes that the route is hardly experienced the traffic jam.

The data structure will be Array List and store the stops information that conclude the distance from this stop to others. The basic data structure will be initialized as below in the format of binary array:

![](https://github.com/Krys1215/Course-Design-And-Analysis-Of-Algorithms-Project/blob/main/4.png)

*Figure 4 The Array that contains the distance and the indexes of the stops*

**5.3 Specification of an algorithm**

**5.3.1 Traveling Salesman Problem algorithm**

The TSP can be formulated as an integer linear program. Several formulations are known. Two notable formulations are the Miller–Tucker–Zemlin (MTZ) formulation and the Dantzig–Fulkerson–Johnson (DFJ) formulation. The DFJ formulation is stronger, though the MTZ formulation is still useful in certain settings.

Common to both these formulations is that one labels the cities with the numbers 1,……,n and takes Cij \> 0 to be the cost (distance) from city i to city j. The main variables in the formulations are:

![](https://github.com/Krys1215/Course-Design-And-Analysis-Of-Algorithms-Project/blob/main/5.png)

It is because these are 0/1 variables that the formulations become integer programs; all other constraints are purely linear. In particular, the objective in the program is to minimize the tour length:

![](https://github.com/Krys1215/Course-Design-And-Analysis-Of-Algorithms-Project/blob/main/6.png)

Without further constraints, the ![](https://github.com/Krys1215/Course-Design-And-Analysis-Of-Algorithms-Project/blob/main/7.png) will however effectively range over all subsets of the set of edges, which is very far from the sets of edges in a tour and allows for a trivial minimum where all Xij = 0. Therefore, both formulations also have the constraints that there at each vertex is exactly one incoming edge and one outgoing edge, which may be expressed as the 2n linear equations.

![](https://github.com/Krys1215/Course-Design-And-Analysis-Of-Algorithms-Project/blob/main/8.png)

These ensure that the chosen set of edges locally looks like that of a tour, but still allow for solutions violating the global requirement that there is one tour which visits all vertices, as the edges chosen could make up several tours each visiting only a subset of the vertices; arguably it is this global requirement that makes TSP a hard problem. The MTZ and DFJ formulations differ in how they express this final requirement as linear constraints.

**5.3.2 Steps of TSP Algorithm in Pseudocode**

The TSP algorithm is a recursive algorithm that generates all possible routes and then selects the one with the shortest distance as the optimal route.

1\. The TSP function takes in a graph as input, and initializes an empty list to store all possible routes.

2\. It then calls the generate_routes function, passing in the graph, an empty route, the current vertex, and the list of routes.

3\. The generate_routes function uses a backtracking approach to generate all possible routes by visiting the remaining vertices and adding them to the current route.

4\. If all the vertices have been visited, the function adds the route to the list of routes and returns.

5\. The TSP function then calls the select_optimal_route function, passing in the list of routes.

6\. The select_optimal_route function iterates over the routes and calculates the distance of each route using the calculate_distance function.

7\. It compares the distance of each route to the shortest distance and updates the optimal route and the shortest distance if the current route has a shorter distance.

8\. Finally, the select_optimal_route function returns the optimal route.

Below is the pseudocode implementation.

![](https://github.com/Krys1215/Course-Design-And-Analysis-Of-Algorithms-Project/blob/main/9.png)

![](https://github.com/Krys1215/Course-Design-And-Analysis-Of-Algorithms-Project/blob/main/10.png)

**5.4 Designing an Algorithm**

In order to satisfy the requirements of our bus route designing problem, we need to modify the TSP algorithm to apply the algorithm in Java.

![](https://github.com/Krys1215/Course-Design-And-Analysis-Of-Algorithms-Project/blob/main/11.png)

This code shows the procedure of the initialization of the data structures and the instance. The variables of the data structure need to be sign as the specific value. As we mentioned before. For example, the graph will be extracted as a binary array. The best paths will be stored in an Integer List.

![](https://github.com/Krys1215/Course-Design-And-Analysis-Of-Algorithms-Project/blob/main/12.png)

1\. Firstly, the calling of the algorithm is beginning with the method “tsp()”, we consider it as the “trigger” of this algorithm. It adds the first stop (index “0”) to the bestPath List, and then call the “travel()” method. The values included inside this method are: index of the stops, count number of the recursive, total distance, the path that have traveled for one execution.

2\. The “If” statement is to check the count number of the recursive is equal to the total number or not, if so, it will be added on the distance of “last” travel. Moreover, if the total distance at that time is smaller than the bestDistance that will be accumulate in the following code, the best distance will be updated to the total distance at this time, and simultaneously, the bestPath List will be updated be the path that last travel has been. This inner “If” statement we consider as the terminating statement.

3\. To traversal all the other stops, and if the path has visited one of the stops, it will skip this stop. Then, add on the distance from the starting stop to the stop in current loop execution. If the current distance is larger than the best distance that has been calculated, then no need further searching.

4\. However, if the city is not visited and the current distance is not larger than the pervious distance, the program will add this path as the potential best path, then keep on travelling by calling the travel method again with the value of: current index of the city, the count number of the recursive + 1, the distance from the current stop to the next stop, and the potential best path.

5\. path.remove(path.size() - 1) is for the recalling purpose, if the all the recursive execution is terminated.

**5.5 Checking the correctness of an algorithm**

After the implementation of the graph that we extracted, the result is below:

![](https://github.com/Krys1215/Course-Design-And-Analysis-Of-Algorithms-Project/blob/main/13.png)

The implementation design will be explained later in the next 5.6 section. Ignoring the implementation of this design, according to the graph that we extracted, the shortest path that we choose by our hands is below:

![](https://github.com/Krys1215/Course-Design-And-Analysis-Of-Algorithms-Project/blob/main/14.png)

Which exactly the same with the original route design of our school bus and the output of our program.

**5.6 Implementation of an algorithm**

According to the initial thought that we came up with in the first part of our report, we wanted to develop an application that allows students or the bus takers to make the bus appointment at the period of time before the departure of the bus. Therefore, we involve the function to let the user to input “1” if there are any passengers intend to take the bus, “0” means there is no passenger call for the application and the bus will not consider to pass the stop.

![](https://github.com/Krys1215/Course-Design-And-Analysis-Of-Algorithms-Project/blob/main/15.png)

In order to make it easier to store the stop information, we create a class to store all the bus stops’ information:

It concludes the name of the station, for us to print out the name in the later output section. The index is to set the index of the stop, to match with the distance from “index to index”. The array of distance is to record the distances from the current station to others’ distance.

![](https://github.com/Krys1215/Course-Design-And-Analysis-Of-Algorithms-Project/blob/main/16.png)

This method is to create an Array List to store all the information of all the stations.

![](https://github.com/Krys1215/Course-Design-And-Analysis-Of-Algorithms-Project/blob/main/17.png)

For the passengerCall() method, is to store the calling value from the passengers, and store all the request into an array, in order to match the index of the stops. “1” for there is passenger, and “0” for no passenger.

![](https://github.com/Krys1215/Course-Design-And-Analysis-Of-Algorithms-Project/blob/main/18.png)

Here is the most interesting part of the implementation, which I designed by myself to call the stations.

At the very beginning of the project development, if one station is not selected, the distance to all the other destinations will be disordered. Remember that all distances stored inside one station, and the index will be the distance from the station to the station of this index.

Therefore, I found that I could use the request from the different stops to pick up the station and the distance accordingly.

Let’s say, if there is only one station and the station’s index is 1 that has the request from the passengers, the array of the request will be: [0, 1, 0 ,0 ,0 ,0 ,0 ,0]. Then the only valid data will be:

0: [0,4400]

1: [4400,0]

Then, I need to remain the index of 0, and pick up the index 1 for the outer loop of the execution. Moreover, I need to pick up the inner loop of every value in index of 1 and 0, to be the “dynamicSelection”.

![](https://github.com/Krys1215/Course-Design-And-Analysis-Of-Algorithms-Project/blob/main/19.png)

The main method, to call out all the methods and operate the program.

After the “dynamicSelection”, the requested list of the stations is created. In the first for loop, it will accumulate the total distance for the display purpose. The array, [][]distance is from the created list of the requested station’s value of the distance.

Finish getting the number of the stops, and the distance information from the selected stops, we could finally call the algorithm method to output the path.

The output formation will be print out the destinations one by one and finally print out the total distance of the shortest path.

**5.7 Program testing**

As the assumption that we made, the route only travel through the “green lines”, will be less likely to experience the traffic jam, and the first test will be selecting a destination that is only connected with the “green lines”, for example, Starting point, SPE, and KTM Serdang.

![](https://github.com/Krys1215/Course-Design-And-Analysis-Of-Algorithms-Project/blob/main/20.png)

The output is totally correct and satisfying with our assumption.

Another example of the testing will be only select the stations that connect with the red lines:

![](https://github.com/Krys1215/Course-Design-And-Analysis-Of-Algorithms-Project/blob/main/21.png)

The output is correct as well, and it indeed follow the shortest path.

**6. Time Complexity**

1\. Best-case time complexity: This is the scenario where the algorithm performs the best, typically when the input is already sorted or in the optimal configuration. The best-case time complexity of the TSP algorithm is O(n!) where n is the number of stops.

2\. Average-case time complexity: This is the scenario where the algorithm is run on randomly generated inputs. The average-case time complexity of the TSP algorithm is also O(n!)

3\. Worst-case time complexity: This is the scenario where the algorithm performs the worst, typically when the input is in the worst possible configuration. The worst-case time complexity of the TSP algorithm is also O(n!)

It's worth mentioning that the TSP problem is an NP-hard problem, which means that no algorithm with polynomial time complexity (O(n\^k) for some constant k) is known. The complexity of the TSP problem is O(n!) which is impractical for large input sizes, that's why there are many heuristics and approximate solutions that have been proposed to solve the TSP problem more efficiently.

**7. Reference**

[1] Papadimitriou, C.H.; Steiglitz, K. (1998), Combinatorial optimization: algorithms and complexity, Mineola, NY: Dover, pp.308-309.

[2] Tucker, A. W. (1960), "On Directed Graphs and Integer Programs", IBM Mathematical research Project (Princeton University)

[3] Dantzig, George B. (1963), Linear Programming and Extensions, Princeton, NJ: PrincetonUP, pp. 545–7, ISBN 0-691-08000-3, sixth printing, 1974.

[4] Velednitsky, Mark (2017). "Short combinatorial proof that the DFJ polytope is contained in the MTZ polytope for the Asymmetric Traveling Salesman Problem". Operations Research Letters. 45 (4): 323–324. arXiv:1805.06997. doi:10.1016/j.orl.2017.04.010. S2CID 6941484.

[5] Bektaş, Tolga; Gouveia, Luis (2014). "Requiem for the Miller–Tucker–Zemlin subtour elimination constraints?". European Journal of Operational Research. 236 (3): 820–832. doi:10.1016/j.ejor.2013.07.038.
