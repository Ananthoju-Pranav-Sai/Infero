# C++ Library
## **The C++ Standard Template Library (STL)**
The Standard Template Library, or STL, is a C++ library of container classes, algorithms, and iterators; it provides many of the basic algorithms and data structures of computer science. It is a generalized library and so, its components are parameterized: almost every component in the STL is a template.

As mentioned earlier **STL has four components**
- Containers
- Iterators
- Algorithms
- Functions

### **Containers**
The containers are objects that store data. The STL contains three types of containers they are
- Sequential Containers
- Associative Containers
- Derived Containers

#### **Sequential Containers :**
In sequential containers elements can be accessed sequentially. We will discuss the following containers which are defined in the current revision of the C++ standard :
- array
- vector
- deque

#### **Array** :
Array class in STL is a better alternative for C-style arrays. The advantages of array class over C-style array are :-
- Array classes knows its own size, whereas C-style arrays lack this property. So when passing the array to the functions, we dont need to pass size of Array as a separate parameter.
- With C-style array there is more risk of array being decayed into a pointer (i.e., loss of type and dimensions of an array). Array classes don't decay into pointers.
#### Operations on array :-
1. **at()** :-   used to access the elements of array.
2. **operator[]** :-   similar to C-style arrays this method is also used to access array elements.
3. **front()** :- returns the first element of array.
4. **back()** :- returns the last element of array.
5. **size()** :- returns the number of elements in the array.
6. **empty()** :- returns true when array size is zero.
7. **fill()** :- fills the entire array with specified value.

```
#include <iostream>
#include <array>

using namespace std;

int main()
{
    array<int,7> ar = {10,20,30,40,23,12,11};   //array initialization
    array<int,7> ar1;

    cout << ar.at(5) <<"\n";   

    cout << ar[5] <<"\n";  

    cout << ar.front() << "\n";

    cout << ar.back() << "\n";   

    cout << ar.size() << "\n";    

    ar1.empty()? cout << "Array is empty":
        cout << "Array is not empty";       
    cout << "\n";

    ar1.fill(0);       

    for ( int i=0; i<7; i++)
        cout << ar[i] << " ";     
    cout << "\n";

    return 0;
}
```
Output :
```
12
12
10
11
7
Array is empty
0 0 0 0 0 0 0
```
#### **Vector** :
Vectors are sequential containers representing arrays that can change in size or a dynamic array. Just like arrays, elements are stored in contiguous storage locations. In vectors, data is inserted at the end.

#### Operations on vector :-
1. **begin()** - returns an iterator pointing to the first element in the vector.
2. **end()** - returns an iterator pointing to last element in the vector.
3. **size()** - returns the number of elements in the vector.
4. **push_back()** - it pushes the elements into the vector from the back.
5. **pop_back** - it is used to remove elements from vector from the back.
6. **erase()** - it is used to remove elements from a container from the specified position or range.
7. **clear()** - used to remove all elements from the vector.
8. **resize(n)** - resizes the container so that it contains 'n' elements.
9. **empty()** - returns true if vector is empty.
10. **at(g)** - returns the element at position 'g' in the vector.
11. **operator[g]** :- returns the element at position 'g' in the vector.
12. **front()** - returns a reference to the first element in the vector.
13. **back()** - returns a reference to the last element in the vector.

```
#include <iostream>
#include <vector>

using namespace std;

int main()
{
    vector <int> g1;    //initializing vector g1 of type int.

    g1.empty()? cout << "Vector is empty":
        cout << "Vector is not empty";   
    cout << "\n";

    for(int i=1;i<=7;i++)
        g1.push_back(i*10);

    int l = g1.size();

    cout << "Size of the vector is "  << l <<"\n";

    cout << "First and last elements of the vector are " << g1.front() << " " << g1.back() << "\n";

    cout << "Vector : ";
    for(int i=0;i<l;i++)
        cout << g1[i] << " ";
    cout << "\n";

    g1.pop_back();

    cout << "Vector after pop_back() : ";
    for (auto i = g1.begin(); i != g1.end(); i++)
        cout << *i << " ";
    cout << "\n";

    g1.erase(g1.begin()+2);

    cout << "Vector after erasing element at index 2 :";
    for (auto i = g1.begin(); i != g1.end(); i++)
        cout << *i << " ";
    cout << "\n";


    g1.resize(7);

    cout << "Vector after resizing : ";
    for (auto i = g1.begin(); i != g1.end(); i++)
        cout << *i << " ";
    cout << "\n";


    g1.clear();
    cout << "Vector has been cleared\n";

    g1.empty()? cout << "Vector is empty":
        cout << "Vector is not empty";   
    cout << "\n";

    return 0;

}

```
Output :
```
Vector is empty
Size of the vector is 7
First and last elements of the vector are 10 70
Vector : 10 20 30 40 50 60 70
Vector after pop_back() : 10 20 30 40 50 60
Vector after erasing element at index 2 :10 20 40 50 60
Vector after resizing : 10 20 40 50 60 0 0
Vector has been cleared
Vector is empty
```
#### **Deque** :
Deque or double ended queues are sequence containers which can be expanded and contracted from the both ends. They are similar but more efficient than vectors in case of insertion and deletion of elements. Unlike vectors, contiguous storage allocations may not be guaranteed.

