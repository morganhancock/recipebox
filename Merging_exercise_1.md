# Exercise 1: Sharing a branch
> **Cooks:** 2+ **Goal:** Multiple cooks add new recipes and edit existing recipes without conflict.

When multiple cooks are in one kitchen, they coordinate to avoid ruining meals and duplicating work. 

The same applies to Git. When multiple people are working in the same development branch, they need to make sure they can share their work correctly. 

Work through the following tasks to discover how to successfully share a branch.

## 1.1 Adding new files
First, have one teammate create a new branch called `new_recipes` and push it to the remote. The following commands should do the trick.

```
git checkout -b new_recipes
git push --set-upstream origin new_recipes
```

The rest of the team can fetch and checkout this branch with `git fetch orign` followed by `git checkout new_recipes`.

Then each cook should do one of the following in the `new_recipes` branch.

### Cook #1
Do the following to add a cookie recipe to the recipe box.

1. Open a text editor and paste the following.

 ```
![recipe image](https://static01.nyt.com/images/2014/04/24/dining/French-TV-Snacks/French-TV-Snacks-articleLarge.jpg)

# Buttery French TV Snacks
Good butter is the key to these easy, delectable cookies. Before the pastry chef Anita Chu began work on her “Field Guide to Cookies” (Quirk Books), she was a Berkeley-trained structural engineer with a baking habit she couldn’t shake. One of her favorite cookies is the croq-télé, or TV snack, a chunky cookie she adapted from the Paris pastry chef Arnaud Larher. “There is no leavening to lift it, no eggs to hold it together,” she said. “It’s all about the butter.”

## Ingredients
* ¾ cup blanched almonds or hazelnuts, lightly toasted and cooled to room temperature
* ½ cup sugar
* ½ teaspoon kosher or flaky sea salt (if using fine or table salt, use 3/8 teaspoon)
* 1 cup all-purpose flour
* 7 tablespoons cold unsalted butter, cut into 1/2-inch pieces.

## Steps
1. Position 2 oven racks in top third and bottom third of oven. Preheat oven to 325 degrees. Line two cookie sheets with parchment paper.
2. In a food processor, grind nuts, sugar and salt to a fine meal. In a mixer, beat flour and butter together on low speed until texture is sandy. Add nut mixture and mix on low until dough starts to form small lumps; keep mixing until dough just holds together when pinched between fingers. Do not use wet fingers: the cookies will collapse.
3. Pinch off about a teaspoon of dough and place in palm of your hand. With tips of fingers, pinch and press dough together until cookie has a flat bottom and pointed top, like a rough pyramid. Cookies need not be perfectly smooth or equal size. Place on parchment about 1 inch apart.
4. Bake about 15 minutes, rotating cookie sheets halfway through. Cookies should be turning golden brown on edges. Cool on sheets 5 minutes, then transfer to wire racks and cool completely before storing in airtight containers up to 1 week.
```
2. Save the file as `buttery_french_cookie.md` in the `snacks` folder. 
3. Add and commit the new recipe using `git add -A` followed by `git commit -am "<your commit message>"`. Make sure you replace `<your commit message>` with a descriptive commit message!
4. Push to the remote repo using `git push`.

### Cook #2
Do the following to add a fried rice recipe to the recipe box.

1. Open a text editor and paste the following.

 ```
# Thai Combination Fried Rice
This dish is loosely based on Thailand’s ubiquitous fried rice dish, kao pad. Usually some kind of animal protein accompanies the rice — squid, crabmeat, ham, chicken, whatever the cook has on hand. My version relies instead on tofu and vegetables; the most important ingredients are the rice itself, the garlic and the fish sauce. Have all of your ingredients prepared and close to the stove. Cooking goes very quickly.

## Ingredients
* 4 tablespoons canola or vegetable oil
* 8 garlic cloves, minced or pressed
* 1 large carrot, peeled and diced small or cut in julienne
* 4 ounces tofu, patted dry and cut in 1/2-inch dice
* 4 eggs, beaten and seasoned with salt and pepper
* 5 cups cooked rice, preferably Thai jasmine rice available in markets that sell Asian foods
* 2 to 3 tablespoons Thai or Vietnamese fish sauce (to taste)
* 2 to 3 teaspoons Thai or Indonesian chile sauce (to taste)
* 1 tomato, chopped
* 1 bunch scallions, both white and green parts, chopped

FOR THE GARNISH
* ½ cup chopped cilantro
* Thinly sliced cucumber
* Lime wedges
* Scallions
* Fish sauce with hot chiles nam pla prik or half the amount of soy sauce
 
## Steps
1. Heat a large wok or large, heavy nonstick skillet over medium-high heat until a drop of water evaporates upon contact.
2. Add the oil and swirl, then add the carrot and tofu. Stir-fry until lightly colored, about two minutes. Add the garlic and stir-fry until golden, about 30 seconds.
3. Pour in the beaten egg. Stir-fry until scrambled, then add the rice. Cook the rice — scooping it up and pressing it into the pan, then scooping it up again — for about two minutes.
4. Add the fish, chile sauces, tomato and chopped scallions, then stir together for about a half-minute. 
5. Serve, garnishing each plate with the cilantro and cucumbers and passing lime wedges, scallions and fish sauce with chiles. Diners should squeeze lime juice onto their rice as they eat.
```
2. Save the file as `thai_fried_rice.md` in the `dinner` folder. 
3. Add and commit the new recipe using `git add -A` followed by `git commit -am "<your commit message>"`. Make sure you replace `<your commit message>` with a descriptive commit message!
4. Push to the remote repo using `git push`.

