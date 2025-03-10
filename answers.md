# Quiz questions

This is only a "quiz" in the loosest sense that it's asking questions whose
answers will be part of your grade. Please use *any resources you want*, as
long as you list those resources (e.g. peers, websites, etc.)

## Navigating logs

1. What is the SHA for the last commit made by Prof. Xanda on the branch
xanda_0000_movie_processing?
(For this and future questions, the first 5 characters is plenty - neither
Git nor I need the whole SHA.)

9b257

2. What is the SHA for the last commit associated with line 9 of this file?

d1d83

3. What did line 12 of this file say in commit d1d83?

2. I should really finish writing this.

4. What changed between commit e474c and 82045?

The gross_sort function in process_movie_data.py is now specified to be an int.
gross_sort = lambda x : x["Gross"] -> gross_sort = lambda x : int(x["Gross"])

The index or rows for top_five changed from -5 to -6.
top_five = rows[:-5:-1] ->  top_five = rows[:-6:-1]

## Predicting merges

Assume at the start of each of these three questions that your
branch for switching to a top-10 list was called `top_ten`
and your branch generalizing to any number of movies was called `top_N`.
Predict the behavior of these three possible operations - you don't
have to provide a full `diff` but you should describe at a high level
what changes would happen.

These questions are supposed to be separate paths, not cumulative;
for example, you should *not* assume that the operations of 5 were run
before 6. When testing outcomes later in the lab, you should make sure to
revert back to the state of the branch before you started these questions.

5. What do you think would happen if you ran the following commands?
What branches would change, and how?
```
git checkout test
git merge top_N
```
The "test" branch changes to incorporate the changes from the "top_N" branch. The "test" branch is updated to have the find_top_N function in process_movie_data.py instead of find_top_5.

6. What do you think would happen if you ran the following commands?
What branches would change, and how?
```
git checkout top_ten
git merge test
```
The "top_ten" branch changes to incorporate the changes from the "test" branch. The "top_ten" branch is updated to have quiz.md be named answer.md.

7. What do you think would happen if you ran the following commands?
What branches would change, and how?
```
git checkout test
git rebase top_ten
git rebase top_N
```

The "test" branch first changes find_top_5 to find_top_10 from the "top_ten" branch. Then, when we rebase top_N, the "test" branch has a merge conflict in process_movie_data.py between the find_top_10 function and find_top_n function. We have to manually approve or reject the incoming changes and then call "git rebase --continue" to resolve the merge conflict.