# 2.circular-queue
Operations: Insert 10, 20, 30, 40 → Delete 2 → Insert 50, 60 → Display
#include <stdio.h>

#define MAX 5

int queue[MAX];
int front = -1, rear = -1;

void insert(int value)
{
    if ((rear + 1) % MAX == front)
    {
        printf("Queue Overflow\n");
        return;
    }

    if (front == -1)
    {
        front = 0;
        rear = 0;
    }
    else
    {
        rear = (rear + 1) % MAX;
    }

    queue[rear] = value;
}

void delete()
{
    if (front == -1)
    {
        printf("Queue Underflow\n");
        return;
    }

    printf("Deleted: %d\n", queue[front]);

    if (front == rear)
    {
        front = -1;
        rear = -1;
    }
    else
    {
        front = (front + 1) % MAX;
    }
}

void display()
{
    int i;

    if (front == -1)
    {
        printf("Queue is empty\n");
        return;
    }

    printf("Circular Queue: ");

    i = front;

    while (1)
    {
        printf("%d ", queue[i]);

        if (i == rear)
            break;

        i = (i + 1) % MAX;
    }

    printf("\n");
}

int main()
{
    insert(10);
    insert(20);
    insert(30);
    insert(40);

    delete();
    delete();

    insert(50);
    insert(60);

    display();

    return 0;
}
