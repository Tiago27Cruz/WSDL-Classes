> Find Margherita and see how it is defined as a pizza with only cheese and tomato topping. Look at the definition of VegetarianPizza. Is a Margherita pizza a vegetarian pizza? Why / why not?

A vegetarian pizza is defined as equivalent to not having neither a fish nor meat topping, therefore margherita will be a vegetarian pizza.

> Find hasIngredient. What is the domain and range of this property? What are the subproperties of hasIngredient? What is the inverse property of hasIngredient? What property characteristics does hasIngredient have? Explain it.

Domain is Food and the range is also Food. This is because a given food, let's say a pizza has food ingredients, like mozarella, meat, peperoni...

Subproperties are hasBase and hasTopping. This is because the ingredients the food can have, in this case pizza, are a base (tomato sauce, etc) and toppings.

Inverse property is isIngredientOf, this is because if X has an ingredient y, then y is an ingredient of x.

hasIngredient has the Transitive property. This means that if X is related to Y and Y is related to Z, then x will be related to Z. In this case, if pizza has a given ingredient, that itself to be composed needs another ingredient, then said ingredient will be also an ingredient of pizza. For example sausages have meat, therefore a sausage pizza has meat as an ingredient.

> In general, what is the difference between the asserted class hierarchy and the inferred class hierarchy?

The asserted classes are the ones we defined, the inferred are the ones the reasoner logically inferred from our definitions.

> What does it mean for a class to be a subclass of owl:Nothing? 

It means the class is unsatisfiable (empty), so they can't have instances because they are logically inconsistent, therefore, wrong.

> Explain why these two classes appear as subclasses of owl:Nothing.

Regarding IceCream: The property hasTopping has a domain of Pizza. This means that the reasoner can infer that all individuals using the hasTopping property must be of type Pizza. Because of the restriction on this class, all members of IceCream must use the hasTopping property, and therefore must also be members of Pizza. However, Pizza and IceCream are disjoint, so this causes an inconsistency. If they were not disjoint, IceCream would be inferred to be a subclass of Pizza.

Regarding CheeseAndVegetableToppings: This class will be unsatisfiable. This is because we have given it 2 disjoint parents, which means it could never have any instances (as nothing can be both a CheeseTopping and a VegetableTopping). NB Called ProbeInconsistentTopping in the ProtegeOWL Tutorial.

> Find Margherita in the inferred class hierarchy and see which classes are inferred as  superclasses of Margherita

CheesePizza, VegetarianPizzaEquivalent1 and VegetarianPizzaEquivalent2