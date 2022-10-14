# Week 3 Lab Report

## Part 1

---
In the week 2, I made a simple search engine:
```
import java.io.IOException;
import java.net.URI;
import java.util.ArrayList;

class Handler implements URLHandler {
    ArrayList<String> list = new ArrayList<>();

    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            String str = "";
            for(int i = 0; i < list.size(); i++){
                str += list.get(i) + " ";
            }
            return str;
        } else if (url.getPath().equals("/add")) {
            String[] parameters = url.getQuery().split("=");
            if (parameters[0].equals("s")) {
                    list.add(parameters[1]);
                    return parameters[1] + " added into the server!";
                }
            return "404 Not Found!";
        } else {
            if (url.getPath().contains("/search")) {
                String[] parameters = url.getQuery().split("=");
                if (parameters[0].equals("s")) {
                    String str = parameters[1];
                    String temp = "";
                    for(int i = 0; i < list.size(); i++){
                        if(list.get(i).contains(str)){
                            temp += list.get(i) + " ";
                        }
                    }
                    return temp;
                }
            }
            return "404 Not Found!";
        }
    }
}

class SearchEngine {
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
![image](/lab-report-1-week-3-folder/001.png)

* handleRequest(URI url) was called
* Since url.getPath() is `"/"`, the method returns a String that contains all elements in `list` in this class. In this case, `list` has no value, therefore there is nothing showing on the webpage
* No value is changed during this call

![image](/lab-report-1-week-3-folder/002.png)

* handleRequest(URI url) was called
* Since url.getPath() is `"/add?s=application"`, the method takes the Query of the url, which is `"s=application"`. Then the method add the String after the equal sign to `list` and it returns a String that shows the String has added to `list` successfully
* `"application"` was added to `list` during this call

![image](/lab-report-1-week-3-folder/005.png)

* After adding several String into `list`, the main page shows Strings that are in the `list`

![image](/lab-report-1-week-3-folder/006.png)

* handleRequest(URI url) was called
* Since url.getPath() is `"/search?s=pple"`, the method takes the Query of the url, which is `"s=pple"`. Then the method loops through the entrie `list` and return a String that shows all Strings in the `list` that contains the keyword `"pple"`
* No value is changed during this call

![image](/lab-report-1-week-3-folder/007.png)

* handleRequest(URI url) was called
* Since url.getPath() is `"/ls"`, which does not meet any situation in the method, so the it returns a String that shows `"404 Not Found!"`
* No value is changed during this call

## Part 2
___
For reversed() method in ArraysExamples.java
![image](/lab-report-1-week-3-folder/reversedTest.png)

I passed an array of {3, 5, 6, 7, 8, 9} as the failure-inducing input. 
The symptom is shown as:
![image](/lab-report-1-week-3-folder/reversedSymptom.png)

The failing test output is an array of {0, 0, 0, 0, 0, 0}. Let's look at the code of the method reversed():
![image](/lab-report-1-week-3-folder/reversedOriginalCode.png)

This method creates a new int array with the length of the original array, and then assign the inverse order of the elements in the new array to the each element in the original array. Finally, it returns the original array. 

The new array has all zeros when it was created. Then, its values were assigned to the original array, which causes the method return an array that has all zeros.
![image](/lab-report-1-week-3-folder/reversedFixedCode.png)

One simple way to fix this bug is to swap the new array and the original array of the code that inside the for loop. Making the method to assign the inverse order of the original array to the new array and then return the new array.

___
For merge() method in ListExamples.java
![image](/lab-report-1-week-3-folder/mergeTest.png)

I passed two arraylists into merge() as the failure-inducing input. 
The symptomp is shown as;
![image](/lab-report-1-week-3-folder/mergeSymptom.png)

It falls into an infinite loop. Let's look at the code of merge():
![image](/lab-report-1-week-3-folder/mergeOriginalCode.png)

In this test case, the method falls into an infinite loop in the thrid while loop. It just keeps adding `index1` by 1 and adding the element at the index 1 of `list2` into the arraylist `result`.
![image](/lab-report-1-week-3-folder/mergeFixedCode.png)

To fix this bug, just change the adding 1 to the `index1` to `index2` in the thrid while loop.


