# Ex29 Travelling Salesman Problem
## DATE: 01/05/2025
## AIM:
To write a C Program to implement Travelling Salesman Problem for finding shortest path.
## Algorithm
1.Initialize global variables:

Declare a 2D array a[10][10] to store the cost matrix, an array visited[10] to track visited cities, an integer n for the number of cities, and an integer cost initialized to 0.

2.Define the function get() to read the input data:

Declare local variables i and j as integers.
Read the number of cities n using scanf.
For each city i from 0 to n-1:
For each city j from 0 to n-1:
Read the cost of traveling from city i to city j into a[i][j] using scanf.
Initialize visited[i] to 0 (indicating that the city has not been visited).

3.Define the function mincost(int city) to find the minimum cost path:

Declare a local variable ncity to store the next city.
Call the least(int) function to find the next city with the least cost.
Mark the current city as visited by setting visited[city] to 1 and print the current city (adjusted for 1-based indexing).
If ncity is 999 (indicating no unvisited cities), set ncity to 0 (returning to the starting city) and print it.
Add the cost of traveling from the current city to ncity to the total cost.
Recursively call mincost(ncity) to continue the path.

4.Define the function least(int c) to find the city with the least cost from the current city:

Declare local variables i, nc, min, and kmin.
Initialize nc to 999 and min to 999.
For each city i from 0 to n-1:
If there is a path from city c to city i (i.e., a[c][i] != 0) and city i has not been visited:
If the cost a[c][i] is less than min, update min, kmin, and nc with the current values.
If min is not 999, add kmin to the total cost.
Return nc, the next city to visit.

5.Define the function put() to print the total minimum cost:

Print the total cost using printf.
6.In the main function:

Call the get() function to read the input data.
Call the mincost(0) function to start the path from the first city (index 0).
Call the put() function to display the minimum cost.
Return 0 to indicate successful completion.



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
