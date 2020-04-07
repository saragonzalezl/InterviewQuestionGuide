## **Problem**
Reverse a singly linked list
___
## **Example:**

### **Check-in:**
What would the following list look like reversed as the example above ? { 5, 8, 10, 34 }


___
## **Solution:**

There are two ways to solve this problem, *Iterative* or *Recursive*.

*Iterative:* This method loops through and changes the direction of the links. We must take a destructive approach, meaning we must change the original list in order to get the output we want instead of making an entirely new list and making the copy look like the output we want. By being an iterative solution, it means there is going to be a loop somewhere in our solution. There are five crucial observations we must accomplish:

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
 
	Node prev= null;		// this is because it comes before the first node at the start
	
	Node next = null; 
	
	while (curr != null) {	       // we know we reached the the end when curr points to null
	
		next = curr.next;
		curr.next = prev;		// it is now linking to the first node
		
		
		prev = curr;			// now it points to the original first node and will continue as there are 							more iterations of the loop to move
		
		curr = next;		// now curr points to the new first node 
		
		}
		
	return prev;			// prev points to the last node, which was the first node
	
}
```

**In depth step-by-step illustration:**

