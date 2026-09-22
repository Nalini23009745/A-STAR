<h1>ExpNo 4 : Implement A* search algorithm for a Graph</h1> 
<h3>Name: NALINI P </h3>
<h3>Register Number:  212223220063    </h3>
<h3> Date: 13/08/2026 </h3>
<H3>Aim:</H3>
<p>To ImplementA * Search algorithm for a Graph using Python 3.</p>
<H3>Algorithm:</H3>

``````
// A* Search Algorithm
1.  Initialize the open list
2.  Initialize the closed list
    put the starting node on the open 
    list (you can leave its f at zero)

3.  while the open list is not empty
    a) find the node with the least f on 
       the open list, call it "q"

    b) pop q off the open list
  
    c) generate q's 8 successors and set their 
       parents to q
   
    d) for each successor
        i) if successor is the goal, stop search
        
        ii) else, compute both g and h for successor
          successor.g = q.g + distance between 
                              successor and q
          successor.h = distance from goal to 
          successor (This can be done using many 
          ways, we will discuss three heuristics- 
          Manhattan, Diagonal and Euclidean 
          Heuristics)
          
          successor.f = successor.g + successor.h

        iii) if a node with the same position as 
            successor is in the OPEN list which has a 
           lower f than successor, skip this successor

        iV) if a node with the same position as 
            successor  is in the CLOSED list which has
            a lower f than successor, skip this successor
            otherwise, add  the node to the open list
     end (for loop)
  
    e) push q on the closed list
    end (while loop)

``````

## Program:

```
def a_star(graph, h, start, goal):

    open_list = [start]
    g = {start: 0}
    parent = {start: None}

    while open_list:

        current = min(open_list, key=lambda x: g[x] + h[x])

        if current == goal:
            path = []

            while current is not None:
                path.append(current)
                current = parent[current]

            path.reverse()

            print("Shortest Path:", " -> ".join(path))
            print("Total Cost:", g[goal])
            return

        open_list.remove(current)

        for neighbour, cost in graph[current]:

            new_cost = g[current] + cost

            if neighbour not in g or new_cost < g[neighbour]:
                g[neighbour] = new_cost
                parent[neighbour] = current

                if neighbour not in open_list:
                    open_list.append(neighbour)

    print("Path does not exist!")


# Graph
graph = {
    'A': [('B', 1), ('C', 4)],
    'B': [('A', 1), ('D', 2), ('E', 5)],
    'C': [('A', 4), ('E', 1)],
    'D': [('B', 2), ('G', 3)],
    'E': [('B', 5), ('C', 1), ('G', 2)],
    'G': [('D', 3), ('E', 2)]
}

# Heuristic values
h = {
    'A': 7,
    'B': 6,
    'C': 4,
    'D': 3,
    'E': 2,
    'G': 0
}

a_star(graph, h, 'A', 'G')

```

<hr>
<h2>Sample Graph I</h2>
<hr>

![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/b1377c3f-011a-4c0f-a843-516842ae056a)

<hr>
<h2>Sample Input</h2>
<hr>
10 14 <br>
A B 6 <br>
A F 3 <br>
B D 2 <br>
B C 3 <br>
C D 1 <br>
C E 5 <br>
D E 8 <br>
E I 5 <br>
E J 5 <br>
F G 1 <br>
G I 3 <br>
I J 3 <br>
F H 7 <br>
I H 2 <br>
A 10 <br>
B 8 <br>
C 5 <br>
D 7 <br>
E 3 <br>
F 6 <br>
G 5 <br>
H 3 <br>
I 1 <br>
J 0 <br>
<hr>
<h2>Sample Output</h2>
<hr>
Path found: ['A', 'F', 'G', 'I', 'J']


<hr>
<h2>Sample Graph II</h2>
<hr>

![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/acbb09cb-ed39-48e5-a59b-2f8d61b978a3)


<hr>
<h2>Sample Input</h2>
<hr>
6 6 <br>
A B 2 <br>
B C 1 <br>
A E 3 <br>
B G 9 <br>
E D 6 <br>
D G 1 <br>
A 11 <br>
B 6 <br>
C 99 <br>
E 7 <br>
D 1 <br>
G 0 <br>
<hr>
<h2>Sample Output</h2>
<img width="730" height="400" alt="image" src="https://github.com/user-attachments/assets/6bc56cb6-6bc1-42d6-8dd3-c1cb5852f0c2" />

<hr>
Path found: ['A', 'E', 'D', 'G']
<hr>

## INPUT:

<img width="497" height="653" alt="image" src="https://github.com/user-attachments/assets/a86362da-8959-4b99-8207-3068b733ae73" />



## Output:
 <img width="522" height="66" alt="image" src="https://github.com/user-attachments/assets/a967037f-1720-4608-99e6-0691e10f8c84" />

 <img width="817" height="696" alt="image" src="https://github.com/user-attachments/assets/3419ed53-1d90-4992-8f45-c4c8a66e27a5" />



## Result:

Thus a graph was constructed and implemantation of A star Search for the same graph was done successfully.

