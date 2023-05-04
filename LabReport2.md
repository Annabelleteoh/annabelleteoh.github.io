# Lab Report 2

## Part 1 

StringServer code: 

```
import java.io.IOException;
import java.net.URI;

class Handler implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.

    String str = "";
    public String handleRequest(URI url) {
        if(url.getPath().contains("/add-message")) {
            
            String[] params = url.getQuery().split("=");
            
            if(params[0].equals("s")){
                str = str + "\n" + params[1];
                return str;
            }
            
            return "404 Not Found!";
        }

        return "404 Not Found!";
    }
}

class StringServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}

```

![Image](https://github.com/Annabelleteoh/at.github.io/blob/main/Screenshot%202023-04-24%20at%2011.35.16%20PM.png)
In this usage of the /add-message path, the getQuery() and split() methods are called. The split() method splits the query (everything after the "?") into two strings in a String array. If the 0th parameter in the array is 's', it will add the string in the 1st parameter to the message.

![Image](https://github.com/Annabelleteoh/at.github.io/blob/main/Screenshot%202023-04-24%20at%2011.35.44%20PM.png)
In this usage of the /add-message path, the getQuery() and split() methods are not called because a query isn't given. Instead, a 404 error message is returned. Though it is not shown in this screenshot, if a query is given, but the 0th parameter in the query array is not 's', a 404 error message will also be returned.




## Part 2
### Screenshot of code
![Image](https://github.com/Annabelleteoh/at.github.io/blob/main/Screenshot%202023-04-24%20at%2011.26.15%20PM.png)

### Failure inducing input & an input that doesn't induce a failure

#### Inputs:
- Failure incuding input: {0,3,1}
- Input that doesn't induce a failure: {3}

#### Test:

```
public class ArrayTests {
	@Test 
	public void testReverseInPlace() {
    int[] input1 = { 3 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 3 }, input1);

    int[] input2 = {0,3,1};
    ArrayExamples.reverseInPlace(input2);
    assertArrayEquals(new int[]{1,3,0}, input2);
 
	}
```
#### Symptom: 
assertArrayEquals for {0,3,1} fails, arrays first differed at element [2]; expected:[0] but was:[1]![Image](https://github.com/Annabelleteoh/at.github.io/blob/main/Screenshot%202023-05-04%20at%201.40.17%20PM.png)


### Bug
The symptom is showing up because the new values are being assigned back into the same array. For example, after the first iteration of the loop, the initial array will be {1,3,0}. By the third iteration of the loop, the value at index 0 will be set to the new value at index 0, rather than the initial value, thus producing the error shown above. I fixed the bug by instantiating a new array by which I stored the new values, and assigned the the values of the new array into the initial array so that the initial values are not lost.

#### Code before fix

```
 static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
```

#### Code after fix

```
static void reverseInPlace(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i++) {
      newArray[i] = arr[arr.length - i - 1];
    }
    
    for(int i = 0; i < arr.length; i++){
      arr[i] = newArray[i];
    }
    
  }
```


## Part 3
I learned the different parts of a URL, such as the domain, path, and query. The domain of the URL is the part after the https:// and before the /. The / marks the beginning of the path, and ends at the ?. The ? marks the beginning of the query.
I also learned how to create a web server and how to manipulate its behavior based on the path and query given. 
