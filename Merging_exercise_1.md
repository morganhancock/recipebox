# Exercise 1: Sharing a branch
> **Cooks:** 2+ **Goal:** Multiple cooks add new recipes and edit existing recipes without conflict.

When multiple cooks are in one kitchen, they coordinate to avoid ruining meals and duplicating work. 

The same applies to Git. When multiple people are working in the same development branch, they need to make sure they can share their work correctly. 

Work through the following tasks to discover how to successfully share a branch.

## Adding new files
Sharing a branch is fairly easy when you're just adding new files. First, have one teammate create a new branch called `new_recipes`. Then each cook should do one of the following in the `new_recipes` branch.

### Cook #1
Do the following to add a cookie recipe to the recipe box.

1. Open a text editor and paste the following.

 ```
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
3. Add and commit the new recipe using `git commit *`. In the notepad file that opens, type your commit message and save and close the file.
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
3. Add and commit the new recipe using `git commit *`. In the notepad file that opens, type your commit message and save and close the file.
4. Push to the remote repo using `git push`.

### Results
Honestly I'm not sure yet! Ha! State what happened and explain why it worked or didn't work...

## Editing existing, but different files
This is basically the same as adding new files since you aren't working on top of anyone else yet.

### Cook #1
1. In the `snacks` folder, open `greek_goddess_dip.md`, add the following to the first line, and press enter.

 ```
![recipe image](https://static01.nyt.com/images/2014/04/08/dining/goddessdip/Greek-Goddess-Dip-articleLarge-v2.jpg)
```
2. Save the file.
3. Add and commit the change using `git commit *`. In the notepad file that opens, type your commit message and save and close the file.
4. Push to the remote repo using `git push`.

### Cook #2
1. In the `dinner` folder, open `thai_fried_rice.md`, add the following to the first line, and press enter.

 ```
![recipe image](https://static01.nyt.com/images/2016/05/23/dining/thai-combination-fried-rice/thai-combination-fried-rice-articleLarge.jpg)
```
2. Save the file.
3. Add and commit the change using `git commit *`. In the notepad file that opens, type your commit message and save and close the file.
4. Push to the remote repo using `git push`.

### Results
Honestly I'm not sure yet! Ha! State what happened and explain why it worked or didn't work...

## Editing the same file
Now you're just asking for conflicts. But sometimes you gotta do it, so let's figure this out.

### Cook #1
1. In the `dinner` folder, open `obamas_short_ribs.md`, add the following to the first line, and press enter.

 ```
![recipe image](https://static01.nyt.com/images/2016/09/28/dining/28ROOSTER1/28ROOSTER1-articleLarge.jpg)
```
2. Save the file.
3. Add and commit the change using `git commit *`. In the notepad file that opens, type your commit message and save and close the file.
4. Push to the remote repo using `git push`.

### Cook #2
1. In the `dinner` folder, open `obamas_short_ribs.md`, and replace `1 onion, chopped` with `½ cup chopped onion`. 
2. Save the file.
3. Add and commit the change using `git commit *`. In the notepad file that opens, type your commit message and save and close the file.
4. Push to the remote repo using `git push`.

### Results
Probably some trouble, I'd guess... But maybe not yet.
