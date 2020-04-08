# Dynamic Queue Optimisation

### I. Introduction

I worked on the implementation of a dynamic queue for a game engine developed in C++. The queue is used to store elements of type T ( which means any type wanted by the user). They are based on the principle FIFO ( First In, First Out), which means that the first element who are push in the queue will be the first one to be out from the queue.
I have implemented two versions of the dynamic queue. The first one is the basic dynamic queue, this queue is a vector of type T which will move every element of the vector each time an element is a pop, and when you will add an element in this queue he is gonna be added at the end of the vector. The second queue is the optimized dynamic queue, it is also a vector of type T but there are two more variables called start and end, those two variable are the index of the front and the back of the queue, each time a value is pop from the queue the operation start++ is done, and when an element is pushback into the queue the operation end++ is done and if end is bigger than the actual capacity of the vector and start is not equal to zero then end will be zero, this method will refill the unused elements of the vector instead of increasing the capacity of the vector.



### II. Basic dynamic queue



Here are the function of the basic dynamic queue :

>void PushBack(T element)
>void Clear()
>T Pop()
>T Front()
>T Back()
>int Size()
                    
In this queue the PushBack() function only adds the element pushed in the last position of the queue.

The Clear() function clear the vector of all the elements inside him.

The Pop() function returns the element at the index zero of the vector and every element of the vector move from one place to the front of the vector.

The Front() function returns the element at the index zero of the vector.

The Back() function returns the element at the last index (found by doing Size()-1) of the vector.

The Size() function returns the size of the vector.



### II. Optimized dynamic queue



Here are the functions of the optimized dynamic queue :

>void PushBack(T element)
>void Clear()
>T Pop()
>T Front()
>T Back()
>int Size()
>void Rebase()
                    
you will also need two variables that are gonna be the index of the first and the last elements of the queue.

>size_t start _= 0, end_ _= 0;
                    

In this queue the PushBack() function is more complicated, the element pushed is assigned to the index end of the vector and the operation end ++ is done, after this operation if the value of the number of elements in the queue ( calculated by doing start-end+1) is less the size of the queue, the function Rebase() is called and the vector is resized to the value of the number of elements in the queue

The Clear() function clears the vector of all the elements inside him and changes the value of the start and end variables to zero.

The Pop() function returns the value at the index start of the vector and does the operation start++, and if after this operation the value of start is bigger than the size of the vector, the value zero is assigned to the start variable.

The Front() function returns the value at the index start.

The Back() function returns the value at the index end after doing the operation end -1 only if the end value is not equal to zero, but if end is equal to zero it returns the value at the index end without doing the operation end -1.

The Size() function returns the size of the queue by doing the operation start- end + 1
or end - start + 1 depending on which one of the variables has the biggest value.

The Rebase() function is gonna rebase all the element at the right place, the element at the start index will be at the front of the vector and all the element after the one who is at the start index will be after him and the last one will be the value at the index end of the vector, and then the vector is resized.
