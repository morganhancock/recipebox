# Exercise 2: Merging branches
> **Cooks:** 2+ **Goal:** Multiple cooks add new recipes and edit existing recipes without conflict.

If you didn't complete [Exercise 1: Sharing a branch](Merging_exercise_1.md), stop and go do that! This exercise builds on work done in Exercise 1.

Will this line throw an error?

Developers working in the same branch are like cooks working in the same kitchen—while they might get in each other's way, it's easy to see what's going on.

But imagine if you could cook a meal with someone else, but have your own, separate workspace. You'd have complete control over your kitchen—your development environment—and you wouldn't have to worry too much about the other cook messing up your dish while you're working on it. You only have to worry about combining your dishes into a meal after you've cooked them.

In Git, branches are like private kitckens. They're independent development environments.

## 2.1 Getting updates from another branch
Sometimes you need to get updates from another branch. Let's do that.

### Cook #1
First you need to set up your own private kitchen. Do the following to create a new branch.

1. Start from a `MASTER` branch. If you're on another branch enter `git push MASTER`. 
2. Create and checkout a new branch by entering `git checkout -b breakfast`.

You just created a new branch that, right now, matches the `MASTER` branch. It doesn't contain the commits (the new recipes and changes to existing recipes) from Exercise 1.

Now let's add a new recipe.

1. Open a text editor and paste the following.
 ```
![recipe image](https://static01.nyt.com/images/2014/04/03/dining/All-Purpose-Biscuits/All-Purpose-Biscuits-articleLarge.jpg)

# All-Purpose Biscuits
Biscuits are what take us into the kitchen today to cook: fat, flaky mounds of quick bread, golden brown, with a significant crumb. Composed of flour, baking powder, fat and a liquid, then baked in a hot oven, they are an excellent sop for sorghum syrup, molasses or honey. They are marvelous layered with country ham or smothered in white sausage gravy, with eggs, with grits. Biscuits are easy to make.

## Ingredients
* 2 cups all-purpose flour, plus more for dusting
* 2 tablespoons baking powder
* 1 scant tablespoon sugar
* 1 teaspoon salt
* 5 tablespoons cold, unsalted butter, preferably European style
* 1 cup whole milk

## Steps
1. Preheat oven to 425. Sift flour, baking powder, sugar and salt into a large mixing bowl. Transfer to a food processor. Cut butter into pats and add to flour, then pulse 5 or 6 times until the mixture resembles rough crumbs. (Alternatively, cut butter into flour in the mixing bowl using a fork or a pastry cutter.) Return dough to bowl, add milk and stir with a fork until it forms a rough ball.
2. Turn the dough out onto a well-floured surface and pat it down into a rough rectangle, about an inch thick. Fold it over and gently pat it down again. Repeat. Cover the dough loosely with a kitchen towel and allow it to rest for 30 minutes.
3. Gently pat out the dough some more, so that the rectangle is roughly 10 inches by 6 inches. Cut dough into biscuits using a floured glass or biscuit cutter. Do not twist cutter when cutting; this crimps the edges of the biscuit and impedes its rise.
4. While the pasta and sausage cook, whisk together the eggs, cheese and pepper.
5. Drain the pasta, reserving a 1/3 cup of the starchy water. Add the pasta to the sausage mixture, tossing well to coat.
6. Place biscuits on a cookie sheet and bake until golden brown, approximately 10 to 15 minutes.
```
2. Save the file as `biscuits.md` in the `breakfast` folder. 
3. Add and commit the new recipe using `git add -A` followed by `git commit -am "<your commit message>"`. Make sure you replace `<your commit message>` with a descriptive commit message!
4. Push to the remote repo using `git push`.

### Cook #2
You're going to keep working in the branch created in Exercise 1, `new_recipes`. You want to get Cook #1's biscuit recipe and use it in your kitchen. Do the following to get it.

1. Start from the `new_recipes` branch. If you're on another another branch enter `git checkout new_recipes`.
2. Enter `git merge breakfast`.

### Summary
Cook #1 created a new development environment, `breakfast`, that matched the `MASTER` branch. This branch didn't contain any of the new recipes or updates created in Exercise 1. Cook #1 added a new biscuit recipe to the `breakfast` branch. 

Cook #2 was able to pull that biscuit recipe into the `new_recipes` branch. But why would Cook #2 add the biscuit recipe to `new_recipes` instead of `MASTER`? 

Cook #2 may choose this workflow for many reasons, like if the cooks want to release all new recipes at the same time. In that case, the cooks will add all of their new recipes and changes to `new recipes`, even if they decide to cook in a different kitchen (develop in a different environment). 

## 2.2 Merging into the MASTER branch
Let's say that the cooks don't want to release a new batch of recipes all at once; they want to release new content as soon as it's developed. Let's see how that would work.

### Cook #1 (or any cook)
In the previous section, Cook #1 created a new branch, `breakfast`, and added a new recipe to it, `biscuits.md`. To release that recipe right away, instead of waiting for the `new_recipes` to release, Cook #1 needs to merge into a `MASTER` branch. You can merge locally or through a pull request, so choose one of the following.

#### Merging locally
If your team is cool with merging into MASTER locally, do the following.

1. Start from the `breakfast` branch. If you're on another branch enter `git checkout breakfast`.
2. Enter `git pull MASTER` to make sure `breakfast` isn't missing anything newly adde to `MASTER` (remember what you learned in Exercise 1)!
3. Enter `git checkout MASTER` to switch to the `MASTER` branch. 
  
  Why? You want `MASTER` to have the biscuit recipe that's in `breakfast`, so you need to switch to `MASTER` before merging.
4. Enter `git merge breakfast`.

The `MASTER` branch in your **local** repository now contains commits made in `breakfast` (the new biscuit recipe). Update the remote `MASTER` branch by entering `git push`. You can then delete `breakfast` by entering `git branch -d breakfast`.

#### Merging through a pull request
If your team is a little more strict about merging into the MASTER branch, do the following to submit a pull request.

1. Start from the `breakfast` branch. If you're on another branch enter `git checkout breakfast`.
2. Enter 
q
`git pull MASTER` to make sure `breakfast` isn't missing anything newly added to `MASTER` (remember what you learned in Exercise 1)!
3. Enter `git push` to make sure the remote branch is up-to-date.
4. In your web browser, go to <https://github.com/morganhancock/recipebox/pull/new/MASTER>.
5. In the **base:** drop down select `MASTER` and in the **compare** drop down select `breakfast`.
6. Update the pull request details if desired, then click the **Create pull request button**.

Someone else on your team can then review your pull request and merge it.

## 2.3 Merging into MASTER when MASTER has changed

## 2.4 Undoing a merge, but saving it for later
But I want to keep this commit.
But now I want that old commit back.

## 2.5 Merging a *really* old branch
I don't want this commit.
Let's try some other changes now.
And now I want to keep going. 