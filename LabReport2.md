# Lab Report 2

## Part 1 

![Image](https://github.com/Annabelleteoh/at.github.io/blob/main/Screenshot%202023-04-24%20at%2011.35.16%20PM.png)

#### Which methods in your code are called?
handleRequest, handle, and start
#### What are the relevant arguments to those methods, and the values of any relevant fields of the class?
The relevant arguments to the methods are the path and the query. The relevant field of the class are Strings and the URI.
#### How do the values of any relevant fields of the class change from this specific request? If no values got changed, explain why.
The handleRequest method changes the query; since there is a query found, the query is changed from this specific request.


![Image](https://github.com/Annabelleteoh/at.github.io/blob/main/Screenshot%202023-04-24%20at%2011.35.44%20PM.png)

#### Which methods in your code are called?
handleRequest, handle, and start

#### What are the relevant arguments to those methods, and the values of any relevant fields of the class?
The relevant arguments to the methods are the path and the query. The relevant field of the class are Strings and the URI.

#### How do the values of any relevant fields of the class change from this specific request? If no values got changed, explain why.
The handleRequest method only changes the query; thus the values don't change from this request, as there is no query here. 


## Part 2
### Screenshot of code
![Image](https://github.com/Annabelleteoh/at.github.io/blob/main/Screenshot%202023-04-24%20at%2011.26.15%20PM.png)

### Failure inducing input
{1,3,0}
### An input that doesn't induce a failure
{3}
### Symptom
assertArrayEquals for {1,3,0} fails, expected is {0,3,1}, but it is actually {0,3,0}

### Bug
The new values are being assigned back into the same array.


## Part 3
I learned the different parts of a URL, such as the domain, path, and query. The domain of the URL is the part after the https:// and before the /. The / marks the beginning of the path, and ends at the ?. The ? marks the beginning of the query.
I also learned how to create a web server and how to manipulate its behavior based on the path and query given. 
