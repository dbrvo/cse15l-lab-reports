# Lab Report 4 - Vim (Week 7)
>Daniel Bravo
>
>CSE 15l

## Steps
1. Log into ieng6
   * <img width="1132" alt="image" src="https://github.com/dbrvo/cse15l-lab-reports/assets/87788227/3a25adad-030f-4fab-a15c-62bbb8826965">
   * I typed `ssh dbravo@ieng6.ucsd.edu` `<enter>` to log into my ieng6 account.
3. Clone your fork of the repository from your Github account (using the SSH URL)
   * <img width="397" alt="image" src="https://github.com/dbrvo/cse15l-lab-reports/assets/87788227/6ddea43b-eb9a-43b3-b60e-12906181b065">
   * First I coppied my ssh link from my git hub fork.
   * <img width="906" alt="image" src="https://github.com/dbrvo/cse15l-lab-reports/assets/87788227/61f66886-d4e2-42b2-ae07-b226de0fb1ce">
   * Then I typed `git clone git@github.com:dbrvo/lab7.git` `<enter>` because git@github.com:dbrvo/lab7.git is the SSH URL of my fork.
5. Run the tests, demonstrating that they fail
   * <img width="1132" alt="image" src="https://github.com/dbrvo/cse15l-lab-reports/assets/87788227/126aa0e9-f3d7-462d-abe9-d7e4dc16ea7c">
   * I ran the tests by first typing `cd lab7/` `<enter>` to change my current directory to lab 7
   * I then typed `javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java` `<enter>` and next `java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests` `<enter>` to run the tests, demonstrating that they fail.
7. Edit the code file to fix the failing test
   * <img width="997" alt="image" src="https://github.com/dbrvo/cse15l-lab-reports/assets/87788227/d08e5f94-357b-4483-8440-7c1ded654ec3">
   * I typed `vim ListExamples.java` `<enter>` to open the file in vim
   * Then, with previous knowledge that the error was on line 44, I knew I had to go down 43 lines
   * <img width="461" alt="image" src="https://github.com/dbrvo/cse15l-lab-reports/assets/87788227/7992cedf-95cf-43e6-8735-4cd16bb2f93e">
   * So I press `4` `3` `j` so that I can go down 43 lines.
   * <img width="486" alt="image" src="https://github.com/dbrvo/cse15l-lab-reports/assets/87788227/a884e108-2c08-4f2b-955c-bc3b8f7a6087">
   * Then I pressed `e` and `x` to go to the end of the next word and delete the last character which was "1" in "index1".
   * <img width="478" alt="image" src="https://github.com/dbrvo/cse15l-lab-reports/assets/87788227/46cfec15-6488-4d10-bd29-e7d217de9892">
   * Then I pressed `i` to enter instert mode and pressed `2` and lastly `<esc>` to finally change `index1` into `index2`.
   * <img width="247" alt="image" src="https://github.com/dbrvo/cse15l-lab-reports/assets/87788227/ca9801c3-8130-4474-891d-c2184f631075">
   * Lastly I typed in `:wq` to save the file and exit vim mode.
9. Run the tests, demonstrating that they now succeed
    * <img width="1126" alt="image" src="https://github.com/dbrvo/cse15l-lab-reports/assets/87788227/783cd030-4a30-46f1-bbb7-f162b17c5f2e">
    * Keys pressed: <up><up><up><enter>, <up><up><up><up><enter> The javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java command was 3 up in the search history, so I used up arrow to access it. Then the java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTest command was 3 up in the history, so I accessed and ran it in the same way.
11. Commit and push the resulting change to your Github account (you can pick any commit message!)
    * <img width="627" alt="image" src="https://github.com/dbrvo/cse15l-lab-reports/assets/87788227/07ecc2f1-74af-405d-a621-20124e8aeace">
    * I typed the command `git add ListExamples.java` `<enter>` to add the file that I edited into the commit
    * Then I typed the command `git commit -m "yipee, fixed bug"` `<enter>` to commit the changes and add a message to go along with it
    * Lastly I typed the command `git push` `<enter>` to officially push the edits to my Github account