Deque has all the functions for vector with an addition of :-
1. **push_front()** - it pushes the elements into the deque from the front.
2. **pop_front()** - it removes elements from the deque from the front.

```
#include <iostream>
#include <deque>

using namespace std;

int main()
{
    deque <int> g;
    g.push_back(10);
    g.push_front(100);
    g.push_back(1000);
    g.push_front(10000);

    cout << "Deque : ";
    for(auto  it=g.begin();it!=g.end();it++)
    {
        cout << *it << " ";
    }
    cout << "\n";

    g.pop_back();
    cout << "Deque after pop_back() : ";
    for(auto  it=g.begin();it!=g.end();it++)
    {
        cout << *it << " ";
    }
    cout << "\n";

    g.pop_front();
    cout << "Deque after pop_front() : ";
    for(auto  it=g.begin();it!=g.end();it++)
    {
        cout << *it << " ";
    }
    cout << "\n";

    return 0;
}
```
Output :
```
Deque : 10000 100 10 1000
Deque after pop_back() : 10000 100 10
Deque after pop_front() : 100 10
```
#### **Associative containers :**
Associative containers is a variable-sized container that supports efficient retrieval of elements. These are sorted data structures so they can be quickly searched(i.e., in
O(log n) complexity).

We will discuss the following containers which are defined in the current revision of the C++ standard :
- Set
- Map

#### **Set** :
Sets are a type of associative containers in which each element has to be unique, because the value of the element identifies. We cannot alter the value of element in the set but we can remove or add the elements to set.

Some basic funtions associated with Set :
1. **begin()** -returns an iterator pointing to the first element in the set.
2. **end()** -returns an iterator pointing to the last element in the set.
3. **size()** -returns the number of elements in the set.
4. **empty()** -returns true if set is empty.
5. **insert(g)** -adds a new element 'g' to the set.
6. **erase(g)** -removes the value 'g' from the set.
7. **clear()** -removes all elements from the set.

```
#include <iostream>
#include <set>

using namespace std;

int main()
{
    set <int> s;    //intialising set
    s.insert(10);
    s.insert(1);
    s.insert(100);
    s.insert(50);
    s.insert(50);   //50 is inserted only once.

    int l=s.size();
    cout << "No of elements in the set are " << l <<"\n";

    cout << "Set : ";
    for (auto it=s.begin();it!=s.end();it++)
    {
        cout << *it << " ";
    }
    cout << "\n";

    s.erase(10);
    cout << "Set after removing 10 : ";
    for (auto it=s.begin();it!=s.end();it++)
    {
        cout << *it << " ";
    }
    cout << "\n";

    s.clear();
    cout << "Set has been cleared\n";

    s.empty()? cout << "Set is empty":
        cout << "Set is not empty";   
    cout << "\n";

}
```
Output :
```
No of elements in the set are 4
Set : 1 10 50 100
Set after removing 10 : 1 50 100
Set has been cleared
Set is empty
```
#### **Map** :
Maps are associative containers that store elements in a mapped fashion i.e., each element has a key value and a mapped value. Key value is unique i.e., no two mapped values can have same key values.

Some basic function associated with Map :
1. **begin()** -returns an iterator pointing to the first element in the map.
2. **end()** -returns an iterator pointing to the last element in the map.
3. **size()** -returns the number of elements in the map.
4. **empty()** -returns true if map is empty.
5. **insert()** -adds a new element to the map.
6. **erase(g)** -removes the key value 'g' from the map.
7. **clear()** -removes all the elements from the map.

Also **it->first** and **it->second** are used to access the key and mapped values respectively where it is a iterator pointing to any of the element in the map.

