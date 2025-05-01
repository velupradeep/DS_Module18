# Ex29 Travelling Salesman Problem
## DATE: 01/05/2025
## AIM:
To write a C Program to implement Travelling Salesman Problem for finding shortest path.
## Algorithm
1.List all cities and distances between each pair:

Represent the problem as a graph with cities as nodes and distances as edge weights.

2.Generate all possible permutations of cities:

Create all possible orders in which the cities can be visited (except the starting city is fixed to reduce duplicates).

3.Calculate total distance for each permutation:

For each route, calculate the total travel distance (including the return to the starting city).

4.Track the minimum distance found so far:

Compare distances of each route to keep track of the shortest one.

5.Repeat until all permutations are checked:

Continue checking all combinations to ensure the optimal solution is found.

6.Return the route with the minimum total distance:

This is the shortest possible tour that visits every city once and returns to the start.


## Program:
```
/*
Program to implement Travelling Salesman Problem for finding shortest path
Developed by: PRADEEP V
RegisterNumber: 212223240119
*/
#include<stdio.h>
int a[10][10],visited[10],n,cost=0;

void get()
{
	int i,j;
		scanf("%d",&n);
	for(i=0;i < n;i++)
	{
			for( j=0;j < n;j++)
			scanf("%d",&a[i][j]);
		visited[i]=0;
	}
	}

void mincost(int city)
{
	int ncity;
	int least(int);
	visited[city]=1;	
	printf("%d -->",city+1);
	ncity=least(city);
	if(ncity==999)
	{
		ncity=0;
		printf("%d",ncity+1);
		cost+=a[city][ncity];
		return;
	}
	mincost(ncity);
}

int least(int c)
{
	int i,nc=999;
	int min=999,kmin;
	for(i=0;i < n;i++)
	{
		if((a[c][i]!=0)&&(visited[i]==0))
			if(a[c][i] < min)
			{
				min=a[i][0]+a[c][i];
				kmin=a[c][i];
				nc=i;
			}
	}
	if(min!=999)
		cost+=kmin;
	return nc;
}

void put()
{
	printf("\n\nMinimum cost:%d",cost);
	}

int main()
{
	get();
	mincost(0);
	put();
	return 0;
	}

```

## Output:

![437492381-cba89abe-c91d-4dd9-9101-0b6508c93555](https://github.com/user-attachments/assets/2f6c1ae9-f35d-4a28-82d5-6552544c9e6d)


## Result:
Thus, the C program to implement Travelling Salesman Problem for finding shortest path is implemented successfully.
