# Ex24 Topological Sort
## DATE: 01/05/2025
## AIM:
To compose the code to determine whether the topological ordering for the following graph is possible or not.

![image](https://github.com/user-attachments/assets/c74a7111-9b59-475c-aad4-9baf23d50ec0)


## Algorithm
1.Initialize variables:

Declare i, v, count, topo_order[MAX], and indeg[MAX].

2.Create the graph:

Call create_graph() to initialize the graph structure.

3.Calculate indegree for each vertex:

For each vertex i from 0 to n-1:
Calculate indeg[i] using indegree(i).
If indeg[i] is 0, insert vertex i into the queue using insert_queue(i).

4.Perform topological sorting:

Initialize count to 0.
While the queue is not empty and count is less than n:
Remove vertex v from the queue using delete_queue().
Add vertex v to topo_order at index ++count.
For each vertex i from 0 to n-1:
If there is an edge from v to i (i.e., adj[v][i] == 1):
Remove the edge by setting adj[v][i] to 0.
Decrease indeg[i] by 1.
If indeg[i] becomes 0, insert vertex i into the queue.

5.Check for cycles:

If count is less than n, print "No topological ordering possible, graph contains cycle" and exit the program.

6.Print the topological order:
Print "Vertices in topological order are:".
For each index i from 1 to count, print topo_order[i].

7.End the program:

Return 0 to indicate successful completion 

## Program:
```
/*
Program to determine whether the topological ordering for the following graph is possible or not
Developed by: PRADEEP V
RegisterNumber: 212223240119
*/
int main()
{
        int i,v,count,topo_order[MAX],indeg[MAX];

        create_graph();

        /*Find the indegree of each vertex*/
        for(i=0;i<n;i++)
        {
                indeg[i] = indegree(i);
                if( indeg[i] == 0 )
                        insert_queue(i);
        }

        count = 0;

        while(  !isEmpty_queue( ) && count < n )
        {
                v = delete_queue();
        topo_order[++count] = v; /*Add vertex v to topo_order array*/
                /*Delete all edges going from vertex v */
                for(i=0; i<n; i++)
                {
                        if(adj[v][i] == 1)
                        {
                                adj[v][i] = 0;
                                indeg[i] = indeg[i]-1;
                                if(indeg[i] == 0)
                                        insert_queue(i);
                        }
                }
        }

        if( count < n )
        {
                printf("No topological ordering possible, graph contains cycle\n");
                exit(1);
        }
        printf("Vertices in topological order are :\n");
        for(i=1; i<=count; i++)
                printf( "%d ",topo_order[i] );
        printf("\n");

        return 0;
}/*End of main()*/
```

## Output:

![437484428-8845165c-ad03-49d2-a955-1552731101e1](https://github.com/user-attachments/assets/3604635b-0ea1-4d20-84c3-1a19d4d7c047)


## Result:
Thus, the C program for determining whether the topological ordering for the following graph is possible or not, is implemented successfully.