```
#include <iostream>
#include <map>

using namespace std;

int main()
{
    map <int,int> M;        //intialising map with key and mapped values of type int

    M.insert(pair<int,int>(1,400));
    M.insert(pair<int,int>(9,600));
    M.insert(pair<int,int>(3,300));
    M.insert(pair<int,int>(7,20));
    M.insert(pair<int,int>(8,90));
    M.insert(pair<int,int>(5,30));
    M.insert(pair<int,int>(2,10));

    cout << "Map :\n";
    cout << "KEY\tELEMENT\n";
    for(auto it=M.begin();it!=M.end();it++)
    {
        cout << it->first << "\t" << it->second << "\n";
    }

    int l = M.size();
    cout << "No of elements in the Map M is : " << l << "\n";

    M.erase(8);

    cout << "Map after erasing 8:\n";
    cout << "KEY\tELEMENT\n";
    for(auto it=M.begin();it!=M.end();it++)
    {
        cout << it->first << "\t" << it->second << "\n";
    }

    M.clear();
    cout << "Map has been cleared\n";

    M.empty()? cout << "Map is empty":
        cout << "Map is not empty";   
    cout << "\n";
}
```
Output :
```
Map :
KEY     ELEMENT
1       400
2       10
3       300
5       30
7       20
8       90
9       600
No of elements in the Map M is : 7
Map after erasing 8:
KEY     ELEMENT
1       400
2       10
3       300
5       30
7       20
9       600
Map has been cleared
Map is empty
```
#### **Derived containers :**
#### **Stack** :
Stacks are a type of data structure where a new element is stacked on top of the rest of the elements. It works on the LIFO (Last In, First Out) principle. We can think of it as stacking books on a pile of books.

Some basic function associated with Stack:
1. **empty()** -checks whether the stack is empty or not.
2. **top()** -returns the element present at the top of the stack.
3. **size()** -returns the number of elements in the stack.
4. **push()** -pushes the element on top of the stack.
5. **pop()** -removes the element from the top of the stack.
```
#include <iostream>
#include <stack>
using namespace std;

int main()
{
    //Initializing a stack
	stack<int> s;
	//Pushing the elements in the stack
	s.push(10);
	s.push(15);
	s.push(9);

    cout << "Size of stack: " << s.size() << "\n";
    //Creating a temporary stack
    stack<int> sTemp = s;

    cout << "Elements of the stack: \n";
    while(!sTemp.empty()){
        cout << sTemp.top() << " ";
        sTemp.pop();
    }
    cout << "\n\n";

    s.pop();
    cout << "Size of stack after popping: " << s.size() << "\n";
    cout << "Elements of the stack: \n";
    while(!s.empty()){
        cout << s.top() << " ";
        s.pop();
    }
}
```
Output:
```
Size of stack: 3
Elements of the stack:
9 15 10

Size of stack after popping: 2
Elements of the stack:
15 10
```
#### **Queue** :
Queue is a data structure where a new element is placed at the back of the queue. It follows the FIFO (First In, First Out) principle.

Some basic function associated with Queue:
1. **empty()** -checks whether the queue is empty or not.
2. **front()** -returns the element present at the front of the queue.
3. **size()** -returns the number of elements in the queue.
4. **push()** -pushes the element to the back of the queue.
5. **pop()** -removes the element from the front of the queue.
```
#include <iostream>
#include <queue>
using namespace std;

int main()
{
    //Initializing a queue
	queue<int> q;
	//Pushing the elements in the queue
	q.push(10);
	q.push(15);
	q.push(9);

    cout << "Size of queue: " << q.size() << "\n";
    //Creating a temporary queue
    queue<int> qTemp = q;

    cout << "Elements of the queue: \n";
    while(!qTemp.empty()){
        cout << qTemp.front() << " ";
        qTemp.pop();
    }
    cout << "\n\n";

    q.pop();
    cout << "Size of queue after popping: " << q.size() << "\n";
    cout << "Elements of the queue: \n";
    while(!q.empty()){
        cout << q.front() << " ";
        q.pop();
    }
}
```
Output:
```
Size of queue: 3
Elements of the queue:
10 15 9

Size of queue after popping: 2
Elements of the queue:
15 9
```
### **Iterators**
Iterators are objects which are used to point at the memory addresses of the STL containers. They reduce the time complexity and execution time of program.

#### **Operations of iterators**:-
1. **begin()** -returns the beginning position of the container.
2. **end()** -returns the ending position of the container.
3. **advance()** -is used to increment the iterator position by specified value.
4. **next()** -returns a new iterator which points after advancing the positions mentioned in its arguments.
5. **back()** -returns a new iterator which points after decrementing the positions mentioned in its arguments.

