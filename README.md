(selectionsort)

#include <stdio.h>
#include <stdlib.h>
#include <time.h>
void selectionSort(int arr[], int n)
{
int temp;
for (int i = 0; i < n - 2; i++)
{
int min_idx = i;
for (int j = i + 1; j < n-1; j++)
{
if (arr[j] < arr[min_idx])
{
min_idx = j;
}
}
temp = arr[i];
arr[i] = arr[min_idx];
arr[min_idx] = temp;
}
}
void generateRandomArray(int arr[], int n)
{
srand(time(NULL));
for (int i = 0; i < n; i++)
{
arr[i] = rand();
}
}int main()
{
int n_values[] = {5000, 10000, 15000, 20000}; 
int num_values = sizeof(n_values) / sizeof(n_values[0]);
double time_taken[num_values];
for (int i = 0; i < num_values; i++)
{
int n = n_values[i];
int *arr = (int*)malloc(n * sizeof(int));
generateRandomArray(arr, n);
clock_t start = clock();
selectionSort(arr, n);
clock_t end = clock();
time_taken[i] = ((double)(end - start)) / CLOCKS_PER_SEC;
free(arr);
}
printf("n\tTime Taken (s)\n");
for (int i = 0; i < num_values; i++) {
printf("%d\t%f\n", n_values[i], time_taken[i]);
}
return 0;
}
#include <stdio.h>
#include <stdlib.h>
#include <time.h>
void selectionSort(int arr[], int n)
{
int i, j, min_idx, temp;
for (i = 0; i < n-1; i++)
{
min_idx = i;
for (j = i+1; j < n; j++)
{
if (arr[j] < arr[min_idx])
{
min_idx = j;
}
}
temp = arr[min_idx];
arr[min_idx] = arr[i];
arr[i] = temp;
}
}
int main()
{
int n, i;
printf("Enter the number of elements: ");
scanf("%d", &n);
int arr[n];
srand(time(NULL));
printf("Generated array: ");
for (i = 0; i < n; i++)
{
arr[i] = rand() % 100; 
printf("%d ", arr[i]);
}
selectionSort(arr, n);
printf("\nSorted array: ");
for (i = 0; i < n; i++)
{
printf("%d ", arr[i]);
}
printf("\n");
return 0;
}
