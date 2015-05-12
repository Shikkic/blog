---
title: "Let's talk about BIG-O"
---

Ever hear anyone mention Big-O notation, or the complexity of certain alogorithems or programs? No idea what they're talking about? In this tutorial we'll talk all about how we understand complexity in programs and more!

## Big-O-Notation
In the computer science field you may have heard people discussing the complexity of a program. In fact effiency is usually always a key component of design in software development. To put it simply Big-O-Notation is an exention of this concept.

>  Big-O-Notation is a way to measure how well a computer algorithem scales as the amount of data changes

**Its that simple.** Lets look at the mathamatical formula below to give us an idea of how certain exponents can weigh more heavily on the final anwser than other figures in an equation.

```
(n = 1)
n^3 + n^2 + 15 = 17
```

You can see that that ``15`` makes up a very large portion of the answer when ``n = 1``.

```
(n = 2)
n^3 + n^2 + 15 =  27
```
Now we see that ``15`` still makes up about half of our answer when ``n = 2``. Now lets look when ``n`` is a bit higher. 

```
(n = 5)
n^3 + n^2 + 15 = 165
```
Now when we can see that ``15`` is no longer making much of an impact in our answer as opposed to ``5^3 + 5^2 = 150``. **However will n^2 even matter before long?**

```
(n = 10)
n^3 + n^2 + 15 = 1115  
```

> As the equation approaches higher values of ``n`` we notice a trend. The *highest* exponential value has the highest impact on our answer. ``10^3 = 1115`` **This is called an order of magnitude**, for this equation its ``O(n^3)``.


###Here is an example of a few significant orders of magnitude

- O(1) _constant time_ **Very Good** 
- O(log n) **Good**
- O(n) **Fair**
- O(n log n) **Bad**
- O(n^2) **Very Bad**

So now lets take a look at some Java code examples of the above order of magnitudes.

### O(1)

If we have an insertion algorithm for a linked list what would the order of magnitude be?

{% highlight java%}
public void insert(LinkedList L, int input) {
    LinkedList newNode = new LinkedList(input);
    L.link = newNode;
}
{% endhighlight %}

If you understand how Linked Lists work the above example is easy to undersand. It takes exactly **O(1)** time, or _constant_ time to execute. There is no traversal of elements, so there is no implication when we scale our elements from 1 to 1 million!

### O(n)

If we had a simple algorithem that looped through every element of an array what would the order of magnitude be?

{% highlight java %}
int[] numbers = [1,2,3,4,5];

for(int i = 0; i < (numbers.length - 1); i++) {
    System.out.println("Index["+i+"] = " + numbers[i]);
}
{% endhighlight %}

Since we loop for every ``n`` elements in the array, our magnitude would always be **O(n)**.  

### O(log n)

For **O(log n)** lets use an example invloving binary trees. One of the aspects that makes these Data Structures useful and unqiue is traversal at worst possible case takes **O(log n)**. This is stricly because of its structure. Lets take a look.

> If you did not know already Binary tree structures consist of Nodes. Each node has two children, that are also nodes. In our case we will store integers in our nodes. Lastly we will store the nodes by using an algorithm that puts numbers less than the node we compare it to, to the left, and numbers greater than to the right child of the node we are on.

{% highlight java %}
//A Binary tree is made up of nodes that have at most two children, a left child and a right child.
class BinaryNode {
    int info;
    BinaryNode left;
    BinaryNode right;
    public BinaryNode(int input) {
        info = input;
        left = NULL;
        right = NULL;
    }
}
public boolean searchBinaryTree( int input ){ 
    BinaryNode node = root;
    while(Node != NULL) {
        //if the number we want to look for is greater than the node we are on, make node point to the right child
        if(info > node.info) {
            node = node.right;
        }//if the number we are looking for is less than the node we are on, we make node point to the left child 
        else if {
            node = node.left;
        }// if it's not less than or greater than, and it's not NULL, it must be equal so we return true!
        else {
            return true;
        }
    }
    //if we traverse until the end and have not found the number we are looking for we return false
    return false;
}
{% endhighlight %}

### O(n log n)

### O(n^2)



