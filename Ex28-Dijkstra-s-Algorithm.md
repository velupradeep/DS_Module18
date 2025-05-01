# Ex28 Dijkstra’s Algorithm
## DATE: 01/05/2025
## AIM:
To write a C Program to implement Dijkstra's Algorithm to find the shortest path

## Algorithm
1.Initialize distances:

Set the distance to the start node as 0 and to all other nodes as infinity. Mark all nodes as unvisited.

2.Pick the unvisited node with the smallest distance:

Start with the node with the smallest known distance (initially, the start node).

3.Update distances to neighbors:

For each unvisited neighbor, calculate the tentative distance through the current node.
If it’s smaller than the known distance, update it.

4.Mark the current node as visited:

Once all neighbors are checked, mark the current node as visited.
A visited node will not be checked again.

5.Repeat steps 2–4:

Continue picking the unvisited node with the smallest distance and updating its neighbors.

6.Stop when all nodes are visited or the shortest path is found:

If you’re only looking for the shortest path to one target node, you can stop once that node is visited.
 

## Program:
```
/*
Program to implement Dijkstra's Algorithm 
Developed by: PRADEEP V
RegisterNumber: 212223240119
*/
#include<stdio.h>
#define INFINITY 9999
#define MAX 10
 
void dijkstra(int G[MAX][MAX],int n,int startnode);
 
int main()
{
int G[MAX][MAX],i,j,n,u;
scanf("%d",&n);
for(i=0;i<n;i++)
for(j=0;j<n;j++)
scanf("%d",&G[i][j]);
scanf("%d",&u);
dijkstra(G,n,u);
return 0;
}
 
void dijkstra(int G[MAX][MAX],int n,int startnode)
{
 
int cost[MAX][MAX],distance[MAX],pred[MAX];
int visited[MAX],count,mindistance,nextnode,i,j;
//pred[] stores the predecessor of each node
//count gives the number of nodes seen so far
//create the cost matrix
for(i=0;i<n;i++)
for(j=0;j<n;j++)
if(G[i][j]==0)
cost[i][j]=INFINITY;
else
cost[i][j]=G[i][j];
//initialize pred[],distance[] and visited[]
for(i=0;i<n;i++)
{
distance[i]=cost[startnode][i];
pred[i]=startnode;
visited[i]=0;
}
distance[startnode]=0;
visited[startnode]=1;
count=1;
while(count<n-1)
{
mindistance=INFINITY;
//nextnode gives the node at minimum distance
for(i=0;i<n;i++)
if(distance[i]<mindistance&&!visited[i])
{
mindistance=distance[i];
nextnode=i;
}
//check if a better path exists through nextnode
visited[nextnode]=1;
for(i=0;i<n;i++)
if(!visited[i])
if(mindistance+cost[nextnode][i]<distance[i])
{
distance[i]=mindistance+cost[nextnode][i];
pred[i]=nextnode;
}
count++;
}
 
//print the path and distance of each node
for(i=0;i<n;i++)
if(i!=startnode)
{
printf("Distance of node%d=%d\n",i,distance[i]);
printf("Path=%d",i);
j=i;
do
{
j=pred[j];
printf("<-%d",j);
}while(j!=startnode);
}
}

```

## Output:

![437490804-121d86c2-a203-4174-aa9d-5389b62714ef](https://github.com/user-attachments/assets/b63feac2-efd2-4c8d-95eb-30666c561995)


## Result:
Thus, the Program to implement Dijkstra's Algorithm to find the shortest path is implemented successfully.