### Conflict cause & resolution
*So what happened?*

Cook #2 didn't have the `buttery_french_cookie.md` file Cook #1 added and pushed to the remote repo. So when Cook #2 tried to push the commit containing `thai_fried_rice.md`, Git threw a conflict.

*But these are separate files, why would there be a conflict?*

With Git, it's not about separate files, it's about a repository's history. Cook #2's history didn't match the remote branch's history because Cook #1 changed it. When Cook #2 tried to push to the remote, Git saw that Cook #1's commit was missing.

#### Resolution
Cook #2 can resolve the conflict and push to the remote by doing the following.

1. Enter `git status` to compare how the state if the remote and local branch.
2. Enter `git pull` to get updates from the remote branch.

 This should've added the commits made by Cook #1 to your local copy of the `new_recipes` branch.
3. Enter `git push` to send your commit to the remote.

### Summary
When working in the same development environment, each cook needs to keep track of what others are pushing to the remote. Errors occur when one cook changes the remote's history and another cook tries pushing before getting that change.

Check the branch's remote and local status with `git status` then enter `git pull` before pushing.

## 1.2 Editing existing, but different files
This is basically the same as adding new files, but let's do it.

### Cook #1
1. In the `snacks` folder, open `greek_goddess_dip.md`, add the following to the first line, and press enter.

 ```
![recipe image](https://static01.nyt.com/images/2014/04/08/dining/goddessdip/Greek-Goddess-Dip-articleLarge-v2.jpg)
```
2. Save the file.
3. Add and commit the change using `git commit -am "<your commit message>"`. Make sure you replace `<your commit message>` with a descriptive commit message!
4. Push to the remote repo using `git push`.

### Cook #2
1. In the `dinner` folder, open `thai_fried_rice.md`, add the following to the first line, and press enter.

 ```
![recipe image](https://static01.nyt.com/images/2016/05/23/dining/thai-combination-fried-rice/thai-combination-fried-rice-articleLarge.jpg)
```
2. Save the file.
3. Add and commit the change using `git commit -am "<your commit message>"`. Make sure you replace `<your commit message>` with a descriptive commit message!
4. Push to the remote repo using `git push`.

### Conflict cause & resolution
*So what happened?*

Cook #2 didn't have the change Cook #1 made to `greek_goddess_dip.md`. So when Cook #2 tried to push the commit containing the change to `thai_fried_rice.md`, Git threw a conflict.

*But these are separate files, why would there be a conflict?*

With Git, it's not about separate files, it's about a repository's history. Cook #2's history didn't match the remote branch's history because Cook #1 changed it. When Cook #2 tried to push to the remote, Git saw that Cook #1's commit was missing.

#### Resolution
Cook #2 can resolve the conflict and push to the remote by doing the following.

1. Enter `git status` to compare how the state if the remote and local branch.
2. Enter `git pull` to get updates from the remote branch.

 This should've added the commits made by Cook #1 to your local copy of the `new_recipes` branch.
3. Enter `git push` to send your commit to the remote.

### Summary
When working in the same development environment, each cook needs to keep track of what others are pushing to the remote. Errors occur when one cook changes the remote's history and another cook tries pushing before getting that change.

Check the branch's remote and local status with `git status` then enter `git pull` before pushing.

## 1.3 Editing the same file
Now you're just asking for conflicts. But sometimes you gotta do it, so let's figure this out.

### Cook #1
1. In the `dinner` folder, open `obamas_short_ribs.md`, add the following to the first line, and press enter.

 ```
![recipe image](https://static01.nyt.com/images/2016/09/28/dining/28ROOSTER1/28ROOSTER1-articleLarge.jpg)
```
2. Save the file.
3. Add and commit the change using `git commit -am "<your commit message>"`. Make sure you replace `<your commit message>` with a descriptive commit message!
4. Push to the remote repo using `git push`.

### Cook #2
1. In the `dinner` folder, open `obamas_short_ribs.md`, and replace `1 onion, chopped` with `½ cup chopped onion`. 
2. Save the file.
3. Add and commit the change using `git commit -am "<your commit message>"`. Make sure you replace `<your commit message>` with a descriptive commit message!
4. Push to the remote repo using `git push`.


### Conflict cause & resolution
*So what happened?*

Both cooks edited the same file, So when Cook #2 tried to push the commit containing the change to `obamas_short_ribs.md`, Git threw a conflict.

*Does that mean we can't work in the same file?*

Nope! It just means that you'll have to manually resolve the conflicts on your own. Git isn't *that* magical.

#### Resolution
Cook #2 will need to manually merge the changes in this file. Complete the following steps to do it.

1. Enter `git pull` to get updates from the remote branch.
2. In a text editor, open `obamas_short_ribs.md`.
3. Manually merge the changes (specific instructions coming soon!)
4. Add and commit the change using `git commit -am "<your commit message>"`. 
5. Enter `git push` to send your commit to the remote.

### Summary
Again, `git status` and `git pull` would have helped you out, but you still couldn't have avoided this conflict. You'll have to manually merge the changes in this file.

## TL;DR
`git status` to compare the remote and local branch, `git pull` to update before pushing.
