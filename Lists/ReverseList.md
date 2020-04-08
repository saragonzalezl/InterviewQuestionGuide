## **Problem**

**Reverse a singly linked list**
___
## **Example:**
![Example.png](https://i.postimg.cc/yxPW8mw8/Example.png)


### **Check-in:**
What would the following list look like reversed as the example above ? { 5, 8, 10, 34 }


___
## **Solution:**

There are two ways to solve this problem, *Iterative* or *Recursive*.

### *Iterative:* 
This method loops through and changes the direction of the links. We must take a destructive approach, meaning we must change the original list in order to get the output we want instead of making an entirely new list and making the copy look like the output we want. By being an iterative solution, it means there is going to be a loop somewhere in our solution. There are five crucial observations we must accomplish:

1. Null the reference of our first node / set *curr.next* to *prev* 
2. Keep a *next* pointer 
3. Keep a *prev* point 
4. Set *prev* pointer to the *curr* node 
5. Advancing the *curr* pointer


- prev → points to node that came before curr
- curr → will point to the first node in our linked list 
- next → represent the link; it can only point to null or to another node
 
 ```
 public Node reverse(Node curr) {
 
	Node prev= null;			// this is because it comes before the first node at the start
	Node next = null; 
	
	while (curr != null) {	       		// we know we reached the the end when curr points to null
		next = curr.next;
		curr.next = prev;		// it is now linking to the first node
		prev = curr;			// now it points to the original first node and will continue as there are 							more iterations of the loop to move
		curr = next;			// now curr points to the new first node 
		}
	return prev;				// prev points to the last node, which was the first node
}
```

**In depth step-by-step illustration:**

![Screen-Shot-2020-04-07-at-7-43-08-PM.png](https://i.postimg.cc/d10d7mM3/Screen-Shot-2020-04-07-at-7-43-08-PM.png)

Here is where the variables are stated


![1.png](https://i.postimg.cc/9MpVrK55/1.png)

First iteration result


![1.png](https://i.postimg.cc/DwdvbSKb/1.png)

Second iteration result


![2.png](https://i.postimg.cc/SxqX5FSC/2.png)

Third iteration result


![3.png](https://i.postimg.cc/tJQRxW7W/3.png)

The output now that we go back to the base case the conditional is not met


**Complexity:**
O(*n*). Assume *n* is the length of the list.


### *Recursive:* 
The key to the recursive method is working backwards. One has to assume the rest of the list has been reversed and tackle reversing the first node first. Therefore, there are five crucial steps:
 
1. Divide the list in two parts - first node and rest of the linked list
2. Store nextNode pointer 			// the second node
3. Set curr.next to null 
4. Reverse rest of list
5. Connect rest of list back to 1st node
 
- curr → points to the first node in the linked list

```
public Node reverse(Node curr) {
	if (curr == null) {			// the easiest case
		return null;
	} else if (curr.next == null) {		// checks to see if it is only one node (base case)
		return curr;			// it is already reversed 
	} else {				// when recursion stops, it is longer than one node 
		Node nextNode = curr.next;
		curr.next = null;		// this way the first node won't point to any nodes
		Node rest = reverse(nextNode); 	// here is where we split 
		nextNode.next = curr;		// connecting back to the first node
		return rest;
		}
	}
```

**In depth step-by-step illustration:**

![7.png](https://i.postimg.cc/Bv8yDzrP/7.png)

This is what the input looks like


![6.png](https://i.postimg.cc/43SGRVgV/6.png)

Making the first node to not point to other nodes


![5.png](https://i.postimg.cc/HscpYSxn/5.png)

Separating the first node from the rest of the list


![4.png](https://i.postimg.cc/jdszB7dM/4.png)

Separating the list into smaller pieces 


![3.png](https://i.postimg.cc/0NHWyCr5/3.png)

Reversing of the pieces, the rest


![Screen-Shot-2020-04-07-at-7-58-52-PM.png](https://i.postimg.cc/WzWpzCRY/Screen-Shot-2020-04-07-at-7-58-52-PM.png)

Reverse has occurred and now the nextNode.next = curr


![1.png](https://i.postimg.cc/1R7Tzsnc/1.png)

Return rest


**Complexity:**
O(*n*). Assume *n* is the length of the list.

___

## **Review:**
Which method is best for solving this problem? Under which circumstance is it better to use iterative or recursive?

___
**Source:**
[Link](https://leetcode.com/problems/reverse-linked-list/)
