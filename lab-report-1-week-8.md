# Week 8 Lab Report 

```
rm -rf student-submission
git clone $1 student-submission
cp TestListExamples.java student-submission
cp lib/hamcrest-core-1.3.jar student-submission
cp lib/junit-4.13.2.jar student-submission
cd student-submission
CPATH=".:hamcrest-core-1.3.jar:junit-4.13.2.jar"
if [ -f "ListExamples.java" ]
then
    echo ""
else 
    echo "ListExamples.java not found!!! 0/2"
    exit
fi
javac ListExamples.java 2> err.txt > out.txt 
if [ $? -eq 0 ]
then
    javac -cp $CPATH TestListExamples.java 2> err.txt > out.txt
else
    echo "ListExamples.java cannot be compiled!!! 0/2"
    exit
fi

java -cp $CPATH org.junit.runner.JUnitCore TestListExamples 2> err2.txt > out.txt
if [ $? -eq 0 ]
then
    echo "2/2!!!"
    exit
else
    grep -c "error:" err.txt > result.txt
    cat result.txt
    echo "are wrong, total tests: 2!!!"
    exit
fi
```

![image](/lab-report-1-week-8-folder/repo1.png)

![image](/lab-report-1-week-8-folder/repo2.png)

![image](/lab-report-1-week-8-folder/repo4.png)

## Look at the example shown in the second screenshot

At the 1st line of my `grade.sh`, it deletes `stundent-submission` folder and the files in it. There is no standad output or standard error.

At the 2nd line, it copies the submitted files into a folder called `student-submission`.

At the line 3rd, 4th, 5th, it copies the tester, junit test files into `student-submission`.

At the 8th line, there is the first if statement of my code. It checks if the file `ListExamples.java` exist. It is true in this situation. 

If this if statement's condition is false, it will echo "ListExamples.java not found!!! 0/2" and then exit the bash script.

At the 15th line of my code, the standard output and standard error are empty in this example. The exit code is 0.

At the 16th line, since the exit code is zero, the condition is true, so "ListExamples.java cannot be compiled!!! 0/2" will not be echoed. 

At the 18th line, the TestListExamples is complied and there are no standard output and standard error. The exit code is zero.

At the 21st line, since the Tests are all passed, there will not be any standard error, but standard ouput : 
```
JUnit version 4.13.2
..
Time: 0.013

OK (2 tests)
```
The exit code is zero.

At the 22nd line, since the exit code is zero, the condition is true, it will echo "2/2!!!" and then exit the bash script.

The conmmands after line 26th will not be run. 

