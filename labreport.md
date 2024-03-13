# LAB REPORT 5

## Part 1 

CONVERSATION 

User: Hi! I am getting these errors while running these commands. Can you kindly help me out with what the potential issue might be? 

prashamshah@Prashams-MacBook-Pro lab3 % javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar ArrayExamples.java                               
prashamshah@Prashams-MacBook-Pro lab3 % java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ArrayExamples ArrayTests

JUnit version 4.13.2
.E.....
Time: 0.004
There was 1 failure:
1) initializationError(ArrayExamples)
org.junit.runners.model.InvalidTestClassError: Invalid test class 'ArrayExamples':
  1. No runnable methods
        at org.junit.runners.ParentRunner.validate(ParentRunner.java:525)
        at org.junit.runners.ParentRunner.<init>(ParentRunner.java:102)
        at org.junit.runners.BlockJUnit4ClassRunner.<init>(BlockJUnit4ClassRunner.java:84)
        at org.junit.runners.JUnit4.<init>(JUnit4.java:23)
        at org.junit.internal.builders.JUnit4Builder.runnerForClass(JUnit4Builder.java:10)
        at org.junit.runners.model.RunnerBuilder.safeRunnerForClass(RunnerBuilder.java:70)
        at org.junit.internal.builders.AllDefaultPossibilitiesBuilder.runnerForClass(AllDefaultPossibilitiesBuilder.java:37)
        at org.junit.runner.Computer.getRunner(Computer.java:50)
        at org.junit.runner.Computer$1.runnerForClass(Computer.java:31)
        at org.junit.runners.model.RunnerBuilder.safeRunnerForClass(RunnerBuilder.java:70)
        at org.junit.runners.model.RunnerBuilder.runners(RunnerBuilder.java:125)
        at org.junit.runners.model.RunnerBuilder.runners(RunnerBuilder.java:111)
        at org.junit.runners.Suite.<init>(Suite.java:81)
        at org.junit.runner.Computer$2.<init>(Computer.java:33)
        at org.junit.runner.Computer.getSuite(Computer.java:28)
        at org.junit.runner.Request.classes(Request.java:77)
        at org.junit.runner.JUnitCommandLineParseResult.createRequest(JUnitCommandLineParseResult.java:116)
        at org.junit.runner.JUnitCore.runMain(JUnitCore.java:77)
        at org.junit.runner.JUnitCore.main(JUnitCore.java:36)

FAILURES!!!
Tests run: 6,  Failures: 1

prashamshah@Prashams-MacBook-Pro lab3 % 