```
#include <iostream>
#include <iterator>
#include <vector>

using namespace std;

int main()
{
    vector <int> ar = {1,2,3,4,5};

    vector <int>::iterator ptr = ar.begin(); //iterator intialisation

    auto itr = ar.begin();      //can also be done this way

    cout << "The position of the iterator is " << *ptr << "\n";

    auto it = next(itr,3);

    cout << "The position of the new iterator using next() is " << *it << "\n";

    advance(itr,3);

    cout << "The position of iterator itr after advancing is " << *itr <<"\n";

    auto it1 = prev(itr,3);

    cout << "The position of the new iterator using prev() is " << *it1 <<"\n";

}
```
Output :
```
The position of the iterator is 1
The position of the new iterator using next() is 4
The position of iterator itr after advancing is 4
The position of the new iterator using prev() is 1
```
We can use the iterators similarly for other containers as well.

### **Algorithms** 
Under the header algorithm there are collection of functions which act on containers and can be used on ranges of elements.

We will discuss the usage of few algorithms under this header.
1. **sort(first_iterator,last_iterator)** -To sort the given vector from first_iterator to last_iterator.

2. **binary_search(first_iterator,last_iterator,x)** -checks whether x exists in the the range [first,last] sorted vector or not.
```
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

int main()
{
    vector <int> v;
    v.push_back(10);
    v.push_back(26);
    v.push_back(18);
    v.push_back(12);
    v.push_back(100);
    v.push_back(90);

    cout << "Vector before sorting : ";
    for(auto it=v.begin();it!=v.end();it++)
        cout << *it << " "; 
    cout << "\n";

    sort(v.begin(),v.end());

    cout << "Vector after sorting : ";
    for(auto it=v.begin();it!=v.end();it++)
        cout << *it << " ";
    cout << "\n"; 

    cout << "Searching for 18 in the vector...\n";
    if(binary_search(v.begin(),v.end(),18))
        cout << "Element found in vector\n";
    else
        cout << "Element not found in the vector\n";
    
    cout << "Searching for 19 in the vector...\n";
    if(binary_search(v.begin(),v.end(),19))
        cout << "Element found in the vector\n";
    else
        cout << "Element not found in the vector\n";
    
    return 0;
}
```
Output :
```
Vector before sorting : 10 26 18 12 100 90 
Vector after sorting : 10 12 18 26 90 100 
Searching for 18 in the vector...
Element found in the vector
Searching for 19 in the vector...
Element not found in the vector
```
3. **max_element(first_iterator,last_iterator)** -returns an iterator pointing the maximum element of the vector in the range [first,last]
4. **min_element(first_iterator,last_iterator** -returns an iterator pointing the minimum element of the vector in the range [first,last]
```
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

int main()
{
    vector <int> v;
    v.push_back(10);
    v.push_back(26);
    v.push_back(18);
    v.push_back(12);
    v.push_back(100);
    v.push_back(90);

    cout << "Vector : ";
    for(auto it=v.begin();it!=v.end();it++)
        cout << *it << " ";
    cout << "\n"; 

    auto max_itr = max_element(v.begin(),v.end());
    cout << "Maximum element in the vector : " << *max_itr << "\n";
     
    auto min_itr = min_element(v.begin(),v.end());
    cout << "Maximum element in the vector : " << *min_itr << "\n";
    
    
    return 0;
}
```
Output :
```
Vector : 10 26 18 12 100 90 
Maximum element in the vector : 100
Maximum element in the vector : 10
```
5. **lower_bound(first_iterator,last_iterator,x)** -returns an iterator pointing to the first element in the vector in the range [first,last] whose value is not less than 'x'.
6. **upper_bound(first_iterator,last_iterator,x)** -returns an iterator pointing to the first element in the vector in the range [first,last] whose value is greater than 'x'.
```
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

int main()
{
    vector <int> v;
    v.push_back(10);
    v.push_back(26);
    v.push_back(12);
    v.push_back(12);
    v.push_back(100);
    v.push_back(90);

    sort(v.begin(),v.end());

    cout << "Vector after sorting : ";
    for(auto it=v.begin();it!=v.end();it++)
        cout << *it << " ";
    cout << "\n"; 

    auto lb = lower_bound(v.begin(),v.end(),12);

    auto ub = upper_bound(v.begin(),v.end(),12);

    cout << "lower bound is at position " << lb-v.begin() << " and is " << *lb << "\n";

    cout << "upper bound is at position " << ub-v.begin() << " and is " << *ub << "\n";
    
    
    return 0;
}
```   
Output :
```
Vector after sorting : 10 12 12 26 90 100 
lower bound is at position 1 and is 12
upper bound is at position 3 and is 26
```
## References and practice problems :

- https://www.hackerrank.com/domains/cpp/stl/page/1
- https://www.hackerearth.com/practice/data-structures/stacks/basics-of-stacks/tutorial/
- https://www.hackerearth.com/practice/data-structures/queues/basics-of-queues/tutorial/
- https://cp.cyberlabs.club/docs/roadmap/stl/stl-problems/