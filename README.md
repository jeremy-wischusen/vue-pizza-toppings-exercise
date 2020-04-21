# vue-pizza-toppings-exercise
Most popular pizza toppings coding exercise using Vue and Veutify
## Task
Pizza Exercise (Front-end)

One of our restaurant clients wants to know which pizza topping combinations are the most popular.
Using Ember, React, Angular, or Vue, write a throw-away app that will download orders directly from pizzas.json and output the top 20 most frequently ordered pizza topping combinations. List the toppings for each popular pizza topping combination along with its rank and the number of times that combination has been ordered.

## Notes
I would have simply done this using a Vuetify table, but apparently they removed the index property from the item object passed to each row. So in order to display the rank number, I used a simple v-for with an index variable. 
