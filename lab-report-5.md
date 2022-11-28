## Code Overview
Here is my code for ```grade.sh```:

# Create your grading script here

    set -e

    CPATH="student-submission/ListExamples.java"
    JUNITPATH=".:../lib/hamcrest-core-1.3.jar:../lib/junit-4.13.2.jar"

    rm -rf student-submission
    git clone $1 student-submission

    if [[ ! -f $CPATH ]]
    then
        echo "ListExamples.java wasn't found :("
        exit
    else 
        echo "student-submission was cloned successfully :)"
    fi

    set +e 

    cp TestListExamples.java student-submission
    cd student-submission

    javac -cp $JUNIT_PATH *.java 2> juniterr.txt

    if [[ $? -eq 0 ]]
    then
        echo "Compilation was a success :)"
    else
        echo "ListExamples.java failed to compile :/"
        exit
    fi

    java -cp $JUNIT_PATH org.junit.runner.JUnitCore TestListExamples 2> junitout.txt

    if [[ $? -ne 0 ]]
    then
        echo "Some tests failed :,("
        FAILURE=$(grep "Failures: " junitout.txt)
        SCORE=$((5-$FAILURE))
        echo $SCORE "/5"
    else
        echo "All tests passed!"
        echo "Score: 5/5 :)"
    fi

Here is my output for https://github.com/ucsd-cse15l-f22/list-methods-compile-error
![no-compile](/lab-report-5/5-failed-to-compile-2.png)

Here is my output for https://github.com/ucsd-cse15l-f22/list-methods-nested
![not-found](/lab-report-5/5-not-found.png)

Here is my output for https://github.com/ucsd-cse15l-f22/list-methods-corrected
![all-good](/lab-report-5/5-all-good.png)

## Code Trace

Here is the code trace for Example 2, where the file wasn't found. 
- ```rm -rf student-submission```
    - This deletes the entire student-submission file from list-example-grader. Once the command is executed successfully, the entire folder is removed.
- ```git clone```
    - exit code: 0 (executed successfully)
    - standard output: 
        
            Cloning into 'student-submission'...
            remote: Enumerating objects: 3, done.
            remote: Counting objects: 100% (3/3), done.
            remote: Compressing objects: 100% (2/2), done.
            remote: Total 3 (delta 0), reused 3 (delta 0), pack-reused 0
            Receiving objects: 100% (3/3), done.
    - standard error: there is none
- ```-f```
    - exit code: 1
    - standard output: none
    - standard error: none
    - This checks to see whether the file exists. Since, in example 2, the file can't be found, this command will fail. 

Since this command failed, we exit the code and none of the following lines are executed. 
