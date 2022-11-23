## Code Overview
Here is my code for ```grade.sh```:

    set -e

    CPATH="student-submission/ListExamples.java"
    JUNITPATH=".:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar"

    rm -rf student-submission
    git clone $1 student-submission

    if [[ ! -f $CPATH ]]
    then
        echo "ListExamples.java wasn't found :("
        exit
    fi

    set +e 

    # inspired by https://github.com/phuanh004/list-examples-grader
    mkdir student-submission/lib
    cp lib/* student-submission/lib
    cp *.java student-submission

    cd student-submission

    javac -cp $JUNITPATH ListExamples.java TestListExamples.java 2> junitout.txt
    java -cp $JUNITPATH org.junit.runner.JUnitCore ListExamples TestListExamples 2 > junitout.txt

    if [[ ! $? -ne 0 ]]
    then
        echo "ListExamples.java failed to compile :/"
        exit
    else
        echo "Everything looks good :)"
        exit
    fi

Here is my output for https://github.com/ucsd-cse15l-f22/list-methods-compile-error
![no-compile](/lab-report-5/5-failed-to-compile-2.png)

Here is my output for https://github.com/ucsd-cse15l-f22/list-methods-nested
![not-found](/lab-report-5/5-not-found.png)

Here is my output for https://github.com/ucsd-cse15l-f22/list-methods-corrected
![all-good](/lab-report-5/5-all-good.png)

## Code Trace

Here is the code trace for Example 2, where the file wasn't found. 
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

Since this command failed, we exit the code and none of the following lines are executed. 
