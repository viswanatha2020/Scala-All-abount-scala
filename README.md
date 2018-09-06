# Scala-All-abount-scala
Scala Basic Tutorial - How To Declare Variables And Types
By Nadim Bahadoor | Last updated: March 16, 2018 at 15:14 pm
Overview
In this tutorial, we will go over declaring variables and learn about the data  types that are supported in Scala.
Steps
1. Immutable variables
As we described in the Scala Introduction tutorial, immutability is a first class citizen in the Scala programming language. To define immutable variable, we use the keyword val with the following syntax:
val <Name of our variable>: <Scala type> = <Some literal>
As an example, you can define an immutable variable named donutsToBuy of type Int and assign its value to 5.

val donutsToBuy: Int = 5
Now, if you try to change the value of donutsToBuy to say 10, the Scala compiler will not be happy :(

donutsToBuy = 10

If you then hover your mouse on the red lines in IntelliJ, you will see the message "Reassignment to val". The message tells us that once a value has been assigned, we can no longer change it!
Feel free to review the Scala Introduction where we discussed some of the benefits of having immutable variables.
2. Mutable variables
OK, fair enough that Scala is a functional programming language which favours the immutable pattern. But, what if you are in a loop and need to increment some variable. That's a perfectly legitimate use case and to declare a variable as mutable, we use the keyword var as opposed to val.

var favoriteDonut: String = "Glazed Donut"
favoriteDonut = "Vanilla Donut"

NOTE:
•	The Scala compiler no longer complains that we are reassigning the favoriteDonut value from "Glazed Donut" to "Vanilla Donut".
•	The type of favoriteDonut is defined as String using syntax : String
3. Lazy initialization
Sometimes you may wish to delay the initialization of some variable until at the point where it is consumed by your application. This is usually referred to as lazy initialization and we need to make use of the lazy keyword

lazy val donutService = "initialize some donut service"

NOTE:
•	We've not specified the type of donutService! However, in this case, the Scala compiler knew that it should be of type String. This is called type inference which we will see in the upcoming tutorials.
4. Scala Supported Types
If you have used other programming languages such as Java or .NET, you would intuitively look for the supported  types similar to Java's primitives or .NET's built-in types. However, Scala does not have built-in types! Instead, it was designed from the ground up to have a set of classes for representing its supporting types as shown below:

val donutsBought: Int = 5
val bigNumberOfDonuts: Long = 100000000L
val smallNumberOfDonuts: Short = 1
val priceOfDonut: Double = 2.50
val donutPrice: Float = 2.50f
val donutStoreName: String = "allaboutscala Donut Store"
val donutByte: Byte = 0xa
val donutFirstLetter: Char = 'D'
val nothing: Unit = ()
NOTE:
•	Scala also provides a type called Unit. For now, you can think of the Unit type similar to Java's or .NET's void keyword.
5. Declare a variable with no initialization
Sometimes you may not know the value of your variable immediately. You can only assign your variable's value at some later point in time during the execution of your application.
Let's assume that you need to declare a variable called leastFavoriteDonut of type String, but you won't initialize it just yet.

var leastFavoriteDonut: String = _
leastFavoriteDonut = "Plain Donut"
NOTE:
•	We've use the wildcard operator _ when defining our variable.
•	Somewhere later in our code base, we can then assign a String value for our variable which in our case was "Plain Donut" String value.
•	Now, this may be controversial as you should strive to use the immutable pattern. As a matter of fact, when you code review some Scala application, you should always look out for code smell such as the use of var! There are better ways to avoid the use of var which we will see in upcoming tutorials.
This concludes our tutorial on Scala Basic Tutorial - How To Declare Variables and Typesand I hope you've found it useful!
Stay in touch via Facebook and Twitter for upcoming tutorials!
Don't forget to like and share this page :)
Summary
In this article, we went over the following:
•	How to declare immutable variables in Scala
•	How to declare mutable variables in Scala
•	How to declare the various data types that Scala provides
•	How to declare a variable with no initialization.
Tip
•	If you come from an Object Oriented language, it may be a paradigm shift for using the immutable pattern via the val keyword. But, it will come with lots of benefits especially as you start getting more familiar with the functional programming side of Scala.
Scala String Interpolation - Print And Format Variables
By Nadim Bahadoor | Last updated: March 16, 2018 at 15:14 pm
Overview
In this tutorial, we will go over String interpolation in Scala which allows us to easily print and format variables and expressions.
Make sure you have reviewed the previous tutorial on how to declare immutable variables as we will be using them here. If you do not have IntelliJ IDEA installed, please follow the tutorials from Chapter 1.
Steps
1. Using String interpolation to print a variable
Let's assume that you have a variable called favoriteDonut and would like to use the String interpolation feature in Scala to print that variable.

println("Step 1: Using String interpolation to print a variable")
val favoriteDonut: String = "Glazed Donut"
println(s"My favorite donut = $favoriteDonut")

NOTE:
•	We've prefixed the s at the beginning of our println statement.
•	We also used the dollar sign $ to refer to our variable.
You will see the output below when you run your Scala application in IntelliJ:

Step 1: Using String interpolation to print a variable
My favorite donut = Glazed Donut

2. Using String interpolation on object properties
Say you have an object which represents a donut and it has name and tasteLevel properties. We can represent this donut object using a case class:

println("\nStep 2: Using String interpolation on object properties")
case class Donut(name: String, tasteLevel: String)

NOTE:
•	We've just introduced case class which is yet another feature of Scala! If you've never heard of case class before, don't worry,  we will cover it in upcoming tutorials.
•	For now you can think of case class as a means for creating domain objects where the Scala compiler does the hardwork of adding your getters and setters!
•	If you come from a Java background, think of a case class as an alternative to creating Plain Old Java Objects (POJO) but without having to write boilerplate code for getters and setters.
•	If you've used .NET, it's similar to creating domain objects but without having to define boilerplate properties for getters and setters.
To use String interpolation on the properties exposed by our object, we have to wrap our expression inside curly braces as follows:

println("\nStep 2: Using String interpolation on object properties")
case class Donut(name: String, tasteLevel: String)
val favoriteDonut2: Donut = Donut("Glazed Donut", "Very Tasty")
println(s"My favorite donut name = ${favoriteDonut2.name}, tasteLevel = ${favoriteDonut2.tasteLevel}")

You will see the output below when you run your Scala application in IntelliJ:

Step 2: Using String interpolation on object properties
My favorite donut name = Glazed Donut, tasteLevel = Very Tasty

3. Using String interpolation to evaluate expressions
Similar to step 2, you can use String interpolation with expressions by using the curly braces. In the example below, we check to see if we are buying 10 donuts:

println("\nStep 3: Using String interpolation to evaluate expressions")
val qtyDonutsToBuy: Int = 10
println(s"Are we buying 10 donuts = ${qtyDonutsToBuy == 10}")

You will see the output below when you run your Scala application in IntelliJ:

Step 3: Using String interpolation to evaluate expressions
Are we buying 10 donuts = true

4. Using String interpolation for formatting text
In some cases, you may want to format your strings by say pre-pending some white spaces in front of the text. This can be achieved using the f interpolation as follows:

println("\nStep 4: Using String interpolation for formatting text")
val donutName: String = "Vanilla Donut"
val donutTasteLevel: String = "Tasty"
println(f"$donutName%20s $donutTasteLevel")

You will see the output below when you run your Scala application in IntelliJ:

Step 4: Using String interpolation for formatting text
       Vanilla Donut Tasty

NOTE:
•	The extra white spaces that were prepended to Vanilla Donut String.
5. Using f interpolation to format numbers
As an example, let's first print the price of one donut using the s interpolation:

println("\nStep 5: Using f interpolation to format numbers")
val donutPrice: Double = 2.50
println(s"Donut price = $donutPrice")

You will see the output below when you run your Scala application in IntelliJ:

Step 5: Using f interpolation to format numbers
Donut price = 2.5

But, what if we wanted to print the 2 decimal places for the donutPrice variable. This can be achieved by using the f interpolator.

println("\nStep 5: Using f interpolation to format numbers")
val donutPrice: Double = 2.50
println(s"Donut price = $donutPrice")
println(f"Formatted donut price = $donutPrice%.2f")

You will see the output below when you run your Scala application in IntelliJ:

Formatted donut price = 2.50

6. Using Raw interpolation
The raw String interpolation will allow you to print any symbols within your String. In the example below we would like to print the donut name followed by \t, as opposed to evaluating \t to tab spaces:

println("\nStep 6: Using raw interpolation")
println(raw"Favorite donut\t$donutName")

This concludes our tutorial on Scala String Interpolation - Print And Format Variables and I hope you've found it useful!
Stay in touch via Facebook and Twitter for upcoming tutorials!
Don't forget to like and share this page :)
Scala - How To Escape Characters And Create Multi-line String
By Nadim Bahadoor | Last updated: March 16, 2018 at 15:14 pm
Overview
In this tutorial, we will show how to escape characters when writing text. In addition, we will learn how to format multi-line text so that it is more readable.
 
Make sure that you have followed the tutorials from Chapter 1 on how to install and use IntelliJ IDEA. Don't forget to also review the tutorials from Chapter 2 as we will build on what we've previously learned.
Steps
 1. How to escape a Json String
In tutorial How To Declare Variables And Types, we learned the syntax to create and assign an immutable String variable. Let's assume that you have a JSON String which represents a donut object with properties donut_name, taste_level and price.
How would you define a variable to store the donut JSON String?

println("Step 1: How to escape a Json String")
val donutJson: String ="{"donut_name":"Glazed Donut","taste_level":"Very Tasty","price":2.50}"

NOTE:
•	The Scala compiler will complain about the double quotes in the JSON field names.
2. Using backslash to escape quotes
If you have used another programming language like Java or .NET in the past, you would be familiar with escaping quotes in a String using backslash \

println("\nStep 2: Using backslash to escpae quotes")
val donutJson2: String ="{\"donut_name\":\"Glazed Donut\",\"taste_level\":\"Very Tasty\",\"price\":2.50}"
println(s"donutJson2 = $donutJson2")




You will see the output below when you run your Scala application in IntelliJ:

Step 2: Using backslash to escpae quotes
donutJson2 = {"donut_name":"Glazed Donut","taste_level":"Very Tasty","price":2.50}

NOTE:
•	As you can see from above, we were able to print a JSON String by making use of backslash \
•	This is great but if you have longer text to escape, I'm sure you will get bored quite quickly : ) by having to escape each and every individual quote within your JSON String. So, let's see how to make this easier in Step 3 below.
3. Using triple quotes """ to escape characters
Fortunately Scala has a much better solution! To help you easily escape characters and symbols inside strings, you just need to wrap the text within triple quotes """<YOUR TEXT TO ESCAPE>""" as follows:

println("\nStep 3: Using triple quotes \"\"\" to escape characters")
val donutJson3: String = """{"donut_name":"Glazed Donut","taste_level":"Very Tasty","price":2.50}"""
println(s"donutJson3 = $donutJson3")

You will see the output below when you run your Scala application in IntelliJ:

Step 3: Using triple quotes """ to escape characters
donutJson3 = {"donut_name":"Glazed Donut","taste_level":"Very Tasty","price":2.50}

4. Creating multi-line text using stripMargin
As we've just seen in Step 3, using """ should be a clear winner on escaping quotes and other symbols! But, programmers in today's world demand much more :)
What if you would like to indent your text so that it's more readable? Look no further, Scala is here to help with the use of stripMargin:

val donutJson4: String =
    """
      |{
      |"donut_name":"Glazed Donut",
      |"taste_level":"Very Tasty",
      |"price":2.50
      |}
      """
   .stripMargin

You will see the output below when you run your Scala application in IntelliJ:

Step 4:  Creating multi-line text using stripMargin
donutJson4 = 
{
"donut_name":"Glazed Donut",
"taste_level":"Very Tasty",
"price":2.50
}
This concludes our tutorial on Scala - How To Escape Characters and Create Multi-Line String and I hope you've found it useful!
 
Stay in touch via Facebook and Twitter for upcoming tutorials!
 
Don't forget to like and share this page :)
Summary
In this tutorial, we went over the following:
•	How to assign a JSON String to a val.
•	How to escape characters in a String using backslash
•	How to escape characters using triple quotes
•	How to create multi-line text using stripMargin
Tip
•	You can refer to the Scala API documentation to find more details about some function. If you look at the definition of the stripMargin function, you will see that it also takes in a parameter to allows you to specify a different character other than the default pipe |

println("\nTip: stripMargin using a different character")
val donutJson5: String =
"""
#{
#"donut_name":"Glazed Donut",
#"taste_level":"Very Tasty",
#"price":2.50
#}
""" .stripMargin('#')
println(s"donutJson5 = $donutJson4")

Source Code
An Overview Of Scala Type Inference
By Nadim Bahadoor | Last updated: March 16, 2018 at 15:14 pm
Overview
In this tutorial, we will build on what we've previously learned from Tutorial 1 regarding how to declare variables in Scala.
 
More specifically, we will redo the examples from Tutorial 1 and show how Scala is able to infer the data types for our variables.
Step
1. Scala type inference
Let's review the syntax for declaring immutable variables in Scala.

val <Name of our variable> : <Scala type> = <Some literal>

As an example, you can define an immutable variable named donutsToBuy of type Int and assign its value to 5.

println("Step 1: Immutable variable")
val donutsToBuy: Int = 5
However, through type inference, Scala complier is smart enough to figure out that the literal 5 is actually  an Integer.
As a result, you can simplify the declaration of some immutable variable of type Int as follows:

val donutsBought = 5
2. Declaring Scala Supported Types Using Inference
With type inference in mind, let's redo the data types examples from the tutorial How To Declare Variables And Types.

println("\nStep 2: Scala Types")
val donutsBoughtToday = 5
val bigNumberOfDonuts = 100000000L
val smallNumberOfDonuts = 1
val priceOfDonut = 2.50
val donutPrice = 2.50f
val donutStoreName = "Allaboutscala Donut Store"
val donutByte = 0xa
val donutFirstLetter = 'D'
val nothing = ()
NOTE:
•	We did not specify the data types for any of the above variables. 
3. Using Scala compiler to convert from one data type to another
The Scala compiler is also smart enough to convert from one data type into another. However, you should bear in mind that this conversion is fine so long as your resulting type is not lossy.
In the example below, say you have numberOfDonuts which is of the type Short. But at some later point in your code, you decide to assign it's value to  another  immutable variable called minimumDonutsToBuy of type Int.

println("\nStep 3: Using Scala compiler to convert from one data type to another")
val numberOfDonuts: Short = 1
val minimumDonutsToBuy: Int = numberOfDonuts
NOTE:
•	Converting from a Short to an Int was fine because there was no precision loss, i.e. an Int is larger than a Short.
4. User driven conversion from one data type to another
The example in Step 3 showed how the Scala compiler automatically converted a Short into an Int. But, what would happen if we had a variable minimumDonutsToSell of type String? Let's try it.

println("\nStep 4: User driven conversion from one data type to another ")
// NB: You cannot convert from an Int to a String
// val minimumDonutsToSell: String = numberOfDonuts
The compiler complains with the following error: type mismatch found Short required String. As we've outlined in the tutorial on the Scala features, Scala's type safety guardrails are here to help us!
So how then would you convert an Int to String? As expected in a fluent functional language, you have access to built in conversion functions. In our example, you can call the toStringfunction on numberOfDonuts:

val minimumDonutsToSell: String = numberOfDonuts.toString()
This concludes our tutorial on An Overview Of Scala Type Inference and I hope you've found it useful!
 
Stay in touch via Facebook and Twitter for upcoming tutorials!
 
Don't forget to like and share this page :)
Summary
In this article, we went over the following:
•	How Scala is able to infer the type of our variables
•	How Scala is able to convert from one data type into another
•	How to manually tell Scala to convert one data type into another
Tip
•	Type inference can be incredibly useful such as to avoid redundant code when initializing collections for some given type.
•	But use it wisely. It is a good practice to be clear about the intent of your data type especially when it comes to the return type of a function.
How To Use If Else Statement And Expression
By Nadim Bahadoor | Last updated: March 16, 2018 at 15:14 pm
Overview
In this tutorial, we will go over the if and else expressions. If you are coming from other languages such as Java or .NET, this should be familiar, but with one caveat!
 
In Scala, you can use the if and else clause as a statement to test for some condition or logical step. In addition, you can also use if and else clause as an expression where you get back the result of your condition or logical step.
Steps
1. Using if clause as a statement
Let's declare two immutable integer variables namely numberOfPeople and donutsPerPerson. For simplicity, we are using Scala's type inference when declaring the variables which we have seen in the previous Type Inference tutorial. We then check if the numberOfPeople is greater than 10 and will print the number of donuts to be bought.

println("Step 1: Using if clause as a statement")
val numberOfPeople = 20
val donutsPerPerson = 2

if(numberOfPeople > 10)
  println(s"Number of donuts to buy = ${numberOfPeople * donutsPerPerson}")
NOTE:
•	We are leveraging what we've learned from the Scala String Interpolation tutorial to help us build the String inside the println() function.
2. Using if and else clause as a statement
Now that we know how to write an if statement, let's extend the example from Step 1 and add an else clause to print a default number of donuts you need to buy if there is less that 10persons.

println(s"\nStep 2: Using if and else clause as a statement")
val defaultDonutsToBuy = 8

if(numberOfPeople > 10)
  println(s"Number of donuts to buy = ${numberOfPeople * donutsPerPerson}")
else
  println(s"Number of donuts to buy = $defaultDonutsToBuy")
3. Using if, else if, and else clause as a statement
Let's extend once more our if statement to include and else if clause as follows:

println("\nStep 3: Using if, else if, and else clause as a statement")
if(numberOfPeople > 10) {
  println(s"Number of donuts to buy = ${numberOfPeople * donutsPerPerson}")
} else if (numberOfPeople == 0) {
  println("Number of people is zero.")
  println("No need to buy donuts.")
} else {
  println(s"Number of donuts to buy = $defaultDonutsToBuy")
}
NOTE:
•	It's a good practice to enclose your if, else, else if statements with curly braces {} as they get more complex.
4. Using if and else clause as expression
What if you had to store the result of the if and else expressions above into a variable. With Scala, you can easily inline this as follows:

println("\nStep 4: Using if and else clause as expression")
val numberOfDonutsToBuy = if(numberOfPeople > 10) (numberOfPeople * donutsPerPerson) else defaultDonutsToBuy
println(s"Number of donuts to buy = $numberOfDonutsToBuy")
NOTE:
•	In another language such as Java or .NET, you would have used the Ternary Operatorto achieve Step 4.
•	Perhaps Scala's functional style is much easier to read and less error prone compared to the ternary operator.
This concludes our tutorial on How To Use If Else Statement And Expression and I hope you've found it useful!
 
Stay in touch via Facebook and Twitter for upcoming tutorials!
 
Don't forget to like and share this page :)
Summary
In this tutorial, we went over the following:
•	How to use a simple if statement
•	How to use an if and else statement
•	How to use an if, else if and else statement
•	How to use if and else clause as expressions which can be assigned to a variable
Tip
•	In upcoming tutorials, we will go over pattern matching which is more popular in functional programming rather than using if and else expressions.
•	By now you should have noticed that in Scala there is no need to terminate each statement with a semi-colon ;. If you are coming from Java or .NET it may take some time to get used to it. But this is yet another example of how Scala allows us to not over-clutter our code base and make it more readable!
Learn How To Use For Comprehension
By Nadim Bahadoor | Last updated: March 16, 2018 at 15:14 pm
Overview
In this tutorial, we will go over the for comprehension construct in Scala. If you are coming from another mainstream language such as Java or .NET, a for loop should be fairly self explanatory in that you are writing a piece of code to iterate over some data points.
 
But, the Scala for comprehension can do much more! As an example and similar to the previous tutorial on using IF And Else Expressions, the for construct in Scala can return a value!
Steps
1. A simple for loop from 1 to 5 inclusive
Let's show how to do a simple for loop by iterating from 1 to 5 and print the immutable variable numberOfDonuts during each iteration.

println("Step 1: A simple for loop from 1 to 5 inclusive")
for(numberOfDonuts <- 1 to 5){
  println(s"Number of donuts to buy = $numberOfDonuts")
}
You should see the following output when you run your Scala application in IntelliJ:

Number of donuts to buy = 1
Number of donuts to buy = 2
Number of donuts to buy = 3
Number of donuts to buy = 4
Number of donuts to buy = 5
NOTE:
•	We used the keyword to which meant that iteration number 5 was included.
2. A simple for loop from 1 to 5, where 5 is NOT inclusive
What if we wanted to iterate through numbers 1 to 4? In other words, the last iteration for number 5 will not be included. If you have used Java or .NET for loop to iterate through arrays or other collections, I'm pretty sure that at some point you must have encountered bugs in your code because you had used a <= instead of < or vice versa in your loop.
Scala's language fluency with the use of keyword until makes it clear that your for loop will NOT include the last iteration.

println("\nStep 2: A simple for loop from 1 to 5, where 5 is NOT inclusive")
for(numberOfDonuts <- 1 until 5){
  println(s"Number of donuts to buy = $numberOfDonuts")
}
You should see the following output when you run your Scala application in IntelliJ:

Number of donuts to buy = 1
Number of donuts to buy = 2
Number of donuts to buy = 3
Number of donuts to buy = 4
NOTE:
•	We used of keyword until which meant that the iteration number 5 was NOT included.
3. Filter values using if conditions in for loop
Now that you are familiar with the for loop syntax from Step 1 and 2, let us show that in Scala you can also use if clause to add filtering support as you iterate through your items.
As an example, let's store a List of ingredients for baking donuts into an immutable variable called donutIngredients. We then loop through each ingredient in the list and filter out all items except for the "sugar" item.

println("\nStep 3: Filter values using if conditions in for loop")
val donutIngredients = List("flour", "sugar", "egg yolks", "syrup", "flavouring")
for(ingredient <- donutIngredients if ingredient == "sugar"){
  println(s"Found sweetening ingredient = $ingredient")
}
You should see the following output when you run your Scala application in IntelliJ:

Found sweetening ingredient = sugar
NOTE:
•	This is the first time we are showing how to declare and use a List. If you are coming from Java or .NET, you may be surprised not to find the new keyword used when declaring the List object. This is made possible in Scala using companion objectswhich we will see in upcoming tutorials.
•	We used the if expression within the for loop itself!
•	There are however better ways at filtering out items from collections which we will see in upcoming tutorials.
4. Filter values using if conditions in for loop and return the result back using the yield keyword
Let's expand the example in Step 3 and filter for either "sugar" or "syrup" ingredients in our donutsIngredients list. Instead of using the (), we are using the {} in our for comprehension to make our expressions more explicit.
In addition, to return the result of the for comprehension and store it in the sweeteningIngredients variable, we will make use of the yield keyword.

println("\nStep 4: Filter values using if conditions in for loop and return the result back using the yield keyword")
val sweeteningIngredients = for {
  ingredient <- donutIngredients
  if (ingredient == "sugar" || ingredient == "syrup")
} yield ingredient
println(s"Sweetening ingredients = $sweeteningIngredients")
You should see the following output when you run your Scala application in IntelliJ:

Sweetening ingredients = List(sugar, syrup)
5. Using for comprehension to loop through 2-Dimensional array
It is very common in other programming languages to work with 2-Dimensional arrays. Let's create a 2-Dimensional array consisting of 4 elements of our donuts Ingredients.
To do this, we will use Scala Array class and call the ofDim() function, pass in the type of String in square brackets [String] and then specify our 2 by 2 array in the function parameter. We then fill in each element of our 2-Dimensional array as follows:

val twoDimensionalArray = Array.ofDim[String](2,2)
twoDimensionalArray(0)(0) = "flour"
twoDimensionalArray(0)(1) = "sugar"
twoDimensionalArray(1)(0) = "egg"
twoDimensionalArray(1)(1) = "syrup"
To iterate through your 2-Dimensional array, you can use the for comprehension and first declare an x variable to loop from 0 until 2, followed by a second iteration again from 0 until 2 which you will store in variable y. After the closing } of our for loop, you can call println() to print each element of our 2-Dimensional array.

for { x <- 0 until 2
       y <- 0 until 2
} println(s"Donut ingredient at index ${(x,y)} = ${twoDimensionalArray(x)(y)}")
You should see the following output when you run your Scala application in IntelliJ:

Step 5: Using for comprehension to loop through 2-Dimensional array
Donut ingredient at index (0,0) = flour
Donut ingredient at index (0,1) = sugar
Donut ingredient at index (1,0) = egg
Donut ingredient at index (1,1) = syrup
NOTE:
•	We are making use of String interpolation in our println() function.
•	Learn more from our previous tutorial on Scala's String interpolation feature
Learn How To Use Range
By Nadim Bahadoor | Last updated: March 16, 2018 at 15:14 pm
Overview
In this tutorial, we will show how to use the Scala Range to help you easily write many items such as numbers or characters in sequence that can be used in looping constructs.
 Steps
1. Create a simple numeric range from 1 to 5 inclusive
This simple example should be familiar to you since we have used it in the previous For Comprehension tutorial. To create a range of integers starting with 1, incrementally adding 1 up to and including the number 5, you can do the following:

println("Step 1: Create a simple numeric range from 1 to 5 inclusive")
val from1To5 = 1 to 5
println(s"Range from 1 to 5 inclusive = $from1To5")
You should see the following output when you run your Scala application in IntelliJ:

Step 1: Create a simple numeric range from 1 to 5 inclusive
Range from 1 to 5 inclusive = Range(1, 2, 3, 4, 5)
NOTE:
•	We are using the to keyword which means that the number 5 was included.
2. Create a numeric range from 1 to 5 but excluding the last integer number 5
Let's extend the example from Step 1 and create a range of integers starting with 1 and incrementally adding 1 up to the last upper bound of number of 5:

println("\nStep 2: Create a numeric range from 1 to 5 but excluding the last integer number 5")
val from1Until5 = 1 until 5
println(s"Range from 1 until 5 where 5 is excluded = $from1Until5")
You should see the following output when you run your Scala application in IntelliJ:

Step 2: Create a numeric range from 1 to 5 but excluding the last integer number 5
Range from 1 until 5 where 5 is excluded = Range(1, 2, 3, 4)
NOTE:
•	We are using the until keyword to exclude the last upper bound which is number 5.
3. Create a numeric range from 0 to 10 but increment with multiples of 2
In the examples from Step 1 and 2, we incremented the next number in the range by the default value of 1. But, what if you wanted to increment the range by some arbitrary number other that 1.

println("\nStep 3: Create a numeric range from 0 to 10 but increment with multiples of 2")
val from0To10By2 = 0 to 10 by 2
println(s"Range from 0 to 10 with multiples of 2 = $from0To10By2")
You should see the following output when you run your Scala application in IntelliJ:

Step 3: Create a numeric range from 0 to 10 but increment with multiples of 2
Range from 0 to 10 with multiples of 2 = Range(0, 2, 4, 6, 8, 10)
NOTE:
•	We are using the by keyword to increment by the number 2 as opposed to the default value of 1.
4. Create an alphabetical range to represent letter a to z
So far we have shown how to create numerical ranges. What if you wanted to print the English alphabet starting from the letter a to the letter z.

println("\nStep 4: Create an alphabetical range to represent letter a to z")
val alphabetRangeFromAToZ = 'a' to 'z'
println(s"Range of alphabets from a to z = $alphabetRangeFromAToZ")
You should see the following output when you run your Scala application in IntelliJ:

Step 4: Create an alphabetical range to represent letter a to z
Range of alphabets from a to z = NumericRange(a, b, c, d, e, f, g, h, i, j, k, l, m, n, o, p, q, r, s, t, u, v, w, x, y, z)
NOTE:
•	We are using single quotes and not double quotes such that we end up with a character range.
5. Character ranges with user specified increment
What if you had to print every alternate character in the English alphabet. Similar to Step 3, this can be achieved using the by keyword.

println(s"\nStep 5: Character ranges with user specified increment")
val alphabetRangeFromAToZBy2 = 'a' to 'z' by 2
println(s"Range of every other alphabet = $alphabetRangeFromAToZBy2")
You should see the following output when you run your Scala application in IntelliJ:

Step 5: Character ranges with user specified increment
Range of every other alphabet = NumericRange(a, c, e, g, i, k, m, o, q, s, u, w, y)
6. Convert the Scala Range into collections
If you recall from the previous For Comprehension tutorial, we made use of range inside the for loop construct. What if you wanted to store a range in some data structure such as List, Set, Sequence or an Array.

  println("\nStep 6: Storing our ranges into collections")
  val listFrom1To5 = (1 to 5).toList
  println(s"Range to list = ${listFrom1To5.mkString(" ")}")

  val setFrom1To5 = (1 to 5).toSet
  println(s"Range to set = ${setFrom1To5.mkString(" ")}")

  val sequenceFrom1To5 = (1 to 5).toSeq
  println(s"Range to sequence = ${sequenceFrom1To5.mkString(" ")}")

  val arrayFrom1To5 = (1 to 5).toArray
  println(s"Range to array = `${arrayFrom1To5.mkString(" ")}")
You should see the following output when you run your Scala application in IntelliJ:

Step 6: Storing our ranges into collections
Range to list = 1 2 3 4 5
Range to set = 5 1 2 3 4
Range to sequence = 1 2 3 4 5
Range to array = `1 2 3 4 5
NOTE:
•	We are calling the .toList, .toSet and .toSeq functions to convert our ranges into List, Set and Sequence accordingly.
•	Note also we skipped the () when calling the conversion functions and instead used .toList as opposed to .toList() This may be confusing at first if you are coming from say Java or .NET! But I hope it will become more clear when we get to tutorials on functions. The general practice is to skip the () if the function has no side effects.
•	We are also calling the .mkString() function to create a string representation of each collection type. The .mkString() function takes in a delimiter which in our case is just an empty space.
This concludes our tutorial on Learn How To Use Range and I hope you've found it useful!
 
Stay in touch via Facebook and Twitter for upcoming tutorials!
 
Don't forget to like and share this page :)
Summary
In this tutorial, we went over the following:
•	How to create an inclusive range of integers
•	How to create a range of integers which excludes the upper bound
•	How to create an integer range with a different increment by parameter
•	How to create an alphabet character range from a to z
•	How to create an alphabet character range from a to z with a different increment by parameter
•	How to convert our ranges into collection data structures such as List, Set and Sequence.
Tip
•	In Step 6, we showed how to convert our ranges into collections such as List, Set, Sequence and Array. We then used the mkString() function to create a string representation for the elements in the collection. However, to access and print each element in the collection, you could just as easily used the foreach() function.

arrayFrom1To5.foreach(print(_))
The key thing to remember here is that we used the wildcard _ as part of the print() function parameter.
Learn How To Use While And Do While Loop
By Nadim Bahadoor | Last updated: March 16, 2018 at 15:14 pm
Overview
In this tutorial, we will show how to iterate over some data points using the while loopconstruct. This is a continuation of our discussion from the previous tutorials on For Comprehension and Ranges.
 
If you are coming from a Java or .NET background, the while construct should be familiar. Just a reminder that from a pure functional perspective the use of loop such as the while loop is generally less favoured.
 
Instead, fold and recursive operations are preferred and if you do not know what these mean, that's OK! We will cover them in upcoming tutorials.
Steps
1. How to use while loop in Scala
Let's declare a mutable variable called numberOfDonutsToBake to represent the quantity of donuts that we need to bake :) We can then use a while loop and keep on decrementing the numberOfDonutsToBake variable by 1 after each iteration.

println("Step 1: How to use while loop in Scala")
var numberOfDonutsToBake = 10
while (numberOfDonutsToBake > 0) {
  println(s"Remaining donuts to be baked = $numberOfDonutsToBake")
  numberOfDonutsToBake -= 1
}
You should see the following output when you run your Scala application in IntelliJ:

Remaining donuts to be baked = 10
Remaining donuts to be baked = 9
Remaining donuts to be baked = 8
Remaining donuts to be baked = 7
Remaining donuts to be baked = 6
Remaining donuts to be baked = 5
Remaining donuts to be baked = 4
Remaining donuts to be baked = 3
Remaining donuts to be baked = 2
Remaining donuts to be baked = 1
NOTE:
•	The while loop will stop when the condition numberOfDonutsToBake > 0 becomes false.
•	Yes - we've used a mutable variable! And we know that mutation is a bad thing in functional programming!
•	Once again, there are better functional ways of achieving the same looping semantics using fold or recursive techniques.
2. How to use do while loop in Scala
If you have used another mainstream language like Java or .NET, I'm pretty sure that you would be familiar with do while.
The difference between a while construct from Step 1 versus a do while is that any expressions within the do {} will be ran at least once regardless of the condition within the while() clause.

println("\nStep 2: How to use do while loop in Scala")
var numberOfDonutsBaked = 0
do {
  numberOfDonutsBaked += 1
  println(s"Number of donuts baked = $numberOfDonutsBaked")
} while (numberOfDonutsBaked < 5)
 
You should see the following output when you run your Scala application in IntelliJ:

Step 2: How to use do while loop in Scala
Number of donuts baked = 1
Number of donuts baked = 2
Number of donuts baked = 3
Number of donuts baked = 4
Number of donuts baked = 5
This concludes our tutorial on Learn How To Use While And Do While Loop and I hope you've found it useful!
 
Stay in touch via Facebook and Twitter for upcoming tutorials!
 
Don't forget to like and share this page :)
Summary
In this tutorial, we went over the following:
•	How to use while loop in Scala
•	How to use the do while loop in Scala
Tip
•	If you are new to functional programming, you can read more on the better alternatives to using loop such as fold and tail recursion.
•	If fold and tail recursion do not make any sense at the moment - it's perfectly fine! We will go over them in upcoming tutorials.
Learn How To Use Pattern Matching
By Nadim Bahadoor | Last updated: March 16, 2018 at 15:14 pm
Overview
In this tutorial, we will show a functional feature of Scala which is pattern matching.
 
If you have used Java or .NET in the past, pattern matching may at first sight appear similar to switch statements. But, Scala's pattern matching is a lot more powerful!
Steps
1. Pattern matching 101 - a very basic example
Suppose you want to test a variable called donutType. In the case that its value is Glazed Donut, you will print Very Tasty. On the other hand, if its value is Plain Donut, then you will print Tasty.

println("Step 1: Pattern matching 101 - a very basic example")
val donutType = "Glazed Donut"
donutType match {
  case "Glazed Donut" => println("Very tasty")
  case "Plain Donut" => println("Tasty")
}
You should see the following output when you run your Scala application in IntelliJ:

Step 1: Pattern matching 101 - a very basic example
Very tasty
NOTE:
•	You should have noticed that unlike in Java or in .NET, there are no break statements!
•	I'm pretty sure that you must have seen your share of bugs which come from the fact that someone forgot to use the break clause. In Java or .NET, this would allow the logic to fall-through to the next case statement.
•	Another big thanks to Scala as the compiler is smart enough to prevent fall-throughand hence there is no need to use a break clause with pattern matching.
2. Pattern matching and return the result
What if instead of simply printing the different taste level of a donut, you would like to store it in a variable. Similar to what you've learned in If And Else Expression and For Comprehension, Scala's pattern matching can return the result back to the caller.

println("\nStep 2: Pattern matching and return the result")
val tasteLevel = donutType match {
  case "Glazed Donut" => "Very tasty"
  case "Plain Donut" => "Tasty"
}
println(s"Taste level of $donutType = $tasteLevel")
You should see the following output when you run your Scala application in IntelliJ:

Step 2: Pattern matching and return the result
Taste level of Glazed Donut = Very tasty
NOTE:
•	Notice that you did not have to use the return keyword as you would in say Java or .NET.
•	Instead, the last expression will be the one returned back to the caller. We will see more return types as we get to tutorials on functions.
3. Pattern matching using the wildcard operator
As you have learned in Step 1, there is no need to use any break clauses as there is no fall-through when using pattern matching. But, what if you needed to provide a default case?

println("\nStep 3: Pattern matching using the wildcard operator")
val tasteLevel2 = donutType match {
  case "Glazed Donut" => "Very tasty"
  case "Plain Donut" => "Tasty"
  case _ => "Tasty"
}
println(s"Taste level of $donutType = $tasteLevel2")
You should see the following output when you run your Scala application in IntelliJ:

Step 3: Pattern matching using the wildcard operator
Taste level of Glazed Donut = Very tasty
NOTE:
•	If you come from a pure Object Oriented programming background, using the wildcard operator will almost certainly feel unnatural.
•	Don't worry, we will see more examples of the wildcard operator in upcoming tutorials!
4. Pattern matching with two or more items on the same condition
In our example, we are labelling Glazed Donut item as Very Tasty. What if a Strawberry Donut was also Very Tasty. This behavior seems similar to an OR expression and you can use the pipe |

println("\nStep 4: Pattern matching with two or more items on the same condition")
val tasteLevel3 = donutType match {
  case "Glazed Donut" | "Strawberry Donut" => "Very tasty"
  case "Plain Donut" => "Tasty"
  case _ => "Tasty"
}
println(s"Taste level of $donutType = $tasteLevel3")
You should see the following output when you run your Scala application in IntelliJ:

Step 4: Pattern matching with two or more items on the same condition
Taste level of Glazed Donut = Very tasty
5. Pattern matching and using if expressions in the case clause
Similar to Step 4, you can simulate an OR clause by adding If Expression in the case statements.

println("\nStep 5; Pattern matching and using if expressions in the case clause")
val tasteLevel4 = donutType match {
  case donut if (donut.contains("Glazed") || donut.contains("Strawberry")) => "Very tasty"
  case "Plain Donut"  => "Tasty"
  case _  => "Tasty"
}
println(s"Taste level of $donutType = $tasteLevel4")
You should see the following output when you run your Scala application in IntelliJ:

Step 5; Pattern matching and using if expressions in the case clause
Taste level of Glazed Donut = Very tasty
6. Pattern matching by types
So far we have been pattern matching on the value of some variable. What if you would like to pattern match on the type of the variable?
Let's declare a variable explicitly to be of type Any to hold the price of one donut. As you have learned in the Type Inference tutorial, the Scala compiler would infer that priceOfDonut to be of type Double.
Let's use pattern matching to prove it!

println("\nStep 6: Pattern matching by types")
val priceOfDonut: Any = 2.50
val priceType = priceOfDonut match {
  case price: Int => "Int"
  case price: Double => "Double"
  case price: Float => "Float"
  case price: String => "String"
  case price: Boolean => "Boolean"
  case price: Char => "Char"
  case price: Long => "Long"
}
println(s"Donut price type = $priceType")
You should see the following output when you run your Scala application in IntelliJ:

Step 6: Pattern matching by types
Donut price type = Double
NOTE:
•	If you come from Java or .NET, you can think of the Any type similar to the Objectclass.
•	In other words, Any is at the root of Scala's type hierarchy as shown per the Scala Documentation.
This concludes our tutorial on Learn How To Use Pattern Matching and I hope you've found it useful!
Learn How To Use Tuples (Pattern Match)
By Nadim Bahadoor | Last updated: March 16, 2018 at 15:14 pm
Overview
In this tutorial, we will show how to use the convenient Tuple classes to easily store elements as pairs. If you paid attention in your database class at school :) I'm pretty sure that you would have come across the word Tuple.
 
In Scala, you can think of tuples in terms of providing easy semantics for grouping your data points.
Steps
1. Using Tuple2 to store 2 data points
Let's continue using our donut examples from the previous tutorials. What if you would like to store the taste level of donuts along with the donut type? The Tuple2 class is your friend here :)

println("Step 1: Using Tuple2 to store 2 data points")
val glazedDonutTuple = Tuple2("Glazed Donut", "Very Tasty")
println(s"Glazed Donut with 2 data points = $glazedDonutTuple")
You should see the following output when you run your Scala application in IntelliJ:

Step 1: Using Tuple2 to store 2 data points
Glazed Donut with 2 data points = (Glazed Donut,Very Tasty)
2. Access each element in tuple
In Step 1, we've only printed the tuple glazedDonutTuple. What if you now would like to access each individual element.

println("\nStep 2: Access each element in tuple")
val donutType = glazedDonutTuple._1
val donutTasteLevel = glazedDonutTuple._2
println(s"$donutType taste level is $donutTasteLevel")
You should see the following output when you run your Scala application in IntelliJ:

Step 2: Access each element in tuple
Glazed Donut taste level is Very Tasty
3. Using TupleN classes to store more than 2 data points
Let's extend our examples from Step 1 and 2. What if you also wanted to store the price of the glazed donut?. You now have 3 data points namely the donut type, its taste level and then its price. Not to worry, Scala provides Tuple3 class to achieve just this!

println("\nStep 3: Using TupleN classes to store more than 2 data points")
val glazedDonut = Tuple3("Glazed Donut", "Very Tasty", 2.50)
println(s"${glazedDonut._1} taste level is ${glazedDonut._2} and it's price is ${glazedDonut._3}")
You should see the following output when you run your Scala application in IntelliJ:

Step 3: Using TupleN classes to store more than 2 data points
Glazed Donut taste level is Very Tasty and it's price is 2.5
4. How to use pattern matching on Tuples
In the previous tutorial, we've shown how to use pattern matching in Scala. Let's create two additional donut tuples one for storing the data points of Plain Donut and another one for Strawberry Donut.

println("\nStep 4: How to use pattern matching on Tuples")
val strawberryDonut = Tuple3("Strawberry Donut", "Very Tasty", 2.50)
val plainDonut = Tuple3("Plain Donut", "Tasty", 2)
Now, let's store all our donuts tuples into a list as follows:

val donutList = List(glazedDonut, strawberryDonut, plainDonut)
Let's also assume that the donutList is returned to us by a call to some API which looked up the donut details from a database.
What if you would like to find the price of a Plain Donut in that list? To do this, we will loop through our donutList variable using the foreach() function.

val priceOfPlainDonut = donutList.foreach { tuple => {
  tuple match {
    case ("Plain Donut", taste, price) => println(s"Donut type = Plain Donut, price = $price")
    case d if d._1 == "Glazed Donut" => println(s"Donut type = ${d._1}, price = ${d._3}")
    case _ => None
    }
  }
}
You should see the following output when you run your Scala application in IntelliJ:

Step 4: How to use pattern matching on Tuples
Donut type = Glazed Donut, price = 2.5
Donut type = Plain Donut, price = 2
NOTE:
•	We've used two flavors of case expressions similar to what we've learned from the previous Pattern Matching tutorial.
•	The first case expression case ("Plain Donut", taste, price) will match for Plain Donut and then store the taste and price data points into variables which you can then referenced.
•	The second case expression case d if d._1 == "Glazed Donut" extracts a local variable named d and will only match on Glazed Donut.
•	We've also provided a default case using the wildcard underscore _ and simply return None.
5. Shortcut for creating Tuples
Using Tuples is so common that Scala has an elegant shortcut which we can use to create Tuples. You can simply enclose your data points within ()

println("\nStep 5: Shortcut for creating Tuples")
val chocolateDonut = ("Chocolate Donut", "Very Tasty", 3.0)
println(s"Chocolate donut taste level = ${chocolateDonut._2}, price = ${chocolateDonut._3}")
You should see the following output when you run your Scala application in IntelliJ:

Step 5: Shortcut for creating Tuples
Chocolate donut taste level = Very Tasty, price = 3.0
This concludes our tutorial on Learn How To Use Tuples (Pattern Match) and I hope you've found it useful!
Learn How To Use Option - Avoid Null
By Nadim Bahadoor | Last updated: March 16, 2018 at 15:14 pm
Overview
In this tutorial, we will show how to use Option, Some and None. 
 
If you have used other programming languages in the past such as Java or .NET, I'm pretty sure that you must have seen your share of NullPointerException!
 
By making use of Option, Some and None, Scala encourages you to write functions with no side effects as we've described in the Scala Features tutorial. As a result, all your headaches with NullPointerException should go away :)
Steps
1. How to use Option and None - a basic example
Let's declare a simple String called glazedDonutTaste. But instead of its type being just a String, you will declare it as an Option of type String using the syntax Option[String].
You can then assign its value using the Some class and pass in your donut taste String of Very Tasty.

println("Step 1: How to use Option and None - a basic example")
val glazedDonutTaste: Option[String] = Some("Very Tasty")
println(s"Glazed Donut taste = ${glazedDonutTaste.get}")
You should see the following output when you run your Scala application in IntelliJ:

Step 1: How to use Option and None - a basic example
Glazed Donut taste = Very Tasty
NOTE:
•	Because we have wrapped our String into an Option, to retrieve its value we call the get() function as shown above.
•	But calling get() in a production system is generally a code smell as you may end up with the same NullPointerException.
2. How to use Option and None - a basic example
Let's use another variable called glazedDonutName which is also an Option of type String. But instead of initializing it to a String which is wrapped up into a Some class as shown in Step 1, let's set its value to None.

println("\nStep 2: How to use Option and None - a basic example")
val glazedDonutName: Option[String] = None
println(s"Glazed Donut name = ${glazedDonutName.getOrElse("Glazed Donut")}")
You should see the following output when you run your Scala application in IntelliJ:

Step 2: How to use Option and None - a basic example
Glazed Donut name = Glazed Donut
NOTE:
•	We've used the handy getOrElse() function from the Option to supply a default value.
•	If you were to call the get() function as shown in Step 1, you will get the exception java.util.NoSuchElementException: None.get.
•	At this point, you may be asking yourself that this exception is similar to your NullPointerException.
•	And you are absolutely right! But Pattern Matching is your friend :) let's look at Step 3 below.
3. How to use Pattern Matching with Option
Feel free to review the two previous tutorials Pattern Matching and Tuples.
You've already seen from Step 2 that you can use the getOrElse()  function to get a default value in case your variable had no data.
But you can also use Pattern Matching as shown below:

println("\nStep 3: How to use Pattern Matching with Option")
glazedDonutName match {
  case Some(name) => println(s"Received donut name = $name")
  case None       => println(s"No donut name was found!")
}
You should see the following output when you run your Scala application in IntelliJ:

Step 3: How to use Pattern Matching with Option
No donut name was found!
NOTE:
•	Sure, you can argue that we have not achieved much!
•	But, let's take a pause and assume that you were calling some function to populate your variable glazedDonutName
•	As a consumer of that function call, you would not know that the function could potentially return null.
•	What have we learned? It's all about intent!
•	By being explicit that such a function will return an Option, any consumer of the function can avoid NullPointerException by using getOfElse() or Pattern Matching.
•	Not to worry, we will see examples of functions which return Option in upcoming tutorials.
This concludes our tutorial on Learn How To Use Option - Avoid Null and I hope you've found it useful!
 
Stay in touch via Facebook and Twitter for upcoming tutorials!
 
Don't forget to like and share this page :)
Summary
In this tutorial, we went over the following:
•	How to use Option and Some
•	How to use Option and None
•	How to use Pattern Matching with Option
Tip
•	You can use the map() function as a more elegant way of filtering out None.
println("\nTip 1: Filter None using map function")
glazedDonutTaste.map(taste => println(s"glazedDonutTaste = $taste"))
glazedDonutName.map(name => println(s"glazedDonutName = $name"))
You should see the following output when you run your Scala application in IntelliJ:

Tip 1: Filter None using map function
glazedDonutTaste = Very Tasty
NOTE:
•	Notice that glazedDonutName was not printed as its value was None
•	If the map() function is completely new to you, don't worry we will see more examples when we get to the tutorials on functions.
Learn The Scala Class And Type Hierarchy
By Nadim Bahadoor | Last updated: March 16, 2018 at 15:14 pm
Overview
In this tutorial, we will have a closer look at Scala's type hierarchy. To help you visualize the type hierarchy in Scala, you can refer to the diagram below which is a snapshot from Scala's documentation on Unified Types.
 
The diagram shows that the type Any is at the top most of the Scala's class hierarchy.
 
If you are coming from Java or .NET, you can think of the Any type as the Object class. In other words, Any is the root type and it has two sub-classes namely AnyVal and AnyRef as per the above diagram.
 
So where are the built-in primitive types such as the ones we have in Java? The answer is simple, there are none!
Steps
1. Declare a variable of type Any
If you recall from the previous Type Inference tutorial, Scala is able to infer types.
But in this example let's type our immutable variable favoriteDonut as Any.

println("Step 1: Declare a variable of type Any")
val favoriteDonut: Any = "Glazed Donut"
println(s"favoriteDonut of type Any = $favoriteDonut")
You should see the following output when you run your Scala application in IntelliJ:

Step 1: Declare a variable of type Any
favoriteDonut of type Any = Glazed Donut
2. Declare a variable of type AnyRef
Let's declare another variable called donutName. But this time you will use the type AnyRef.

println("\nStep 2: Declare a variable of type AnyRef")
val donutName: AnyRef = "Glazed Donut"
println(s"donutName of type AnyRef = $donutName")
You should see the following output when you run your Scala application in IntelliJ:

Step 2: Declare a variable of type AnyRef
donutName of type AnyRef = Glazed Donut
3. Declare a variable of type AnyVal
Let's now declare another variable donutPrice to be of type AnyVal and assign its value to 2.50.

println("\nStep 3: Declare a variable of type AnyVal")
val donutPrice: AnyVal = 2.50
println(s"donutPrice of type AnyVal = $donutPrice")
You should see the following output when you run your Scala application in IntelliJ:

Step 3: Declare a variable of type AnyVal
AnyVal donutPrice = 2.5
This concludes our tutorial on Learn The Scala Class And Type Hierarchy and I hope you've found it useful!
 
Learn How To Create And Use Enumerations (enum)
By Nadim Bahadoor | Last updated: March 16, 2018 at 15:14 pm
Overview
In this tutorial, we will go over how to create and use enumerations in Scala.
 
If you have used Java or .NET in the past, I'm pretty sure that you have used the enumkeyword to define your enumerations.
 
But in Scala there is no enum keyword. Instead, Scala provides an Enumeration class which you can extend in order to create your enumerations.
Steps
1. How to create an Enumeration
Let us extend the Enumeration class and create an enumeration to represent donuts.

println("Step 1: How to create an enumeration")
object Donut extends Enumeration {
  type Donut = Value

  val Glazed      = Value("Glazed")
  val Strawberry  = Value("Strawberry")
  val Plain       = Value("Plain")
  val Vanilla     = Value("Vanilla")
}
2. How to print the String value of the enumeration
Now that we've created our Donut enumeration in Step 1, suppose you would like to print the String value for the Vanilla element.

println("\nStep 2: How to print the String value of the enumeration")
println(s"Vanilla Donut string value = ${Donut.Vanilla}")
You should see the following output when you run your Scala application in IntelliJ:

Step 2: How to print the String value of the enumeration
Vanilla Donut string value = Vanilla
3. How to print the id of the enumeration
Similar to Step 2, you first need to navigate down to the Vanilla element and then call the idfunction.

println("\nStep 3: How to print the id of the enumeration")
println(s"Vanilla Donut's id = ${Donut.Vanilla.id}")
You should see the following output when you run your Scala application in IntelliJ:

Step 3: How to print the id of the enumeration
Vanilla Donut's id = 3
NOTE:
•	But where did this magic id function come from?
•	If you recall from Step 1, you extended the Enumeration class. As a result, the Donut enumeration inherited a bunch of useful functions with the id function being one of them.
4. How to print all the values listed in Enumeration
What if you wanted to print all the values that are defined for the Donut enumeration?
 
Very easy! You simply need to call the values function on the Donut enumeration.

println("\nStep 4: How to print all the values listed in Enumeration")
println(s"Donut types = ${Donut.values}")
You should see the following output when you run your Scala application in IntelliJ:

Step 4: How to print all the values listed in Enumeration
Donut types = Donut.ValueSet(Glazed, Strawberry, Plain, Vanilla)
5. How to pattern match on enumeration values
Let's use what you've learned from the Pattern Matching tutorial, and find our favourite donuts namely Strawberry and Glazed :)

println("\nStep 5: How to pattern match on enumeration values")
Donut.values.foreach {
  case d if (d == Donut.Strawberry || d == Donut.Glazed) => println(s"Found favourite donut = $d")
  case _ => None
}
You should see the following output when you run your Scala application in IntelliJ:

Step 5: How to pattern match on enumeration values
Found favourite donut = Glazed
Found favourite donut = Strawberry
6. How to change the default ordering of enumeration values
Suppose you would like to change the default ordering of the enumeration values.
 
When you declare your enumeration elements, you can pass in the index as a parameter to the Value type.

println("\nStep 6: How to change the default ordering of enumeration values")
object DonutTaste extends Enumeration{
  type DonutTaste = Value

  val Tasty       = Value(0, "Tasty")
  val VeryTasty   = Value(1, "Very Tasty")
  val Ok          = Value(-1, "Ok")
}

println(s"Donut taste values = ${DonutTaste.values}")
println(s"Donut taste of OK id = ${DonutTaste.Ok.id}")
You should see the following output when you run your Scala application in IntelliJ:

Step 6: How to change the default ordering of enumeration values
Donut taste values = DonutTaste.ValueSet(Ok, Tasty, Very Tasty)
Donut taste of OK id = -1
NOTE:
•	The Ok element was moved to the front of the enumeration values.
This concludes our tutorial on Learn How To Create And Use Enumerations (enum) and I hope you've found it useful!
Learn How To Create And Use Functions
By Nadim Bahadoor | Last updated: March 16, 2018 at 15:14 pm
Overview
In this tutorial, we will learn the basics for creating and using functions in Scala.
Steps
1. How to define and use a function which has a return type
Let's create a simple function which will return the favorite donut as a String.
To define a function in Scala, you need to use the keyword def.
Then add the name of your function which in our case will be favoriteDonut followed by an empty pair of parenthesis (). 
To specify the return type you need to use the colon : followed by the return type which in our case is a String.
Finally, you will use the = followed by {} to enclose the body of your function

println("Step 1: How to define and use a function which has a return type")
def favoriteDonut(): String = {
  "Glazed Donut"
}

val myFavoriteDonut = favoriteDonut()
println(s"My favorite donut is $myFavoriteDonut")
You should see the following output when you run your Scala application in IntelliJ:

Step 1: How to define and use a function which has a return type
My favorite donut is Glazed Donut
NOTE:
•	We did not use any return keyword in favoriteDonut() as you would in say Java or .NET. The last line within the body of the function is the one that will be returned back to the caller.
•	In upcoming tutorial, we will also show that you can define functions using the valkeyword!
2. How to define and use a function with no parenthesis
If you are coming from another programming language such as Java or .NET, defining functions with no parenthesis will certainly be a shocker!

println("\nStep 2: How to define and use a function with no parenthesis")
def leastFavoriteDonut = "Plain Donut"
println(s"My least favorite donut is $leastFavoriteDonut")
You should see the following output when you run your Scala application in IntelliJ:

Step 2: How to define and use a function with no parenthesis
My least favorite donut is Plain Donut
NOTE:
•	In general, you should define your functions without parenthesis if you are defining a function that does not have any side effects.
•	We also did not provide a return type of String to the leastFavoriteDonut function to leverage what we've learned from the tutorial on Scala Type Inference.
3. How to define and use a function with no return type
In Step 1, we defined a function which had a return type of String. But what if you had to define a function which does not have any return type?

println("\nStep 3: How to define and use a function with no return type")
def printDonutSalesReport(): Unit = {
  // lookup sales data in database and create some report
  println("Printing donut sales report... done!")
}
printDonutSalesReport()
You should see the following output when you run your Scala application in IntelliJ:

Step 3: How to define and use a function with no return type
Printing donut sales report... done!
NOTE:
•	If you have used other mainstream languages such as Java or .NET, Unit is similar to using the void keyword in a method.
4. Use type inference to define function with no return type
Similar to Step 2, you can take advantage of Scala's type inference when defining a function which has no return type.

println("\nStep 4: Use type inference to define function with no return type")
def printReport {
  // lookup sales data in database and create some report
  println("Printing donut report... done!")
}
printReport
You should see the following output when you run your Scala application in IntelliJ:

Step 4: Use type inference to define function with no return type
Printing donut report... done!
NOTE:
•	Notice that we did not include the parenthesis () when calling the function printReport.  This feature becomes more useful and concise as you get to do function chainingwhich we will see in upcoming tutorials.
This concludes our tutorial on Learn How To Create And Use Functions and I hope you've found it useful!
Learn How To Create Function With Parameters
By Nadim Bahadoor | Last updated: March 16, 2018 at 15:14 pm
Overview
In this tutorial, we will learn how to create functions that take parameters as input in Scala. In addition, we will also see how you can assign default values to the parameters.
 
If you are unfamiliar with the syntax for defining functions, please review the previous tutorial on creating and using functions in Scala.
Steps
1. How to define function with parameters
To define a function with parameters, you need to enclose your input parameters within the parenthesis (). Suppose you would like to define a function called calculateDonutCost which will have the following parameters: donutName of type String and quantity of type Int.

println("Step 1: How to define function with parameters")
def calculateDonutCost(donutName: String, quantity: Int): Double = {
  println(s"Calculating cost for $donutName, quantity = $quantity")

  // make some calculations ...
  2.50 * quantity
}
NOTE:
•	Inside the body of our calculateDonutCost function, we are simply multiplying the quantity parameter by a hard coded price value of 2.50.
•	Notice that we explicitly added the return type of : Double = {...} to the function. Although we could have leveraged the type inference feature of Scala, it is a good practice to be explicit about the return types of your function.
2. How to call a function with parameters
To call the calculateDonutCost function which you've defined in Step 1, you simply need to call the function by its name, open parenthesis,  then fill in the blanks for the corresponding input parameters and then close parenthesis.
As an example, let's call our calculateDonutCost function with Glazed Donut as the first parameter of type String and then the number 5 as its second parameter of type Int.

println("\nStep 2: How to call a function with parameters")
val totalCost = calculateDonutCost("Glazed Donut", 5)
println(s"Total cost of donuts = $totalCost")
You should see the following output when you run your Scala application in IntelliJ:

Step 2: How to call a function with parameters
Calculating cost for Glazed Donut, quantity = 5
Total cost of donuts = 12.5
NOTE:
•	We've stored the value which is returned from our calculateDonutCost function into an immutable variable called totalCost.
•	Notice also that we are using Scala's type inference with the totalCost variable and as such did not explicitly specified its type of Double. In large code-base however, be wise about being explicit for your data points where necessary.
3. How to add default values to function parameters
What if some customers who present you a coupon code are eligible for additional discount when buying donuts from your store? Let's add another parameter named couponCode of type String. But, since not all customers will have a coupon code, let's default the value of couponCode to say "NO CODE".

println("\nStep 3: How to add default values to function parameters")
def calculateDonutCost(donutName: String, quantity: Int, couponCode: String = "NO CODE"): Double = {
  println(s"Calculating cost for $donutName, quantity = $quantity, couponCode = $couponCode")
// make some calculations ...
2.50 * quantity
}
NOTE:
•	Limit your use of defaulting parameters for simple cases only.
•	There are better ways to achieve the desired effect of some customers presenting a coupon code such as using Option which we will see in the next tutorial.
4. How to call a function with parameters that has default values
Since coupon code parameter is defined with a default value as shown in Step 3, you can then call calculateDonutCost function by either adding some coupon code or not!

println("\nStep 4: How to call a function with parameters that has default values")
val totalCostWithDiscount = calculateDonutCost("Glazed Donut", 4, "COUPON_12345")
val totalCostWithoutDiscount = calculateDonutCost("Glazed Donut", 4)
NOTE:
•	If you were using Java, you would have had to use method overloading to achieve the same desired effect.
•	However, the ability to provide a default value to function parameters in Scala is a much more elegant solution!
This concludes our tutorial on Learn How To Create Function With Parameters and I hope you've found it useful!
Learn How To Use Option In Function Parameters
By Nadim Bahadoor | Last updated: March 16, 2018 at 15:14 pm
Overview
In this tutorial, we will learn how to use the Option type to define and use functions which take optional parameters.
 
Feel free to review the tutorial from Chapter 2 on how to use Option, Some and None to help avoid the dreaded NullPointerException.
Steps
1. How to define an Option in a function parameter
Let's redo the example from the previous tutorial on Learn How To Create Function Parameters where we had provided a default value to the couponCode parameter.
 
To recap, our use case is that not all our customers who are buying donuts from our store would have a coupon code. Hence, the coupon code parameter should be optional.
 
In Scala, this means that you can declare couponCode using the Option type. Since our coupon code will be a String, couponCode parameter should be declared as: couponCode:Option[String]

println("Step 1: How to define an Option in a function parameter")
def calculateDonutCost(donutName: String, quantity: Int, couponCode: Option[String]): Double = {
  println(s"Calculating cost for $donutName, quantity = $quantity")

  couponCode match {
    case Some(coupon) =>
    val discount = 0.1 // Let's simulate a 10% discount
    val totalCost = 2.50 * quantity * (1 - discount)
    totalCost

    case None => 2.50 * quantity
  }
}
NOTE:
•	Inside our function, we will test for a valid couponCode using pattern matching.
•	In the case of Some(coupon), we assume a database lookup for the discount that needs to be applied. But, in our example, we will assume the discount is 10%.
•	As part of the pattern matching, we also provide the None case where no couponCode was passed-through.
2. How to call a function which has an Option parameter
Let's use the function defined in Step 1 to calculate the cost for a customer buying 5 Glazed Donuts:

println("\nStep 2: How to call a function which has an Option parameter")
println(s"""Total cost = ${calculateDonutCost("Glazed Donut", 5, None)}""")
You should see the following output when you run your Scala application in IntelliJ:

Step 2: How to call a function which has an Option parameter
Calculating cost for Glazed Donut, quantity = 5
Total cost = 12.5
NOTE:
•	Since our customer does not have a couponCode, we had to supply a None as the couponCode parameter.
•	Providing a None for every Option parameter is perhaps not very elegant. Fortunately, this is easily solved - see Step 3 below.
3. How to assign a default value to an Option parameter
To assign a default value of None as part of the declaration for couponCode parameter, you can use the following syntax:

println("\nStep 3: How to assign a default value to an Option parameter")
def calculateDonutCostWithDefaultOptionValue(donutName: String, quantity: Int, couponCode: Option[String] = None): Double = {
  println(s"Calculating cost for $donutName, quantity = $quantity")

  couponCode match{
    case Some(coupon) =>
      val discount = 0.1 // Let's simulate a 10% discount
      val totalCost = 2.50 * quantity * (1 - discount)
      totalCost

    case _ => 2.50 * quantity
  }
}
 
4. How to call a function whose Option parameter has a default value
Using the function defined in Step 3, you no longer have to pass-through a None value for the Option couponCode parameter.
 
If you have a legitimate couponCode to pass-through, you can use Some() as shown below:

println(\n"Step 4: How to call a function which has an Option parameter with a default value")
println(s"""Total cost = ${calculateDonutCostWithDefaultOptionValue("Glazed Donut", 5)}""")
println(s"""Total cost with discount = ${calculateDonutCostWithDefaultOptionValue("Glazed Donut", 5, Some("COUPON_1234"))}""")
You should see the following output when you run your Scala application in IntelliJ:

Step 4: How to call a function which has an Option parameter with a default value
Calculating cost for Glazed Donut, quantity = 5
Total cost = 12.5
Calculating cost for Glazed Donut, quantity = 5
Total cost with discount = 11.25
This concludes our tutorial on Learn How To Use Option In Function Parameters and I hope you've found it useful!


Scala Tutorial - Learn How To Create Function With Option Return Type
By Nadim Bahadoor | Last updated: March 16, 2018 at 15:14 pm
Overview
In this tutorial, we will learn how to create and use function whose return type is an Option.
 
Feel free to review the tutorial from Chapter 2 on how to use Option, Some and None to help avoid the dreaded NullPointerException.
Steps
1. How to define a function which returns an Option of type String
Let's define a function named dailyCouponCode() which will assume a database lookup to provide our customers with a daily coupon code.
 
Since there may or may not be a daily coupon code available, it would be a good idea for the users of our dailyCouponCode() function to be aware explicitly of the possibility that the daily coupon code may be empty.
 
As such, you can define the dailyCouponCode() function's return type to be an Option of the type String.

println(s"Step 1: Define a function which returns an Option of type String")
def dailyCouponCode(): Option[String] = {
  // look up in database if we will provide our customers with a coupon today
  val couponFromDb = "COUPON_1234"
  Option(couponFromDb).filter(_.nonEmpty)
}
NOTE:
•	We are also lifting the couponFromDb value into an Option which will perform a null check.
•	We then remove any empty strings using the filter() function.
2. How to call function with Option return type using getOrElse
Since the dailyCouponCode() function from Step 1 returns an Option of type String, you should use getOrElse() function when retrieving its return value.

println(s"\nStep 2: Call function with Option return type using getOrElse")
val todayCoupon: Option[String] = dailyCouponCode()
println(s"Today's coupon code = ${todayCoupon.getOrElse("No Coupon's Today")}")
You should see the following output when you run your Scala application in IntelliJ:

Step 2: Call function with Option return type using getOrElse
Today's coupon code = COUPON_1234
NOTE:
•	When using getOrElse() function, you need to also provide a default value which in our case will be "No Coupon's Today".
3. How to call a function with Option return type using pattern matching
By now you should have seen pattern matching in the previous tutorials, otherwise feel free to review the tutorial on pattern matching. As such you can use pattern matching on the return value of a function with Option return type and provide the behaviours for the Some or None case.

println(s"\nStep 3: Call function with Option return type using pattern matching")
dailyCouponCode() match {
  case Some(couponCode) => println(s"Today's coupon code = $couponCode")
  case None => println(s"Sorry there is no coupon code today!")
}
You should see the following output when you run your Scala application in IntelliJ:

Step 3: Call function with Option return type using pattern matching
Today's coupon code = COUPON_1234
4. How to call function with Option return type using map() function
When using the getOrElse() function or pattern matching on a function which returns an Option, you will need to provide the default or None case.
 
However, if you only care about valid values from the Option, you can use the map() function.

println(s"\nStep 4: Call function with Option return type using map")
dailyCouponCode().map(couponCode => println(s"Today's coupon code = $couponCode"))
You should see the following output when you run your Scala application in IntelliJ:

Step 4: Call function with Option return type using map
Today's coupon code = COUPON_1234
5. Review function calculateDonutCost() function from previous tutorial
Let's review the calculateDonutCost() function from the previous tutorial Learn How To Use Option In Function Parameters which has an Option parameter for couponCode.
 

println("\nStep 5: Review function from previous tutorial which has an Option parameter")
def calculateDonutCost(donutName: String, quantity: Int, couponCode: Option[String]): Double = {
  println(s"Calculating cost for $donutName, quantity = $quantity")

  couponCode match {
    case Some(coupon) =>
      val discount = 0.1 // Let's simulate a 10% discount
      val totalCost = 2.50 * quantity * (1 - discount)
      totalCost

    case None => 2.50 * quantity
  }
}
Now you can pass it our dailyCouponCode() function from Step 1.

// apply daily coupon code if we have one
println(s"""Total cost with daily coupon code = ${calculateDonutCost("Glazed Donut", 5, dailyCouponCode())}""")
You should see the following output when you run your Scala application in IntelliJ:

Step 5: Review function from previous tutorial which has an Option parameter
Calculating cost for Glazed Donut, quantity = 5
Total cost with daily coupon code = 11.25
This concludes our tutorial on Learn How To Create Function With Option Return Type and I hope you've found it useful!
Scala Tutorial - Learn How To Create Function With Implicit Parameters
By Nadim Bahadoor | Last updated: March 16, 2018 at 15:14 pm
Overview
In this tutorial, we will learn how to create and use function which has implicit parameters.
 
The use of implicit parameters is just one example of how dependency injection can be achieved in Scala. As a matter of fact, dependency injection is built-into the Scala language such that you do not have to import another third party library such as Google Guice.
 
Feel free to review the Scala Features tutorial where dependency injection is outlined as being a first class citizen of the Scala language.
Steps
1. How to define a function which has an implicit parameter
In line with the examples from the previous tutorial, let us define a function to calculate the total cost when buying donuts by taking into account that our customers can benefit from a discount. To this end, we will define the discount parameter as implicit as shown below:

println(s"Step 1: How to define a function with an implicit parameter")
def totalCost(donutType: String, quantity: Int)(implicit discount: Double): Double = {
  println(s"Calculating the price for $quantity $donutType")
  val totalCost = 2.50 * quantity * (1 - discount)
  totalCost
}
NOTE:
•	The implicit parameter discount of type Double is defined using the keyword implicitwithin parenthesis after your usual function parameters.
•	This means that the totalCost() function will require an implicit value of type Double to be in scope as defined in Step 2 below.
2. How to define an implicit value
The totalCost() function you've defined in Step 1 expects an implicit value of type Double to be in scope whenever the totalCost() function is called.
 
Therefore, you will define an implicit value of type Double somewhere within your codebase. Defining an implicit value is similar to defining any other values using the val keyword, except that you prefix the val keyword with the implicit keyword as well.

println("\nStep 2: How to define an implicit value")
implicit val discount: Double = 0.1
println(s"All customer will receive a ${discount * 100}% discount")
 
3. How to call a function which has an implicit parameter
Calling the totalCost() function is similar to calling any other function, except that you will nothave to provide the implicit discount parameter.

println("\nStep 3: How to call a function which has an implicit parameter")
println(s"""Total cost with discount of 5 Glazed Donuts = ${totalCost("Glazed Donut", 5)}""")
You should see the following output when you run your Scala application in IntelliJ:

Step 3: How to call a function which has an implicit parameter
Calculating the price for 5 Glazed Donut
Total cost with discount of 5 Glazed Donuts = 11.25
NOTE:
•	You did not have to manually pass-through the discount value when calling the totalCost() function.
•	The Scala compiler will look for an implicit value of type Double for the discount implicit parameter which you've defined in Step 2.
•	If there are no implicit values in scope, you will get a compiler error.
4. How to define a function which takes multiple implicit parameters
Defining additional implicit parameters is similar to defining any other parameters and you simply needs to separate the parameters using a comma.
 
As an example, let us expand the totalCost() function to take an implicit parameter of type String which will represent our Donut Store name.

println("\nStep 4: How to define a function which takes multiple implicit parameters")
def totalCost2(donutType: String, quantity: Int)(implicit discount: Double, storeName: String): Double = {
  println(s"[$storeName] Calculating the price for $quantity $donutType")
  val totalCost = 2.50 * quantity * (1 - discount)
  totalCost
}
5. How to call a function which takes multiple implicit parameters
As per Step 4 above, the totalCost() function now expects an additional implicit value of type String.
 
Therefore, you need to first define another implicit value of type String so that it is in scope before you can call the totalCost() function.

println("\nStep 5: How to call a function which takes multiple implicit parameters")
implicit val storeName: String = "Tasty Donut Store"
println(s"""Total cost with discount of 5 Glazed Donuts = ${totalCost2("Glazed Donut", 5)}""")
You should see the following output when you run your Scala application in IntelliJ:

Step 5: How to call a function which takes multiple implicit parameters
[Tasty Donut Store] Calculating the price for 5 Glazed Donut
Total cost with discount of 5 Glazed Donuts = 11.25
6. How to manually pass-through implicit parameters
In rare occasions, you may have to manually pass-through the implicit parameter values. This can be done by passing the implicit parameters through another pair of parenthesis as shown below.

println("\nStep 6: How to manually pass-through implicit parameters")
println(s"""Total cost with discount of 5 Glazed Donuts, manually passed-through = ${totalCost2("Glazed Donut", 5)(0.1, "Scala Donut Store")}""")
You should see the following output when you run your Scala application in IntelliJ:

Step 6: How to manually pass-through implicit parameters
[Scala Donut Store] Calculating the price for 5 Glazed Donut
Total cost with discount of 5 Glazed Donuts, manually passed-through = 11.25
This concludes our tutorial on Learn How To Create Function With Implicit Parameters and I hope you've found it useful!
Scala Tutorial - Learn How To Create Implicit Function
By Nadim Bahadoor | Last updated: March 16, 2018 at 15:14 pm
Overview
In this tutorial, we will learn how to create implicit function which will allow you to provide extension methods or functions to pretty much any type or class.
 
As the name implies, Scala was designed from the ground up to be extensible. Feel free to review the Scala Features tutorial which outlines the use of implicit as one of the features which Scala provides to allow you to easily add extension methods or functions to any type or class.
 
To continue with our Donut Store examples from the previous tutorials, we will extend the String class such that it will have an isFavoriteDonut() function.
Steps
1. How to create a wrapper String class which will extend the String type
Let us create a simple wrapper class called DonutString which will take the String type as its parameter and then provide an isFavoriteDonut() function.

println("Step 1: How to create a wrapper String class which will extend the String type")
class DonutString(s: String) {

  def isFavoriteDonut: Boolean = s == "Glazed Donut"

}
NOTE:
•	If you are coming from a Java or .NET programming background, you would perhaps be pleasantly surprised that in Scala you can simply compare two Strings using == as opposed to using equals() method.
2. How to create an implicit function to convert a String to the wrapper String class
It is a good practice to encapsulate your implicit functions or conversions into a singletonusing object. You can also make use of package object which we will see in upcoming tutorials.
 
As such, let us define an implicit function named stringToDonutString which will take the String type as its parameter and wire it through a new instance of the wrapper String class named DonutString from Step 1.

println("\nStep 2: How to create an implicit function to convert a String to the wrapper String class")
object DonutConverstions {
  implicit def stringToDonutString(s: String) = new DonutString(s)
}
NOTE:
•	Defining an implicit function is similar to defining any other functions except that we've prefixed the function signature using the implicit keyword.
3. How to import the String conversion so that it is in scope
In order to use the implicit String function which will convert a String type into a DonutString type, you will have to have the implicit function from Step 2 in scope. This can be achieved using the import keyword as shown below:

println("\nStep 3: How to import the String conversion so that it is in scope")
import DonutConverstions._
NOTE:
•	As part of the import expression, we are using the wildcard operator _ which will import any values or implicit functions.
4. How to create String values
Let us create two immutable values of type String, one for Glazed Donut and the other for Vanilla Donut.

println("\nStep 4: How to create String values")
val glazedDonut = "Glazed Donut"
val vanillaDonut = "Vanilla Donut"
NOTE:
•	By now, you should be familiar with declaring variables and immutable values.
•	Feel free to review the tutorial on declaring variables.
5. How to access the custom String function called isFavaoriteDonut
How would you access the isFavoriteDonut() function from Step 1? Simple - just call it on the Glazed Donut or Vanilla Donut String values.

println("\nStep 5: How to access the custom String function called isFavaoriteDonut")
println(s"Is Glazed Donut my favorite Donut = ${glazedDonut.isFavoriteDonut}")
println(s"Is Vanilla Donut my favorite Donut = ${vanillaDonut.isFavoriteDonut}")
You should see the following output when you run your Scala application in IntelliJ:

Step 5: How to access the custom String function called isFavaoriteDonut
Is Glazed Donut my favorite Donut = true
Is Vanilla Donut my favorite Donut = false
NOTE:
•	The custom isFavoriteDonut() function looks built-into the String class.
•	However, we did not have to manually modify the source code of the String class.
•	Instead, we've used the secret powers of Scala's implicit function to extend the String class.
Scala Tutorial - Learn How To Create Typed Function
By Nadim Bahadoor | Last updated: March 16, 2018 at 15:14 pm
Overview
In this tutorial, we will learn how to create typed functions which will allow you to specify the types of the parameters when calling the function.
 
In addition, we will make use of what we've learned from the Pattern Matching Tutorial when creating our typed functions.
Steps
1. How to define a function which takes a String parameter
Let's start with a simple function to calculate the discount which our customers will receive when buying donuts from our store. The function will have a parameter of type String.
 
By now you should be familiar with how to define functions in Scala. If you do not know how to define functions in Scala, proceed to the tutorial on creating and using functions.

println("Step 1: How to define a function which takes a String parameter")
def applyDiscount(couponCode: String) {
  println(s"Lookup percentage discount in database for $couponCode")
}
 
2. How to define a function which takes a parameter of type Double
Similar to Step 1, let's define another function to calculate the discount for our customers. But this time our function will take a parameter of type Double.

println("\nStep 2: How to define a function which takes a parameter of type Double")
def applyDiscount(percentageDiscount: Double) {
  println(s"$percentageDiscount discount will be applied")
}
 
3. Calling applyDiscount function with String or Double parameter types
Calling the applyDiscount() function which takes a parameter of type String or Double should be familiar to you already if you've followed the tutorial on creating an using functions.

println("\nStep 3: Calling applyDiscount function with String or Double parameter types")
applyDiscount("COUPON_1234")
applyDiscount(10)
You should see the following output when you run your Scala application in IntelliJ:

Step 3: Calling applyDiscount function with String or Double parameter types
Lookup percentage discount in database for COUPON_1234
10.0 discount will be applied
 
4. How to define a generic typed function which will specify the type of its parameter
With the applyDiscount() function from Step 1 and Step 2 in mind, let us create another applyDiscount() function which will not specify the types of its parameters.
 
Instead, we will create a typed function which will specify a generic parameter of type T as follows:

println("\nStep 4: How to define a generic typed function which will specify the type of its parameter")
def applyDiscount[T](discount: T) {
  discount match {
    case d: String =>
      println(s"Lookup percentage discount in database for $d")

    case d: Double =>
      println(s"$d discount will be applied")

    case _ => 
      println("Unsupported discount type")
  }
}
NOTE:
•	We are making use of what we've learned from the Pattern Matching Tutorial to provide the corresponding code block if the parameter type is a String, Double or anything else.
5. How to call a function which has typed parameters
To call the typed function applyDiscount() from Step 4, you must provide the type of its parameters.

println("\nStep 5: How to call a function which has typed parameters")
applyDiscount[String]("COUPON_123")
applyDiscount[Double](10)
You should see the following output when you run your Scala application in IntelliJ:

Step 5: How to call a function which has typed parameters
Lookup percentage discount in database for COUPON_123
10.0 discount will be applied
This concludes our tutorial on Learn How To Create Typed Function and I hope you've found it useful!

Scala Tutorial - Learn How To Create Polymorphic Function With Generic Return Type
By Nadim Bahadoor | Last updated: March 16, 2018 at 15:14 pm
Overview
In this tutorial, we will learn how to create polymorphic functions which will allow you to specify the types of the parameters as well as the return type of the function.
 
This tutorial is a continuation of the previous tutorial on Typed Functions where you learned how to create functions which have typed parameters.
Steps
1. Review how to define a generic typed function which will specify the type of its parameter
Let's first review what we've learned from the previous tutorial on Typed Functions. Typed functions allow you to define functions where you can specify the type of its parameters.
 
In the previous tutorial, we defined an applyDiscount() function which has a generic type parameter named discount.

println("\nStep 1: Review how to define a generic typed function which will specify the type of its parameter")
def applyDiscount[T](discount: T) {
  discount match {
    case d: String =>
      println(s"Lookup percentage discount in database for $d")

    case d: Double =>
      println(s"$d discount will be applied")

    case _ =>
      println("Unsupported discount type")
  }
}
 
2. Review how to call a function which has typed parameters
To call the typed function applyDiscount() from Step 1, you have to specify the type of the discount parameter as follows:

println("\nStep 2: Review how to call a function which has typed parameters")
applyDiscount[String]("COUPON_123")
applyDiscount[Double](10)
You should see the following output when you run your Scala application in IntelliJ:

Step 2: Review how to call a function which has typed parameters
Lookup percentage discount in database for COUPON_123
10.0 discount will be applied
NOTE:
•	Sure you can rely on Scala's type inference to infer the type of your function parameter.
•	But in general it's a good practice to explicitly specify your parameter types.
3. How to define a polymorphic typed function which also has a generic return type
With the applyDiscount() function from Step 1 in mind, let us define another function which will be polymorphic in nature. We will name the function applyDiscountWithReturnType() and it will take a generic type T for its discount parameter. But it will also return a Sequence of the type T.

println("\nStep 3: How to define a generic typed function which also has a generic return type")
def applyDiscountWithReturnType[T](discount: T): Seq[T] = {
  discount match {
    case d: String =>
      println(s"Lookup percentage discount in database for $d")
      Seq[T](discount)

  case d: Double =>
      println(s"$d discount will be applied")
      Seq[T](discount)

  case d @ _ =>
      println("Unsupported discount type")
      Seq[T](discount)
  }
}
NOTE:
•	For simplicity, we are returning a new Sequence of type T for each of the cases within the pattern match.
4. How to call a generic polymorphic function which also has a generic return type
Let us call the polymorphic applyDiscountWithReturnType() function from Step 3 with different types namely String, Double and Char.

println("\nStep 4: How to call a generic typed function which also has a generic return type")
println(s"Result of applyDiscountWithReturnType with String parameter = ${applyDiscountWithReturnType[String]("COUPON_123")}")

println()
println(s"Result of applyDiscountWithReturnType with Double parameter = ${applyDiscountWithReturnType[Double](10.5)}")

println()
println(s"Result of applyDiscountWithReturnType with Char parameter = ${applyDiscountWithReturnType[Char]('U')}")
You should see the following output when you run your Scala application in IntelliJ:

Step 4: How to call a generic typed function which also has a generic return type
Lookup percentage discount in database for COUPON_123
Result of applyDiscountWithReturnType with String parameter = List(COUPON_123)

10.5 discount will be applied
Result of applyDiscountWithReturnType with Double parameter = List(10.5)

Unsupported discount type
Result of applyDiscountWithReturnType with Char parameter = List(U)
NOTE:
•	For each of the specified types used when calling the polymorphic function applyDiscountWithReturnType(), the function also returns the Sequence of the same type.
Scala Tutorial - Learn How To Create Variable Argument Function - varargs :_ *
By Nadim Bahadoor | Last updated: March 16, 2018 at 15:14 pm
Overview
In this tutorial, we will learn how to create functions which take variable arguments or varargs. In addition, you will learn how to pass-through Scala collection such as List or Sequence or even an Array to variable argument function using the syntax :_ *.
Steps
1. How to define function which takes variable number of arguments
As a simple example, let's define a function named printReport() and it will have a single variable argument which represents the names of donuts for which we will print a report.

def printReport(names: String*) {
println(s"""Donut Report = ${names.mkString(", ")}""")
}
NOTE:
•	The names argument is of type String, but it is also a variable argument as we've defined it using the * syntax.
•	As a variable argument, you will be allowed to call the printReport() function by passing zero or many parameters of type String as shown in Step 2 below.
2. How to call function which takes variable number of String arguments
Since the printReport() function takes a variable argument called names of type String, you are allowed to call the function with zero or many String values.

println("\nStep 2: How to call function which takes variable number of String arguments")
printReport("Glazed Donut", "Strawberry Donut", "Vanilla Donut")
printReport("Chocolate Donut")
You should see the following output when you run your Scala application in IntelliJ:

Step 2: How to call function which takes variable number of String arguments
Donut Report = Glazed Donut, Strawberry Donut, Vanilla Donut
Donut Report = Chocolate Donut
 
3. How to pass a List to a function with variable number of arguments
What if you had a variable argument function and had to pass in a List to it?

println("\nStep 3: How to pass a List to a function with variable number of arguments")
val listDonuts: List[String] = List("Glazed Donut", "Strawberry Donut", "Vanilla Donut")
printReport(listDonuts)
NOTE:
•	Calling printReport() function by passing it the listDonuts value which is a List of type String will give you a compiler error!
Instead, you will need to use a special syntax called type ascription as follows:

printReport(listDonuts: _*)
You should see the following output when you run your Scala application in IntelliJ:

Step 3: How to pass a List to a function with variable number of arguments
Donut Report = Glazed Donut, Strawberry Donut, Vanilla Donut
 
4. How to pass a Sequence to a function with variable number of arguments
What if you had a variable argument function and had to pass in a Sequence to it?

println("\nStep 4: How to pass a Sequence to a function with variable number of arguments")
val seqDonuts: Seq[String] = Seq("Chocolate Donut", "Plain Donut")
printReport(listDonuts)
NOTE:
•	Calling printReport() function by passing it the seqDonuts value which is a Sequence of type String will give you a compiler error!
Instead, you will need to use a special syntax called type ascription as follows:

printReport(seqDonuts: _*)
You should see the following output when you run your Scala application in IntelliJ:

Step 4: How to pass a Sequence to a function with variable number of arguments
Donut Report = Glazed Donut, Strawberry Donut, Vanilla Donut
 
5. How to pass an Array to a function with variable number of arguments
What if you had a variable argument function and had to pass in a Array to it?

println("\nStep 5: How to pass an Array to a function with variable number of arguments")
val arrDonuts: Array[String] = Array("Coconut Donut")
printReport(arrDonuts)
NOTE:
•	Calling printReport() function by passing it the arrDonuts value which is a Array of type String will give you a compiler error!
Instead, you will need to use a special syntax called type ascription as follows:

printReport(arrDonuts: _*)
You should see the following output when you run your Scala application in IntelliJ:

Step 5: How to pass an Array to a function with variable number of arguments
Donut Report = Coconut Donut
This concludes our tutorial on Learn How To Create Variable Argument Function - varargs _: * and I hope you've found it useful!
Scala Tutorial - Learn How To Create Functions As Symbols
By Nadim Bahadoor | Last updated: March 16, 2018 at 15:14 pm
Overview
In this tutorial, we will learn how to create functions which are named using just symbols as opposed to alphabets. This feature of Scala is a great building block when you have to create Domain Specific Language syntax.
 
A great example would be the use of the ! symbol in the Akka Framework when sending messages to an Akka Actor.

myActor ! "Hello World"
Steps
1. How to create and instantiate a class
Let's start with creating a class named DonutCostCalculator and hard-coding a value for the total cost as 100. I'm sure in practice you will not be hard-coding the total cost value in your program :)

class DonutCostCalculator {

// We are hard-coding the totalCost value for simplicity.
val totalCost = 100
}
Next, let's add a function named minusDiscount() which will return the totalCost - some discount parameter.

def minusDiscount(discount: Double): Double = {
  totalCost - discount
}
Next, let's create an instance of the DonutCostCalculator as follows:

println("Step 1: How to create and instantiate a class")
val donutCostCalculator = new DonutCostCalculator()
 
2. How to call a function from an instantiated class
If you have used Java or .NET in the past, calling a function on an instantiated class should feel very familiar.
 
To call the minusDiscount() function, you simply need to call the function on the donutCostCalculator value.

println("\nStep 2: How to call a function from an instantiated class")
println(s"Calling minusDiscount() function = ${donutCostCalculator.minusDiscount(10.5)}")
NOTE:
•	Since the minusDiscount() function accepts a Double as its parameter, we are passing some random double of 10.5.
3. How to define function whose name is just the symbol minus  
Defining a function whose name is a symbol is essentially identical to defining any other functions. Instead of having a name, the function will be defined with some symbol.

// Step 3: How to define function whose name is just the symbol minus -
def -(discount: Double): Double = {
  totalCost - discount
}
NOTE:
•	We've defined a function called - where the name of function is simply the symbol -itself.
4. How to call function whose name is just a symbol
Calling a function whose name is just a symbol like the - function from Step 3 above is no different than how you would call any other functions.

println("\nStep 4: How to call function whose name is just the symbol -")
println(s"Calling function - = ${donutCostCalculator.-(10.5)}")
You should see the following output when you run your Scala application in IntelliJ:

Step 4: How to call function whose name is just the symbol -
Calling function - = 89.5
 
5. How to call a function using the operator style notation
Scala allows you to call functions using the operator style notation as shown below:

println("\nStep 5: How to call a function using the operator style notation")
println(s"Calling function - with operator style notation = ${donutCostCalculator - 10.5}")
You should see the following output when you run your Scala application in IntelliJ:

Step 5: How to call a function using the operator style notation
Calling function - with operator style notation = 89.5
NOTE:
•	Calling a function using the operator style is not much different than calling a function except that you do not need to specify the .
•	Using operator style is more clear when calling functions whose names are just symbols.
6. How to define function whose name is just the symbols +++
Now that you know how to define functions whose names are just symbols, let us create another function named +++.

// Step 6: How to define function whose name is just the symbols +++
def +++(taxAmount: Double): Double = {
  totalCost + taxAmount
}
NOTE:
•	This is where it starts getting a bit trickier when defining functions with symbols.
•	Is +++ clear that we are adding some taxes to the totalCost? Probably not!
•	While using functions which are defined as symbols can be very powerful, try not to abuse this feature as shown here.
Scala Tutorial - Learn How To Create Function Currying With Parameter Groups
By Nadim Bahadoor | Last updated: March 16, 2018 at 15:14 pm
Overview
In this tutorial, we will learn how to create functions whose parameters are organized into parameter groups - also known as Function Currying.
 
In addition, you will be introduced to creating Partially Applied Functions from curriedfunctions.
Steps
1. How to define function with curried parameter groups
By now you should be familiar with defining functions with parameters if you have followed Chapter 3 tutorials on functions.
 
However, Scala also allows you to create functions where each parameter is enclosed within its own group using the () as shown below:

println("Step 1: How to define function with curried parameter groups")
def totalCost(donutType: String)(quantity: Int)(discount: Double): Double = {
  println(s"Calculating total cost for $quantity $donutType with ${discount * 100}% discount")
  val totalCost = 2.50 * quantity
  totalCost - (totalCost * discount)
}
NOTE:
•	Functions defined with parameter groups are also commonly referred to as curried functions.
•	Each parameter is enclosed within () and there is no need to separate each parameter with comma as you would when defining a function with parameters.
2. How to call a function with curried parameter groups
When calling a curried function, you will need to fill in its parameters by enclosing each parameter within () as shown below:

println("\nStep 2: How to call a function with curried parameter groups")
println(s"Total cost = ${totalCost("Glazed Donut")(10)(0.1)}")
You should see the following output when you run your Scala application in IntelliJ:

Step 2: How to call a function with curried parameter groups
Calculating total cost for 10 Glazed Donut with 10.0% discount
Total cost = 22.5
 
3. How to create a partially applied function from a function with curried parameter groups
If you recall from the Scala Features tutorial, functions are designed from the ground up to be first class citizens in the language.
 
To this end, one common application of curried function is to be a building block where you can reuse functions by creating partial functions.
 
As a simple example, let's create a partially applied function named totalCostForGlazedDonuts which will call the curried totalCost() function from Step 1.

println("\nStep 3: How to create a partially applied function from a function with curried parameter groups")
val totalCostForGlazedDonuts = totalCost("Glazed Donut") _
NOTE:
•	totalCostForGlazedDonuts function was defined as a value function using the valkeyword as opposed to the def function. In upcoming tutorials, we will show additional examples of value functions.
•	totalCostForGlazedDonuts is a partially applied function because it only fills in the first parameter Glazed Donut. It uses the wildcard _ as a placeholder for the other parameters.
•	Note that the return type of the partially applied function totalCostForGlazedDonuts is Int => Double => Double. The first Int is for our quantity parameter, the Double is for discount parameter and the last Double the return type of the function. In short, the partially applied function creates a chain of functions.
4. How to call a partially applied function
Calling the partially applied function totalCostForGlazedDonuts is no different than how you've called the curried function totalCost in Step 2 by enclosing each parameter within ().
 
However, you do not need to fill in the first parameter for the donutType String parameter as you have already pre-filled it with the Glazed Donut String value in Step 3.

println("\nStep 4: How to call a partially applied function")
println(s"\nTotal cost for Glazed Donuts ${totalCostForGlazedDonuts(10)(0.1)}")
You should see the following output when you run your Scala application in IntelliJ:

Step 4: How to call a partially applied function
Calculating total cost for 10 Glazed Donut with 10.0% discount
Total cost for Glazed Donuts 22.5
This concludes our tutorial on Learn How To Create Function Currying With Parameter Groups and I hope you've found it useful!
 
Scala Tutorial - Learn How To Create Higher Order Function - Function As Parameter
By Nadim Bahadoor | Last updated: March 16, 2018 at 15:14 pm
Overview
In this tutorial, we will learn how to create Higher Order Function which is a function that takes another function as its parameter.
 
In addition, we will show how to pass-through an anonymous function or a regular deffunction to the Higher Order Function.
Steps
1. Review how to define function with curried parameter groups
Let's start by reviewing the totalCost() function from the previous tutorial on Curried Function With Parameter Groups.

println("Step 1: Review how to define function with curried parameter groups")
def totalCost(donutType: String)(quantity: Int)(discount: Double): Double = {
  println(s"Calculating total cost for $quantity $donutType with ${discount * 100}% discount")
  val totalCost = 2.50 * quantity
  totalCost - (totalCost * discount)
}
NOTE:
•	The totalCost() function has a discount parameter which could be a potential candidate to pass-through a function to apply the discount logic.
•	In other words, let's redefine the totalCost() function to take another function for the discount parameter a shown below in Step 2.
2. How to define a higher order function which takes another function as parameter
A Higher Order Function is a function which takes another function as its parameters.
 
Instead of the discount parameter, let's define a parameter which is a function that has an input parameter of type Double and will also return a type of Double using the syntax (f: Double => Double)

println("\nStep 2: How to define a higher order function which takes another function as parameter")
def totalCostWithDiscountFunctionParameter(donutType: String)(quantity: Int)(f: Double => Double): Double = {
  println(s"Calculating total cost for $quantity $donutType")
  val totalCost = 2.50 * quantity
  f(totalCost)
}
NOTE:
•	In the totalCostWithDiscountFunctionParameter() function, you call the function f by passing it the totalCost value
f(totalCost)
•	This function f will be provided at the time when you call thetotalCostWithDiscountFunctionParameter() function.
3. How to call higher order function and pass an anonymous function as parameter
The totalCostWithDiscountFunctionParameter() Higher Order Function defined in Step 2 now expects a discount function to be passed-through.
 
For this example, we will pass through an anonymous function which will apply the discount logic to the totalCost value as shown below:

println("\nStep 3: How to call higher order function and pass an anonymous function as parameter")
  val totalCostOf5Donuts = totalCostWithDiscountFunctionParameter("Glazed Donut")(5){totalCost =>
  val discount = 2 // assume you fetch discount from database
  totalCost - discount
}
println(s"Total cost of 5 Glazed Donuts with anonymous discount function = $totalCostOf5Donuts")
You should see the following output when you run your Scala application in IntelliJ:

Step 3: How to call higher order function and pass an anonymous function as parameter
Calculating total cost for 5 Glazed Donut
Total cost of 5 Glazed Donuts with anonymous discount function = 10.5
 
4. How to define and pass a function to a higher order function
A better approach to Step 3 is to pass-through a common discount function which would encapsulate the discount logic instead of providing an anonymous function.
 
To this end, let's create a function named applyDiscount as follows:

println("\nStep 4: How to define and pass a function to a higher order function")
def applyDiscount(totalCost: Double): Double = {
  val discount = 2 // assume you fetch discount from database
  totalCost - discount
}
You can then pass-through the applyDiscount() function to the totalCostWithDiscountFunctionParameter() function as follows:

println(s"Total cost of 5 Glazed Donuts with discount function = ${totalCostWithDiscountFunctionParameter("Glazed Donut")(5)(applyDiscount(_))}")
You should see the following output when you run your Scala application in IntelliJ:

Step 4: How to define and pass a function to a higher order function
Calculating total cost for 5 Glazed Donut
Total cost of 5 Glazed Donuts with discount function = 10.5
 
This concludes our tutorial on Learn How To Create Higher Order Function - Function As Parameter and I hope you've found it useful!
Scala Tutorial - Learn How To Create Higher Order Function - Call-By-Name Function
By Nadim Bahadoor | Last updated: March 16, 2018 at 15:14 pm
Overview
In this tutorial, we will learn how to create Higher Order Function which is a function that takes another function as its parameter.
 
This tutorial is a continuation of the previous Higher Order Function tutorial and we will showcase the difference between call-by-name and call-by-value function parameters.
Steps
1. How to define a List with Tuple3 elements
Let's start by defining a List containing Tuple3 elements which would represent the name of a donut, the quantity to be purchased and its price.
 
If you are unfamiliar with the Scala Tuple syntax, feel free to review the tutorial on Tuples.

println("Step 1: How to define a List with Tuple3 elements")
val listOrders = List(("Glazed Donut", 5, 2.50), ("Vanilla Donut", 10, 3.50))
 
2. How to define a function to loop through each Tuple3 elements of the List and calculate total cost
Assume that your donut store sells donuts worldwide and as such you need to convert the total cost of buying donuts to the local currency being used.
 
To this end, let's define a placeOrder() function which would take a list of donut orders as defined in Step 1. But the function also has an exchangeRate parameter to convert the total cost to the local currency.

println("\nStep 2: How to define a function to loop through each Tuple3 of the List and calculate total cost")
def placeOrder(orders: List[(String, Int, Double)])(exchangeRate: Double): Double = {
  var totalCost: Double = 0.0
  orders.foreach {order =>
    val costOfItem = order._2 * order._3 * exchangeRate
    println(s"Cost of ${order._2} ${order._1} = £$costOfItem")
    totalCost += costOfItem
  }
  totalCost
}
NOTE:
•	We could have inlined the totalCost calculation and avoid the use of var, but we are showing each step of the calculation.
•	We are also using parameter groups similar to what you've learned from the tutorial on Curried Function With Parameter Groups.
3. How to call function with curried group parameter for List of Tuple3 elements
The syntax for calling the placeOrder() function with currying parameters should be familiar to you already if you've followed the previous tutorials.

println("\nStep 3: How to call function with curried group parameter for List of Tuple3 elements")
println(s"Total cost of order = £${placeOrder(listOrders)(0.5)}")
You should see the following output when you run your Scala application in IntelliJ:

Step 3: How to call function with curried group parameter for List of Tuple3 elements
Cost of 5 Glazed Donut = £6.25
Cost of 10 Vanilla Donut = £17.5
Total cost of order = £23.75
NOTE:
•	For simplicity, we're using 0.5 as the exchange rate.
4. How to define a call-by-name function
You should have already seen the syntax for call-by-name function as per the previous tutorial on Higher Order Function.
 
As a result, let's redefine a placeOrder function which will accept a call-by-name parameter for the exchange rate.

println("\nStep 4: How to define a call-by-name function")
def placeOrderWithByNameParameter(orders: List[(String, Int, Double)])(exchangeRate: => Double): Double = {
  var totalCost: Double = 0.0
  orders.foreach {order =>
    val costOfItem = order._2 * order._3 * exchangeRate
    println(s"Cost of ${order._2} ${order._1} = £$costOfItem")
    totalCost += costOfItem
  }
  totalCost
}
NOTE:
•	The call-by-name function parameter exchangeRate: => Double will evaluate any exchangeRate function each time it is called.
•	This is in contrast to the function defined in Step 1 above which had a call-by-valuefunction parameter for exchange rate. This meant that any exchange rate passed through would be evaluated only once.
5. How to define a simple USD to GBP function
With the call-by-name exchange rate parameter from Step 4 in mind, let's create a function which will randomly generate a USD to GBP currency conversion.

println("\nStep 5: How to define a simple USD to GBP function")
val randomExchangeRate = new Random(10)
def usdToGbp: Double = {
  val rate = randomExchangeRate.nextDouble()
  println(s"Fetching USD to GBP exchange rate = $rate")
  rate
}
6. How to call function with call-by-name parameter
We can then pass the USD to GBP function to the placeOrderWithByNameParameter() function as shown below.
 

println("\nStep 6: How to call function with call-by-name parameter")
println(s"Total cost of order = £${placeOrderWithByNameParameter(listOrders)(usdToGbp)}")
You should see the following output when you run your Scala application in IntelliJ:

Step 6: How to call function with call-by-name parameter
Fetching USD to GBP exchange rate = 0.7304302967434272
Cost of 5 Glazed Donut = £9.13037870929284
Fetching USD to GBP exchange rate = 0.2578027905957804
Cost of 10 Vanilla Donut = £9.023097670852312
Total cost of order = £18.15347638014515
NOTE:
•	For each order in the list, a new exchange rate is being created and that's because the call-by-name function usdToGbp function is being evaluated each time
Scala Tutorial - Learn How To Create Higher Order Function - Callback Function Parameter
By Nadim Bahadoor | Last updated: March 16, 2018 at 15:14 pm
Overview
In this tutorial, we will learn how to create Higher Order Function which is a function that takes another function as its parameter.
 
This tutorial is a continuation of the previous Higher Order Function tutorial and we will showcase how to define a function which has a callback or Option callback parameter.
Steps
1. How to define a function with a callback parameter
Let's say that you have a function named printReport() which needs to be passed in a function for sending email once the report is completed.
 
You can define the printReport() function to have a call-by-name parameter of type unit that will essentially be the email callback function.

println("Step 1: How to define a function with a callback parameter")
def printReport(sendEmailCallback: () => Unit) {
  println("Printing report ... started")
  // look up some data in database and create a report
  println("Printing report ... finished")
  sendEmailCallback()
}
 
2. How to call a function which has a callback parameter
When calling the printReport() function from Step 1, you will need to pass in a callback function for sending email.

println("\nStep 2: How to call a function which has a callback parameter")
printReport(() =>
println("Sending email ... finished")
)
You should see the following output when you run your Scala application in IntelliJ:

Step 2: How to call a function which has a callback parameter
Printing report ... started
Printing report ... finished
Sending email ... finished
 
3. How to call a function without providing its callback parameter
What if you wanted to print the report but not send any email?

println("\nStep 3: How to call a function without providing its callback parameter")
// printReport() // You get compile time error
NOTE:
•	Calling printReport() function without passing a callback function will give you a compile time error.
You can instead pass in an empty anonymous function as shown below, although the syntax does not look that elegant:

printReport(() => {}) // Not that elegant.
 
4. How to define a function with an Option callback
Let's make use of what you've learned from the Option Tutorial and define another printReport() function which would have an Option callback parameter.

println("\nStep 4: How to define a function Function with an Option callback")
def printReportWithOptionCallback(sendEmailCallback: Option[() => Unit] = None) {
  println("Printing report ... started")
  // look up some data in database and create a report
  println("Printing report ... finished")
  sendEmailCallback.map(callback => callback())
}
NOTE:
•	We are using the map() function to filter out any None callback function.
5. How to call a function without providing its callback parameter
With the printReportWithOptionCallback() function from Step 4 above, you can now more elegantly call the print report function without having to specify any callback function.

println("\nStep 5: How to call a function without providing its callback parameter")
printReportWithOptionCallback() // more elegant
You should see the following output when you run your Scala application in IntelliJ:

Step 5: How to call a function without providing its callback parameter
Printing report ... started
Printing report ... finished
 
6. How to call a function with Option callback parameter
If you've followed the tutorial on Option, the syntax for calling a function with an Option parameter should be familiar to you.
 
With regards to the callback function parameter, you now need to wrap it within Some()

println("\nStep 6: How to call a function with Option callback parameter")
printReportWithOptionCallback(Some(() =>
  println("Sending email wrapped in Some() ... finished")
))
You should see the following output when you run your Scala application in IntelliJ:

Step 6: How to call a function with Option callback parameter
Printing report ... started
Printing report ... finished
Sending email wrapped in Some() ... finished
This concludes our tutorial on Learn How To Create Higher 
Scala Tutorial - Learn How To Create Function Using The Val Keyword Instead Of Def
By Nadim Bahadoor | Last updated: March 16, 2018 at 15:14 pm
Overview
In this tutorial, we will learn how to create value functions which are defined using the valkeyword as opposed to using the def keyword.
 
In addition, we will show how to pass through the val function to a Higher Order Function.
Steps
1. How to define a higher order function which takes another function as parameter
Let's review the function totalCostWithDiscountFunctionParameter() which we used in the Higher Order Function tutorial.

println("\nStep 1: How to define a higher order function which takes another function as parameter")
def totalCostWithDiscountFunctionParameter(donutType: String)(quantity: Int)(f: Double => Double): Double = {
  println(s"Calculating total cost for $quantity $donutType")
  val totalCost = 2.50 * quantity
  f(totalCost)
}
NOTE:
•	The function has a by-name parameter which is expected to be a function that has a parameter of type Double and will also return a type of Double.
•	The by-name parameter function will apply some discount to the totalCost value.
2. How to define and pass a def function to a higher order function
Let's also review how we defined a discount function using the def keyword and passed it to the Higher Order Function totalCostWithDiscountFunctionParameter()

println("\nStep 2: How to define and pass a def function to a higher order function")
def applyDiscount(totalCost: Double): Double = {
  val discount = 2 // assume you fetch discount from database
  totalCost - discount
}
println(s"Total cost of 5 Glazed Donuts with discount def function = ${totalCostWithDiscountFunctionParameter("Glazed Donut")(5)(applyDiscount(_))}")
You should see the following output when you run your Scala application in IntelliJ:

Step 2: How to define and pass a def function to a higher order function
Calculating total cost for 5 Glazed Donut
Total cost of 5 Glazed Donuts with discount def function = 10.5
 
3. How to define and pass a val function to a higher order function
If you've also reviewed the Scala Features Tutorial, you should already be familiar with the fact that functions are first class citizens in Scala.
 
As a result, Scala allows you to define value function using the val keyword as shown below:

println("\nStep 3: How to define and pass a val function to a higher order function")
val applyDiscountValueFunction = (totalCost: Double) => {
  val discount = 2 // assume you fetch discount from database
  totalCost - discount
}
println(s"Total cost of 5 Glazed Donuts with discount val function = ${totalCostWithDiscountFunctionParameter("Glazed Donut")(5)(applyDiscountValueFunction)}")
You should see the following output when you run your Scala application in IntelliJ:

Step 3: How to define and pass a val function to a higher order function
Calculating total cost for 5 Glazed Donut
Total cost of 5 Glazed Donuts with discount val function = 10.5
NOTE:
•	The syntax for defining value function is slightly different to functions defined with def keyword.
•	In val applyDiscountValueFunction = (totalCost: Double) => { ... } we did not specify the return type of the function and are making use of Scala Type Inference.
•	If you want to add the return type, the syntax for the value function would look as follows: val applyDiscountValueFunction: Double => Double = totalCost => { ... }
•	When passing the value function to the Higher Order Function, you no longer need to explicitly make use of the wildcard operator _
This concludes our tutorial on Learn How To Create Function Using The Val Keyword Instead Of Def and I hope you've found it useful!
Scala Tutorial - Learn Function Composition Using AndThen
By Nadim Bahadoor | Last updated: March 16, 2018 at 15:14 pm
Overview
In this tutorial, we will learn how to create value functions which are defined using the valkeyword as opposed to using the def keyword.
 
Val functions inherit the andThen function and we will show how to use the andThen function to compose two functions together.
 
Mathematically speaking, f(x) andThen g(x) = g(f(x)). The results of the first function f(x) is ran first and will be passed as input to the second function g(x).
Steps
1. Assume a pre-calculated total cost amount
Let's start with a simple totalCost value which represents the total cost in dollar figure for a particular customer buying donuts from your store.

println("Step 1: Assume a pre-calculated total cost amount")
val totalCost: Double = 10
 
2. How to define a val function to apply discount to total cost
Similar to the example from the previous tutorial on defining function with val keyword, let's define a val function which will apply some discount dollar value from the total cost figure.

println("\nStep 2: How to define a val function to apply discount to total cost")
val applyDiscountValFunction = (amount: Double) => {
  println("Apply discount function")
  val discount = 2 // fetch discount from database
  amount - discount
}
 
3. How to call a val function
Calling the val function applyDiscountValFunction from Step 2 is very straight-forward. You simply need to pass it the totalCost value from Step 1.

println("\nStep 3: How to call a val function")
println(s"Total cost of 5 donuts with discount = ${applyDiscountValFunction(totalCost)}")
You should see the following output when you run your Scala application in IntelliJ:

Step 3: How to call a val function
Apply discount function
Total cost of 5 donuts with discount = 8.0
 
4. How to define a val function to apply tax to total cost
Let's go ahead and define another val function which should apply some tax amount to the totalCost value.

println("\nStep 4: How to define a val function to apply tax to total cost")
val applyTaxValFunction = (amount: Double) => {
  println("Apply tax function")
  val tax = 1 // fetch tax from database
  amount + tax
}
 
5. How to call andThen on a val function
As we've seen from the previous tutorial on defining function with val keyword, val function inherits an andThen function.
 
Calling andThen will take the result from the first function and pass it as input parameter to the second function. Let's use the andThen semantics to apply discount andThen apply tax to the totalCost figure as shown below.

println("\nStep 5: How to call andThen on a val function")
println(s"Total cost of 5 donuts = ${ (applyDiscountValFunction andThen applyTaxValFunction)(totalCost) }")
You should see the following output when you run your Scala application in IntelliJ:

Step 5: How to call andThen on a val function
Apply discount function
Apply tax function
Total cost of 5 donuts = 9.0
NOTE:
•	The apply discount function was called first andThen the apply tax function was called.
•	The output from the first apply discount function was also passed through as input parameter to the second apply tax function
Scala Tutorial - Learn Function Composition Using Compose
By Nadim Bahadoor | Last updated: March 16, 2018 at 15:14 pm
Overview
In this tutorial, we will learn how to create value functions which are defined using the valkeyword as opposed to using the def keyword.
 
Val functions inherit the compose function and we will show how to use the compose function to compose two functions together.
 
Mathematically speaking, f(x) compose g(x) = f(g(x)). The second function g(x) is ran first and its result is passed along to the function f(x).
 
Note however that the ordering when composing function using the compose method is different to using andThen as shown in the Function Composition Using AndThen Tutorial.
 
Mathematically speaking, f(x) andThen g(x) = g(f(x)). The results of the first function f(x) is ran first and will be passed as input to the second function g(x)
Steps
1. Assume a pre-calculated total cost amount
Let's start with a simple totalCost value which represents the total cost in dollar figure for a particular customer buying donuts from your store.

println("Step 1: Assume a pre-calculated total cost amount")
val totalCost: Double = 10
 
2. How to define a val function to apply discount to total cost
Similar to the example from the previous tutorial on defining function with val keyword, let's define a val function which will apply some discount dollar value from the total cost figure.

println("\nStep 2: How to define a val function to apply discount to total cost")
val applyDiscountValFunction = (amount: Double) => {
  println("Apply discount function")
  val discount = 2 // fetch discount from database
  amount - discount
}
 
3. How to call a val function
Calling the val function applyDiscountValFunction from Step 2 is very straight-forward. You simply need to pass it the totalCost value from Step 1.

println("\nStep 3: How to call a val function")
println(s"Total cost of 5 donuts with discount = ${applyDiscountValFunction(totalCost)}")
You should see the following output when you run your Scala application in IntelliJ:

Step 3: How to call a val function
Apply discount function
Total cost of 5 donuts with discount = 8.0
 
4. How to define a val function to apply tax to total cost
Let's go ahead and define another val function which should apply some tax amount to the totalCost value.

println("\nStep 4: How to define a val function to apply tax to total cost")
val applyTaxValFunction = (amount: Double) => {
  println("Apply tax function")
  val tax = 1 // fetch tax from database
  amount + tax
}
 
5. How to call compose on a val function
As we've seen from the previous tutorial on defining function with val keyword, val function inherits a compose function.
 
Calling compose will take the result from the second function and pass it as input parameter to the first function. Let's use the compose semantics to apply tax first and afterwards apply discount to the totalCost figure as shown below.

println("\nStep 5: How to call compose on a val function")
println(s"Total cost of 5 donuts = ${ (applyDiscountValFunction compose applyTaxValFunction)(totalCost) }")
You should see the following output when you run your Scala application in IntelliJ:

Step 5: How to call compose on a val function
Apply tax function
Apply discount function
Total cost of 5 donuts = 9.0
NOTE:
•	The apply tax function was called first following which the apply discount function was called.
•	The output from the apply tax function was also passed through as input parameter to the apply discount function
•	Although in this example, the result is similar to using andThen as shown in the previous tutorial, bear in mind the difference in ordering between andThen and compose.
•	Ordering using andThen: f(x) andThen g(x) = g(f(x))
•	Ordering using compose: f(x) compose g(x) = f(g(x))
Scala Tutorial - Learn How To Create Tail Recursive Function - @annotation.tailrec
By Nadim Bahadoor | Last updated: March 16, 2018 at 15:14 pm
Overview
In this tutorial, we will learn how to create tail recursive function and also make use of the annotation @annotation.tailrec which will instruct the compiler to apply any further optimisation.
 
Tail recursive function will help prevent overflow in your call stack because the evaluation of your looping construct happens at each step.
 
If this does not make any sense at the moment, don't worry we will see an example below.
Steps
1. How to define an Array of type String
Let's start by defining an Array of type String to hold some donut items.

println("Step 1: How to define an Array of type String")
val arrayDonuts: Array[String] = Array("Vanilla Donut", "Strawberry Donut", "Plain Donut", "Glazed Donut")
 
2. How to define a tail recursive function
Next, let's define a tail recursive function named search() which will have the following input parameters:
•	donutName parameter of type String for the donut item to search within the Array
•	donuts parameter of type String Array for the donut items Array
•	index parameter of type Int for the index within the Array on which to run the search
println("\nStep 2: How to define a tail recursive function")
@annotation.tailrec
def search(donutName: String, donuts: Array[String], index: Int): Option[Boolean] = {
  if(donuts.length == index) {
    None
  } else if(donuts(index) == donutName) {
    Some(true)
  } else {
    val nextIndex = index + 1
    search(donutName, donuts, nextIndex)
  }
}
NOTE:
•	The body of the function could have inlined elegantly but we are showing each step verbosely so that it is more clear what the search function is doing.
•	If you have never seen or written a tail recursive function, you can review each step of the function by debugging through. Follow the Debugging Tutorial if you need help with debugging in IntelliJ.
•	The very first expression if(donuts.length == index) is the exit call for the search function because we have looped through all elements within the Array.
•	The second expression else if(donuts(index) == donutName) will exit the search function as we have found the donut item in the Array.
•	In the third expression shown below

val nextIndex = index + 1
search(donutName, donuts, nextIndex)
we increment the current index by 1 and call the search function itself (this is the recursive bit) but for the next item in the Array.
•	The @annotation.tailrec instructs the compiler to add any optimisations with regards to stack frame management as this function is recursive.
3. How to call a tail recursive function
Calling a tail recursive function is not so different than calling any other function. You simply call the function by its name and pass it the corresponding parameters.

println("\nStep 3: How to call a tail recursive function")
val found = search("Glazed Donut", arrayDonuts, 0)
println(s"Find Glazed Donut = $found")

val notFound = search("Chocolate Donut", arrayDonuts, 0)
println(s"Find Chocolate Donut = $notFound")
You should see the following output when you run your Scala application in IntelliJ:

Step 3: How to call a tail recursive function
Find Glazed Donut = Some(true)
Find Chocolate Donut = None
Scala Tutorial - Learn How To Create Tail Recursive Function - scala.util.control.TailCalls._
By Nadim Bahadoor | Last updated: March 16, 2018 at 15:14 pm
Overview
In this tutorial, we will learn how to create tail recursive function by making use of utilities that Scala provides for tail recursions in the package scala.util.control.TailCalls._
 
As a reminder from the previous tutorial on Tail Recursive Function, tail recursive function will help prevent overflow in your call stack because the evaluation of your looping construct happens at each step.
 
If this does not make any sense at the moment, don't worry we will see an example below.
Steps
1. Review how to define a tail recursive function
In the previous tutorial on Tail Recursive Function, we showed how to define a tail recursive function named search() which would find a donut item of type String in an Array.
 
Moreover, we used the annotation @annotation.tailrec in order to instruct the compiler to perform any compiler optimisation with regards to stack frame management for this recursive function.

println("\nStep 1: Review how to define a tail recursive function")
@annotation.tailrec
def search(donutName: String, donuts: Array[String], index: Int): Option[Boolean] = {
  if(donuts.length == index) {
    None
  } else if(donuts(index) == donutName) {
    Some(true)
  } else {
    val nextIndex = index + 1
    search(donutName, donuts, nextIndex)
  }
}
NOTE:
•	Feel free to review the previous tutorial on Tail Recursive Function for additional details on the recursive search() function above.
2. Review how to call a tail recursive function
Similarly, let's review how to call the tail recursive function. There is no special syntax for calling the recursive search() function and you simply need to call the function by its name and pass along its parameters.

println("\nStep 2: Review how to call a tail recursive function")
val arrayDonuts: Array[String] = Array("Vanilla Donut", "Strawberry Donut", "Plain Donut", "Glazed Donut")
val found = search("Glazed Donut", arrayDonuts, 0)
println(s"Find Glazed Donut = $found")
You should see the following output when you run your Scala application in IntelliJ:

Step 2: Review how to call a tail recursive function
Find Glazed Donut = Some(true)
 
3. How to define a tail recursive function using scala.util.control.TailCalls._
When it comes to recursion, Scala provides additional utilities in the package scala.util.control.TailCalls._ 
 
Let's go ahead and re-write the recursive search() function from Step 1 by making use of these recursive utilities.

println("\nStep 3: How to define a tail recursive function using scala.util.control.TailCalls._")
def tailSearch(donutName: String, donuts: Array[String], index: Int): TailRec[Option[Boolean]] = {
  if(donuts.length == index) {
    done(None) // NOTE: done is imported from scala.util.control.TailCalls._
  } else if(donuts(index) == donutName) {
    done(Some(true))
  } else {
    val nextIndex = index + 1
    tailcall(tailSearch(donutName, donuts, nextIndex)) // NOTE: tailcall is imported from  scala.util.control.TailCalls._
  }
}
NOTE:
•	We changed the returned type of our function to be TailRec[Option[Boolean]]
•	As a result of using TailRec, we also need to make use of done() in the exit expression if(donuts.length == index) and for the case when we found the donut item else if(donuts(index) == donutName)
•	When recursively calling the function itself, you need to wrap the call to the function inside a tailcall() as follows: tailcall(tailSearch(donutName, donuts,nextIndex))
•	Using the utilities provided by scala.util.control.TailCalls._ is perhaps a bit artificial with regards to our search() function. But, it should help you see how to make use of them.
•	These utilities are the stepping stone to writing Trampoline Recursive Function which we will see in the next tutorial.
4. How to call tail recursive function using scala.util.control.TailCalls._
The syntax to call the recursive function from Step 3 is slightly different as you need to wrap the call inside a tailcall() as shown below:

println("\nStep 4: How to call tail recursive function using scala.util.control.TailCalls._")
val tailFound = tailcall(tailSearch("Glazed Donut", arrayDonuts, 0))
println(s"Find Glazed Donut using TailCall = ${tailFound.result}") // NOTE: our returned value is wrapped so we need to get it by calling result

val tailNotFound = tailcall(tailSearch("Chocolate Donut", arrayDonuts, 0))
println(s"Find Chocolate Donut using TailCall = ${tailNotFound.result}")
You should see the following output when you run your Scala application in IntelliJ:

Step 4: How to call tail recursive function using scala.util.control.TailCalls._
Find Glazed Donut using TailCall = Some(true)
Find Chocolate Donut using TailCall = None
This concludes our tutorial on Learn How To Create
Scala Tutorial - Learn How To Create Trampoline Tail Recursive Function Using scala.util.control.TailCalls._
By Nadim Bahadoor | Last updated: March 16, 2018 at 15:14 pm
Overview
In this tutorial, we will learn how to create trampoline tail recursive function by making use of utilities that Scala provides for tail recursions in the package scala.util.control.TailCalls._
 
Say you had two tail recursive functions F(A) and F(B) and that F(A) calls F(B) but in turn F(B) also calls F(A).
 
Then F(A) is said to be a trampoline tail recursive function because the call stack jumps back and forth between the two functions F(A) and F(B) - hence the name trampoline.
 
As a reminder from the previous tutorial on Tail Recursive Function, tail recursive function will help prevent overflow in your call stack because the evaluation of your looping construct happens at each step.
 
This tutorial will also make use of TailRec which we have seen from the previous tutorial on How to Create Tail Recursive Function using scala.util.control.TailCalls.
Steps
1. How to define a trampoline function using scala.util.control.TailCalls
Let's start by creating a tail recursive function verySweetDonut() which will return true if the first item in its donutList parameter is a Vanilla, Strawberry or Glazed Donut.
 
If however a sweet donut is not found, the verySweetDonut() function will call another tail recursive function named notSweetDonut() which we will define in step 2.

println("Step 1: How to define a trampoline function using scala.util.control.TailCalls")
def verySweetDonut(donutList: List[String]): TailRec[Boolean] = {
  println(s"verySweetDonut function: donut list = $donutList")
  if (donutList.isEmpty) {
    println("verySweetDonut function: donut list isEmpty, returning false")
    done(false)
  } else {
    if(Set(donutList.head).subsetOf(Set("Vanilla Donut","Strawberry Donut","Glazed Donut"))) {
      println(s"verySweetDonut function: found donut list's head = ${donutList.head} to be VERY sweet, returning true")
      done(true)
    } else {
      println(s"verySweetDonut function: donut list's head = ${donutList.head} is NOT VERY sweet, forwarding donut list's to notSweetDonut function")
      tailcall(notSweetDonut(donutList))
    }
  }
}
NOTE:
•	verySweetDonut() function is making use of TailRec, done and tailcall utilities from scala.util.control.TailCalls._ which should be familiar to you from the previous tutorial.
•	The important thing to note here is that verySweetDonut() function calls notSweetDonut() function tailcall(notSweetDonut(donutList)) defined in Step 2 below.
2. How to define a trampoline function using scala.util.control.TailCalls
To keep the example simple, we'll assume that the notSweetDonut() function below will log the first donut from its donutList parameter

println(s"notSweetDonut function: donut list's head = ${donutList.head} is NOT sweet, forwarding donut list's tail to verySweetDonut function")
 
It will then pass back the tail of the donut list to the verySweetDonut() function tailcall(verySweetDonut(donutList.tail))
 
But if you recall from Step 1 above, the function verySweetDonut() will check the head of the donut list and if it does not find a sweet donut, it will call back the notSweetDonut() function.
 
This jumping back and forth between verySweetDonut() and notSweetDonut() functions is the trampoline effect.

println("\nStep 2: How to define a trampoline function using scala.util.control.TailCalls")
def notSweetDonut(donutList: List[String]): TailRec[Boolean] = {
  println(s"notSweetDonut function: with donut list = $donutList")
  if (donutList.isEmpty) {
    println("notSweetDonut function: donut list isEmpty, returning false")
    done(false)
  } else {
    println(s"notSweetDonut function: donut list's head = ${donutList.head} is NOT sweet,   forwarding donut list's tail to verySweetDonut function")
    tailcall(verySweetDonut(donutList.tail))
  }
}
 
3. How to call a trampoline tail recursive function
Simply make use of tailcall() function from scala.util.control.TailCalls._ and pass it the verySweetDonut() function which takes a List of donuts of type String.

println("\nStep 3: How to call a trampoline tail recursive function")
val donutList: List[String] = List("Plain Donut", "Strawberry Donut", "Plain Donut", "Glazed Donut")
val foundVerySweetDonut = tailcall(verySweetDonut(donutList)).result
println(s"Found very sweet donut = $foundVerySweetDonut")
You should see the following output when you run your Scala application in IntelliJ:

Step 3: How to call a trampoline tail recursive function
verySweetDonut function: donut list = List(Plain Donut, Strawberry Donut, Plain Donut, Glazed Donut)
verySweetDonut function: donut list's head = Plain Donut is NOT VERY sweet, forwarding donut list's to notSweetDonut function
notSweetDonut function: with donut list = List(Plain Donut, Strawberry Donut, Plain Donut, Glazed Donut)
notSweetDonut function: donut list's head = Plain Donut is NOT sweet, forwarding donut list's tail to verySweetDonut function
verySweetDonut function: donut list = List(Strawberry Donut, Plain Donut, Glazed Donut)
verySweetDonut function: found donut list's head = Strawberry Donut to be VERY sweet, returning true
Found very sweet donut = true
NOTE:
•	Notice how the function call is jumping between verySweetDonut() and notSweetDonut() functions.
Scala Tutorial - Learn How To Create Partial Function Using the PartialFunction Trait
By Nadim Bahadoor | Last updated: March 16, 2018 at 15:14 pm
Overview
In this tutorial, we will learn how to create Partial Function using the PartialFunction trait.
 
With pattern matching, if you recall from the Pattern Matching tutorial, you provide a series of case blocks. However, a Partial Function provides some but not all the possible case blocks.
 
If none of these make any sense, don't worry :) let's proceed with the examples below.
Steps
1. Review of Pattern Matching in Scala
First let's review Pattern Matching in Scala which you should already be familiar with from the Pattern Matching tutorial.
 
In the example below, you create a donut of type String with value Glazed Donut and then uses pattern matching to provide the cases for the different taste level.

println("Step 1: Review of Pattern Matching in Scala")
val donut = "Glazed Donut"
val tasteLevel = donut match {
  case "Glazed Donut" | "Strawberry Donut" => "Very tasty"
  case "Plain Donut" => "Tasty"
  case _ => "Tasty"
}
println(s"Taste level of $donut = $tasteLevel")
You should see the following output when you run your Scala application in IntelliJ:

Step 1: Review of Pattern Matching in Scala
Taste level of Glazed Donut = Very tasty
 
2. How to define a Partial Function named isVeryTasty
Instead of doing a full pattern match for the different taste level of a given donut, let's create a partial function named isVeryTasty which will only provide the case for very tasty donuts.

println("\nStep 2: How to define a Partial Function named isVeryTasty")
val isVeryTasty: PartialFunction[String, String] = {
  case "Glazed Donut" | "Strawberry Donut" => "Very Tasty"
}
NOTE:
•	Note that we are using the PartialFunction trait
•	In this example isVeryTasty takes an input of type String which is the donut and produces a String for the taste level. This is specified by PartialFunction[String, String]
3. How to call the Partial Function named isVeryTasty
Calling the partial function isVeryTasty from step 2 is no different than calling any other function - you simply need to pass its required parameter.

println("\nStep 3: How to call the Partial Function named isVeryTasty")
println(s"Calling partial function isVeryTasty = ${isVeryTasty("Glazed Donut")}")
You should see the following output when you run your Scala application in IntelliJ:

Step 3: How to call the Partial Function named isVeryTasty
Calling partial function isVeryTasty = Very Tasty
NOTE:
•	You will get scala.MatchError if the partial function does not have a case which matches the provided input.
4. How to define PartialFunction named isTasty and unknownTaste
Now that you know how to define partial functions as shown in Step 2 above, let's define two additional partial functions namely isTasty and unknownTaste.

println("\nStep 4: How to define PartialFunction named isTasty and unknownTaste")
val isTasty: PartialFunction[String, String] = {
  case "Plain Donut" => "Tasty"
}

val unknownTaste: PartialFunction[String, String] = {
  case donut @ _ => s"Unknown taste for donut = $donut"
}
 
5. How to compose PartialFunction using orElse
Functions in Scala are first class citizens and as such you can compose them. Let's go ahead and use the orElse() function which is inherited from the PartialFunction trait and create another PartialFunction named donutTaste.

println("\nStep 5: How to compose PartialFunction using orElse")
val donutTaste = isVeryTasty orElse isTasty orElse unknownTaste
println(donutTaste("Glazed Donut"))
println(donutTaste("Plain Donut"))
println(donutTaste("Chocolate Donut"))
You should see the following output when you run your Scala application in IntelliJ:

Step 5: How to compose PartialFunction using orElse
Very Tasty
Tasty
Unknown taste for donut = Chocolate Donut
This concludes our tutorial on Learn How To Create Partial Function Using the PartialFunction Trait and I hope you've found it useful!
Scala Tutorial - Learn How To Create Nested Function
By Nadim Bahadoor | Last updated: March 16, 2018 at 15:14 pm
Overview
In this tutorial, we will learn how to create Nested Functions which as the name implies are functions that are defined inside other functions.
 
In Functional Programming, you should try to break your logic into other smaller functions. But sometimes you have logic that is tightly coupled with a particular function and Scala provides you with the ability to nest functions so that you can still benefit from functional style of coding.
Steps
1. How to define a function
If you have followed the tutorials from this Chapter On Functions, you should by now be familiar with defining a function.
 
So let's go ahead and write a function named checkDonutAvailability() which will check if a donut is available from your inventory.
 
But, this function will also perform some validation on the input parameter donutName.

println("Step 1: How to define a function")
def checkDonutAvailability(donutName: String): Boolean = {
  // retrieve donut list that is currently in stock
  val listDonutsFromStock: List[String] = List("Vanilla Donut", "Strawberry Donut", "Plain Donut", "Glazed Donut")

  val iDonutInStock = (donutName.nonEmpty && donutName.length > 0) && (listDonutsFromStock contains donutName)

  iDonutInStock
}
NOTE:
•	Sure we could have inlined the body of this function but we are showing each individual step so you can easily compare with the nested function equivalent later on.
2. How to call a function
Once again, calling a function which has an input parameter should be straight-forward as shown below.

println("\nStep 2: How to call a function")
println(s"Calling checkDonutAvailability with Vanilla Donut = ${checkDonutAvailability("Vanilla Donut")}")
You should see the following output when you run your Scala application in IntelliJ:

Step 2: How to call a function
Calling checkDonutAvailability with Vanilla Donut = true
 
3. How to define a Nested Function
If you look closely at the function defined in step 1, you could easily encapsulate the validation logic into a separate function.
 
For the sake of this example, let's assume that the validation logic is tightly coupled with the function itself and should not be visible by any other functions. As a result, we can use a Nested Function as shown below.

println("\nStep 3: How to define a Nested Function")
def checkDonutAvailabilityWithNestedFunction(donutName: String): Boolean = {
  // retrieve donut list that is currently in stock
  val listDonutsFromStock = List[String]("Vanilla Donut", "Strawberry Donut", "Plain Donut", "Glazed Donut")

  // validate the donutName parameter by some business logic
  val validate = (name: String) => {
    name.nonEmpty && name.length > 0
  }

  // first run validate and then check if we have a matching donut from our list
  val isDonutInStock = validate(donutName) && (listDonutsFromStock contains donutName)

  isDonutInStock
}
NOTE:
•	We've defined a value function named validate() which should be familiar from the Function Stored As Values Tutorial.
•	As a result, the body of the function becomes less cluttered and more clear to read.
4. How to call a Nested Function
The nested function named validate() from Step 3 should never be visible by anyone else. Hence, calling a function which has nested function in its body is inherently the same as calling any other function.

println("\nStep 4: How to call a Nested Function")
println(s"Calling checkDonutAvailabilityWithNestedFunction with Vanilla Donut = ${checkDonutAvailabilityWithNestedFunction("Vanilla Donut")}")
You should see the following output when you run your Scala application in IntelliJ:

Step 4: How to call a Nested Function
Calling checkDonutAvailabilityWithNestedFunction with Vanilla Donut = true
This concludes our tutorial on Learn
Scala Tutorial - Learn How To Create Classes And Objects In Scala
By Nadim Bahadoor | Last updated: March 16, 2018 at 15:14 pm
Overview
In this tutorial, we will learn how to create classes with input parameters and functions. In turn, we will show how to instantiate these classes into objects.
Steps
1. How to define a simple class to represent a Donut object
Let's start with defining a simple class which will represent a Donut object with name and productCode properties.
 
In addition, we will also have a print() function which will print the name and productCode for a given donut object. If you are not familiar with creating functions in Scala, you can refer back to the Functions Tutorials.

// "Step 1: How to define a simple class to represent a Donut object")
class Donut(name: String, productCode: Long) {

 def print = println(s"Donut name = $name, productCode = $productCode")

}
 
 
2. How to create instances of Donut class
If you have used another programming language like Java or .NET in the past, you should be familiar with using the new keyword to create an instance of a class - that is create a new Object of type Donut.

println("\nStep 2: How to create instances of Donut class")
val glazedDonut = new Donut("Glazed Donut", 1111)
val vanillaDonut = new Donut("Vanilla Donut", 2222)
 
 
3. How to call the print function for each of the donut object
Next, let's call the print() function from our donut objects as shown below.

println("\nStep 3: How to call the print function for each of the donut object")
glazedDonut.print
vanillaDonut.print
You should see the following output when you run your Scala application in IntelliJ:

Step 3: How to call the print function for each of the donut object
Donut name = Glazed Donut, productCode = 1111
Donut name = Vanilla Donut, productCode = 2222
 
4. How to access the properties of class Donut
What if you needed to access the name or productCode properties on the donut objects?

println("\nStep 4: How to access the properties of class Donut")
glazedDonut.name
glazedDonut.productCode
NOTE:
Scala Tutorial - Learn How To Create And Use Companion Objects
By Nadim Bahadoor | Last updated: March 16, 2018 at 15:14 pm
Overview
In this tutorial, we will learn how to create Companion Object for a given class. In turn, you will use the companion object to create instances for that particular class without having to make use of the new keyword.
Steps
1. How to define a simple class to represent a Donut object
Let's start with defining a simple class which will represent a Donut object with name and productCode properties. This example is a review from the previous tutorial on How To Create Classes And Objects In Scala.
 
Similar to the previous tutorial, let's also have a print() function which will print the name and productCode for a given donut object. If you are not familiar with creating functions in Scala, you can refer back to the Functions Tutorials.

println("Step 1: How to define a simple class to represent a Donut object")
class Donut(name: String, productCode: Long){

  def print = println(s"Donut name = $name, productCode = $productCode")

}
 
2. How to declare a companion object for the Donut class
A Companion Object is defined using the object keyword and the name of the object should be identical to the class name.
 
In addition, the companion object should define an apply() method which will be responsible for instantiating an instance of the given class.
 
Since the Donut class from Step 1 requires name and productCode properties, we are also providing similar input parameters to the apply() method as shown below.

println("\nStep 2: How to declare a companion object for the Donut class")
object Donut {

 def apply(name: String, productCode: Long): Donut = {
   new Donut(name, productCode)
 }

}
 
3. How to create instances of the Donut class using the companion object
With the companion object defined in Step 2 above, you can now create instances of the Donut class without having to use the new keyword.
 

println("\nStep 3: How to create instances of the Donut class using the companion object")
val glazedDonut = Donut("Glazed Donut", 1111)
val vanillaDonut = Donut("Vanilla Donut", 2222)
NOTE:
•	Sure you could argue that the companion object is not really adding any special value other than not having to use the new keyword.
•	However, in the next tutorial, I will show you how the apply() method of the companion object can be used as a factory for your class.
4. How to call the print function for each of the donut object
Next, let's call the print() function from our donut objects as shown below.

println("\nStep 4: How to call function on each Donut object")
glazedDonut.print
vanillaDonut.print
You should see the following output when you run your Scala application in IntelliJ:

Step 4: How to call the print function for each of the Donut object
Donut name = Glazed Donut, productCode = 1111
Donut name = Vanilla Donut, productCode = 2222
This concludes our tutorial on Learn How To Create And Use Companion Object and I hope you've found it useful!
Scala Tutorial - Learn How To Create And Use Companion Objects
By Nadim Bahadoor | Last updated: March 16, 2018 at 15:14 pm
Overview
In this tutorial, we will learn how to create Companion Object for a given class. In turn, you will use the companion object to create instances for that particular class without having to make use of the new keyword.
Steps
1. How to define a simple class to represent a Donut object
Let's start with defining a simple class which will represent a Donut object with name and productCode properties. This example is a review from the previous tutorial on How To Create Classes And Objects In Scala.
 
Similar to the previous tutorial, let's also have a print() function which will print the name and productCode for a given donut object. If you are not familiar with creating functions in Scala, you can refer back to the Functions Tutorials.

println("Step 1: How to define a simple class to represent a Donut object")
class Donut(name: String, productCode: Long){

  def print = println(s"Donut name = $name, productCode = $productCode")

}
 
2. How to declare a companion object for the Donut class
A Companion Object is defined using the object keyword and the name of the object should be identical to the class name.
 
In addition, the companion object should define an apply() method which will be responsible for instantiating an instance of the given class.
 
Since the Donut class from Step 1 requires name and productCode properties, we are also providing similar input parameters to the apply() method as shown below.

println("\nStep 2: How to declare a companion object for the Donut class")
object Donut {

 def apply(name: String, productCode: Long): Donut = {
   new Donut(name, productCode)
 }

}
 
3. How to create instances of the Donut class using the companion object
With the companion object defined in Step 2 above, you can now create instances of the Donut class without having to use the new keyword.
 

println("\nStep 3: How to create instances of the Donut class using the companion object")
val glazedDonut = Donut("Glazed Donut", 1111)
val vanillaDonut = Donut("Vanilla Donut", 2222)
NOTE:
•	Sure you could argue that the companion object is not really adding any special value other than not having to use the new keyword.
•	However, in the next tutorial, I will show you how the apply() method of the companion object can be used as a factory for your class.
4. How to call the print function for each of the donut object
Next, let's call the print() function from our donut objects as shown below.

println("\nStep 4: How to call function on each Donut object")
glazedDonut.print
vanillaDonut.print
You should see the following output when you run your Scala application in IntelliJ:

Step 4: How to call the print function for each of the Donut object
Donut name = Glazed Donut, productCode = 1111
Donut name = Vanilla Donut, productCode = 2222
This concludes our tutorial on Learn How To Create And Use Companion Object and I hope you've found it useful!
Scala Tutorial - Learn How To Declare Values And Fields In Companion Object
By Nadim Bahadoor | Last updated: March 16, 2018 at 15:14 pm
Overview
In this tutorial, we will learn how to declare values and fields in Companion Object which will be accessed only by the class of the Companion Object.
 
This tutorial builds on what you have learned from the previous tutorials on Learn How To Create And Use Companion Objects and Learn How To Use Companion Objects' Apply Method As A Factory (Class Hierarchy Via Inheritance)
Steps
1. How to define a simple class to represent a Donut object
If you have followed the two previous tutorials on Companion Objects as listed above, you should be familiar with the Donut class below which has a print() method.
 

println("Step 1: How to define a simple class to represent a Donut object")
class Donut(name: String, productCode: Option[Long] = None){

def print = println(s"Donut name = $name, productCode = ${productCode.getOrElse(0)}, uuid = ${Donut.uuid}")

}
NOTE:
•	But within the print statement above, we also print a unique ID for each donut as represented by the uuid field: uuid = ${Donut.uuid}
•	But where does the uuid field come from? Let's proceed to Step 2 below which shows the Donut Companion Object.
2. How to declare fields and values in Companion Object
Notice that within the Donut Companion Object, we've defined a value named uuid but also marked it as private.
 
If you have used another programming language such as Java or .NET in the past, it should be of no surprise that the private keyword would hide the visibility of the field uuid.
 
But, given that a Companion Object works along side the class to which the Companion Object refers to, even though the uuid field is not visible to the outside world, it is still accessible within the Donut class as shown in Step 2.

println("\nStep 2: How to declare fields and values in companion object")
object Donut {

 private val uuid = 1

 def apply(name: String, productCode: Option[Long]): Donut = {
  new Donut(name, productCode)
 }

 def apply(name: String): Donut = {
  new Donut(name)
 }
}
 
3. How to create instances of the Donut class using the Companion Object
Next let's create a couple of instances of Donut class using the Donut's Companion Object apply() method similar to what you've learned from the tutorial on Learn How To Create And Use Companion Objects.

println("\nStep 3: How to create instances of the Donut class using the companion object")
val glazedDonut = Donut("Glazed Donut", Some(1111))
val vanillaDonut = Donut("Vanilla Donut")
 
4. How to call function on each Donut object
When you call the print() method on each of the Donut instances, you will notice that the uuid value is also being printed in the console window.

println("\nStep 4: How to call function on each Donut object")
glazedDonut.print
vanillaDonut.print
You should see the following output when you run your Scala application in IntelliJ:

Step 4: How to call function on each Donut object
Donut name = Glazed Donut, productCode = 1111, uuid = 1
Donut name = Vanilla Donut, productCode = 0, uuid = 1
This concludes our tutorial on Learn How To Declare Values And Fields In Companion Object and I hope you've found it useful!
Scala Tutorial - Learn How To Declare And Use Singleton Object
By Nadim Bahadoor | Last updated: March 16, 2018 at 15:14 pm
Overview
In this tutorial, we will learn how to declare Singleton Object which you can use to store global fields and utility functions or methods.
 
What is a Singleton Object?
As per Wikipedia, the Singleton Pattern is a a fairly common design pattern when you need exactly one instance of an object.
 
The Singleton Pattern is so commonly used that Scala has made it very easy to create single instances of an object. All you need to do is to make use of the keyword object as we will show in the steps below.
Steps
1. How to declare a Singleton Object
In the previous tutorials, we've actually made use of Singleton Objects without even mentioning it! So as a reminder, to create Singleton Objects in Scala, you need to make use of the keyword object as shown below.

println("Step 1: How to declare a Singleton Object")
object DonutShoppingCartCalculator {

}
2. How to define a global field
If you have used another programming language such as Java or .NET, you would perhaps expect that Scala also has the keyword static which would allow you to declare global fields and constants.
 
But, Scala does not have a static keyword! Instead, you can simply encapsulate a global field using the val keyword inside a Singleton Object.

println("Step 1: How to declare a Singleton Object")
object DonutShoppingCartCalculator {

 println("\nStep 2: How to define a global field")
 val discount: Double = 0.01
}
NOTE:
•	Perhaps in a real application, you would not hard-code a discount value. But, we're just showing here how to expose a discount field globally.
3. How to define utility function called calculateTotalCost
Once again as mentioned in Step 2 above, Scala does not exposed a static keyword. But you can encapsulate functions and methods inside a Singleton Object if you would like to expose some globally accessible utility function or method.

println("Step 1: How to declare a Singleton Object")
object DonutShoppingCartCalculator {

 println("\nStep 2: How to define a global field")
 val discount: Double = 0.01

 println("\nStep 3: How to define utility function called calculateTotalCost")
 def calculateTotalCost(donuts: List[String]): Double = {
  // calculate the cost of donuts
  return 1
 }
}
NOTE:
•	In a real application, the calculateTotalCost() function would have other parameters required to calculate the total cost of donuts in a shopping cart.
•	You can always review the tutorials on functions if you are unclear about how to create and use functions in Scala.
4. How to call global discount field from Step 2
To access a global field, you simply call the Singleton Object with the dot operator and followed by the global field.

println("\nStep 4: How to call global discount field from Step 2")
println(s"Global discount = ${DonutShoppingCartCalculator.discount}")
You should see the following output when you run your Scala application in IntelliJ:

Step 4: How to call global discount field from Step 2
Global discount = 0.01
 
5. How to call the utility function calculateTotalCost from Step 3
To access a global utility function or method, you simply call the Singleton Object with the dot operator and followed by the utility function or method.

println("\nStep 5: How to call the utility function calculateTotalCost from Step 3")
println(s"Call to calculateTotalCost function = ${DonutShoppingCartCalculator.calculateTotalCost(List())}")
You should see the following output when you run your Scala application in IntelliJ:

Step 5: How to call the utility function calculateTotalCost from Step 3
Call to calculateTotalCost function = 1.0
This concludes ou
Scala Tutorial - Learn How To Define And Use Case Class
By Nadim Bahadoor | Last updated: March 16, 2018 at 15:14 pm
Overview
In this tutorial, we will learn how to define case class and use it to create instances of objects.
 
What is a case class?
A case class is similar to any other classes except that it also creates the Companion Object. In addition, a case class will automatically create the apply(),  toString(), hashCode and equals() methods for you.
Steps
1. How to define a case class to represent a Donut object
Defining a case class is similar to defining a simple class as we've discussed in the Learn How To Create Class And Objects Tutorial. However, you also make use of the case keyword as part of the class definition.

println("Step 1: How to define a case class to represent a Donut object")
case class Donut(name: String, price: Double, productCode: Option[Long] = None)
2. How to create instances or objects for the Donut case class
Use the following syntax to create instances or objects of the Donut case class.

println("\nStep 2: How to create instances or objects for the Donut case class")
val vanillaDonut: Donut = Donut("Vanilla Donut", 1.50)
val glazedDonut: Donut = Donut("Glazed Donut", 2.0)
println(s"Vanilla Donut = $vanillaDonut")
println(s"Glazed Donut = $glazedDonut")
You should see the following output when you run your Scala application in IntelliJ:

Step 2: How to create instances or objects for the Donut case class
Vanilla Donut = Donut(Vanilla Donut,1.5,None)
Glazed Donut = Donut(Glazed Donut,2.0,None)
NOTE:
•	You did not have to use the new keyword when creating instances of the Donut case class.
•	The case class will automatically create the Companion Object.
3. How to access fields of the Donut object
When using a case class, you do not have to write any boiler plate accessor code to be able to access the fields on objects created from a case class.

println("\nStep 3: How to access fields of the Donut object")
println(s"Vanilla Donut name field = ${vanillaDonut.name}")
println(s"Vanilla Donut price field = ${vanillaDonut.price}")
println(s"Vanilla Donut productCode field = ${vanillaDonut.productCode}")
You should see the following output when you run your Scala application in IntelliJ:

Step 3: How to access fields of the Donut object
Vanilla Donut name field = Vanilla Donut
Vanilla Donut price field = 1.5
Vanilla Donut productCode field = None
4. How to modify or update fields of the Donut object
As you have learned from the Scala Programming Features tutorial, Scala favours the use of immutability. As a results, fields defined on case class are immutable by default and as such you cannot modify them.

println("\nStep 4: How to modify or update fields of the Donut object")
// vanillaDonut.name = "vanilla donut" // compiler error. fields are immutable by default.

5. How to define the hashCode and equals method for Donut object
As mentioned earlier, when you use a case class, the Scala compiler automatically creates the hashCode and equals() methods for you.
 
As an example, let's create a Map to represent the type and quantity of donuts being bought by our customers. If you do not implement the hashCode method, adding and retrieving elements from the Map will give you unpredictable behaviour.
 
However, since we are using the case class to represent the Donut objects, the hashCodemethod is implemented for us!

println("\nStep 5: How to define the hashCode and equals method for Donut object")
val shoppingCart: Map[Donut, Int] = Map(vanillaDonut -> 4, glazedDonut -> 3)
println(s"All items in shopping cart = ${shoppingCart}")
println(s"Quantity of vanilla donuts in shopping cart = ${shoppingCart(vanillaDonut)}")
println(s"Quantity of glazed donuts in shopping cart = ${shoppingCart(glazedDonut)}")
You should see the following output when you run your Scala application in IntelliJ:

Step 5: How to define the hashCode and equals method for Donut object
All items in shopping cart = Map(Donut(Vanilla Donut,1.5,None) -> 4, Donut(Glazed Donut,2.0,None) -> 3)
Quantity of vanilla donuts in shopping cart = 4
Quantity of glazed donuts in shopping cart = 3
This concludes our tutorial on Learn How To Define And Use Case Class and I hope you've found it useful!
Scala Tutorial - Learn How To Use Type Alias: Type Aliasing Versus Case Class
By Nadim Bahadoor | Last updated: March 16, 2018 at 15:14 pm
Overview
In this tutorial, we will learn how to define and use type aliasing to create shortcuts to other types or functions.
 
Type aliasing can be useful to help you provide more meaningful names which represent your business or domain objects without having to create unnecessary types.
 
Steps
1. How to define a case class to represent a Donut object
Let's start by using a case class which we learned from the tutorial on case classes to represent a domain object of type Donut.

println("Step 1: How to define a case class to represent a Donut object")
case class Donut(name: String, price: Double, productCode: Option[Long] = None)
 
2. How to create instances or objects for the Donut case class
Use the following syntax to create instances or objects of the Donut case class.

println("\nStep 2: How to create instances or objects for the Donut case class")
val vanillaDonut: Donut = Donut("Vanilla", 1.50)
val glazedDonut: Donut = Donut("Glazed", 2.0)
println(s"Vanilla Donut = $vanillaDonut")
println(s"Glazed Donut = $glazedDonut")
You should see the following output when you run your Scala application in IntelliJ:

Step 2: How to create instances or objects for the Donut case class
Vanilla Donut = Donut(Vanilla,1.5,None)
Glazed Donut = Donut(Glazed,2.0,None)
 
3. How to use type alias to name a Tuple2 pair into a domain type called CartItem
Instead of using a Tuple2 type to represent a Donut with its corresponding quantity being bought by a customer, you can make use of type aliasing to alias the Tuple2 type.
 
As shown below, we are aliasing the Tuple2 type and giving it a more meaningful name of CartItem which is essentially a pair of Donut item with the quantity being bought.


println("\nStep 3: How to use type alias to name a Tuple2 pair into a domain type called CartItem")
type CartItem[Donut, Int] = Tuple2[Donut, Int]
 
4. How to create instances of the aliased typed CartItem
To create instances of the aliased CartItem type from Step 3 above, you simply need to make use of the new keyword.

println("\nStep 4: How to create instances of the aliased typed CartItem")
val cartItem = new CartItem(vanillaDonut, 4)
println(s"cartItem = $cartItem")
println(s"cartItem first value = ${cartItem._1}")
println(s"cartItem second value = ${cartItem._2}")

You should see the following output when you run your Scala application in IntelliJ:

Step 4: How to create instances of the aliased typed CartItem
cartItem = (Donut(Vanilla,1.5,None),4)
cartItem first value = Donut(Vanilla,1.5,None)
cartItem second value = 4

5. How to use an aliased typed into a function parameter
With the type alias CartItem from Step 3, creating a function to calculate the total cost of donut items in a shopping cart is more clear.
 
As an example, the function calculateTotal below has a function parameter which is a Sequence of type CartItem, where aliased Tuple2 type named CartItem expects a Donut and quantity pair.

println("\nStep 5: How to use an aliased typed into a function parameter")
def calculateTotal(shoppingCartItems: Seq[CartItem[Donut, Int]]): Double = {
  // calculate the total cost
  shoppingCartItems.foreach { cartItem =>
    println(s"CartItem donut = ${cartItem._1}, quantity = ${cartItem._2}")
  }
  10 // some random total cost
}
 
6. How to use a case class instead of an aliased typed
If however you need to be even more precise about your shopping cart items, you might as well create another case class instead of using type aliasing of Tuple2.

println("\nStep 6: How to use a case class instead of an aliased typed")
case class ShoppingCartItem(donut: Donut, quantity: Int)

val shoppingItem: ShoppingCartItem = ShoppingCartItem(Donut("Glazed Donut", 2.50), 10)
println(s"shoppingItem donut = ${shoppingItem.donut}")
println(s"shoppingItem quantity = ${shoppingItem.quantity}")

You should see the following output when you run your Scala application in IntelliJ:

Step 6: How to use a case class instead of an aliased typed
shoppingItem donut = Donut(Glazed Donut,2.5,None)
shoppingItem quantity = 10
 
7. How to use case class from Step 6 to represent a Sequence of Donut items in a shopping cart
Using the ShoppingCartItem case class from Step 6 is even more succinct that ShoppingCartItem holds a donut object and the quantity being bought.

println("\nStep 7: How to use case class from Step 6 to represent a Sequence of Donut items in a shopping cart")
def calculateTotal2(shoppingCartItems: Seq[ShoppingCartItem]): Double = {
 // calculate the total cost
 shoppingCartItems.foreach { shoppingCartItem =>
   println(s"ShoppingCartItem donut = ${shoppingCartItem.donut}, quantity = ${shoppingCartItem.quantity}")
 }
 10 // some random total cost
}
This concludes our t
Scala Tutorial - Learn How To Use Implicit Class - Extension Methods
By Nadim Bahadoor | Last updated: March 16, 2018 at 15:14 pm
Overview
In this tutorial, we will learn how use Implicit Class to add methods to an object without modifying the source code of the object - also commonly known as extension methods.
 
Using Implicit Class to extend functionality of an object can be quite handy especially when you do have have access to modify the source object.
 
Steps
1. How to define a case class to represent a Donut object
Let's start by using a case class which we learned from the tutorial on case classes to represent a domain object of type Donut.

println("Step 1: How to define a case class to represent a Donut object")
case class Donut(name: String, price: Double, productCode: Option[Long] = None)
 
2. How to create instances or objects for the Donut case class
Use the following syntax to create instances or objects of the Donut case class.

println("\nStep 2: How to create instances or objects for the Donut case class")
val vanillaDonut: Donut = Donut("Vanilla", 1.50)
println(s"Vanilla donut name = ${vanillaDonut.name}")
println(s"Vanilla donut price = ${vanillaDonut.price}")
println(s"Vanilla donut produceCode = ${vanillaDonut.productCode}")
You should see the following output when you run your Scala application in IntelliJ:

Step 2: How to create instances or objects for the Donut case class
Vanilla donut name = Vanilla
Vanilla donut price = 1.5
Vanilla donut produceCode = None
 
3. How to define an implicit class to augment or extend the Donut object with a uuid field
Assume that you were given a Donut type in a library or dependency and as such do not have access to modify the Donut source code. In addition, say you are given a requirement to create a unique identifier for the Donut type.
 
With Implicit Class, you can easily extend the functionality of the Donut type. In the example below, we add a new method named uuid which returns a String and it uses the name and productCode of the Donut type to construct the unique id.


println("\nStep 3: How to define an implicit class to augment or extend the Donut object with a uuid field")
object DonutImplicits {
 implicit class AugmentedDonut(donut: Donut) {
  def uuid: String = s"${donut.name} - ${donut.productCode.getOrElse(12345)}"
 }
}
NOTE:
•	It's a good practice to encapsulate Implicit Classes into an object which can later be injected or referenced.
•	In real life you probably would not hardcode the uuid value using donut.productCode.getOrElse(12345) but this is just an example of how to add a default value if the productCode field is None.
•	For additional details on how to use Option, None and Some, you can review the tutorial on Learn How To Use Option And Avoid Null.
4. How to import and use the implicit class AugmentedDonut from Step 3
Since we've wrapped and encapsulated the AugmentedDonut Implicit Class inside the DonutImplicits object, to use the Implicit AugmentedDonut class you simply need to import it as shown below.

println("\nStep 4: How to import and use the implicit class AugmentedDonut from Step 3")
import DonutImplicits._
println(s"Vanilla donut uuid = ${vanillaDonut.uuid}")

You should see the following output when you run your Scala application in IntelliJ:

Step 4: How to import and use the implicit class AugmentedDonut from Step 3
Vanilla donut uuid = Vanilla - 12345

NOTE:
Scala Tutorial - Learn How To Use Package Object
By Nadim Bahadoor | Last updated: March 16, 2018 at 15:14 pm
Overview
In this tutorial, we will learn how use Package Objects to store and encapsulate common Objects and Implicit conversions.
 
Objects and Implicit conversions declared inside Package Objects, as the name implies, will be accessible to any classes or traits in the given package. In addition, Package Objectsmake it easy to inject these Objects and Implicit conversions into other scopes within your application.
 
Steps
1. How to add JodaTime dependency in build.sbt"
In the Tutorial on Importing Dependencies Using build.sbt, we showed how you can update the libraryDependencies settings key in your build.sbt file so that you can easily import other 3rd party libraries.
 
In this tutorial, we will import the popular JodaTime library so that we can later alias a new type called DateTime to refer to JodaTime as opposed to default Scala DateTime.

println("\nStep 1: How to add JodaTime dependency in build.sbt")
libraryDependencies ++= Seq(
 "joda-time" % "joda-time" % "2.9.3",
 "org.joda" % "joda-convert" % "1.8"
)
 
2. How to define a case class to represent a Donut object in a package object
Before we can declare a case class inside a Package Object you must first create it! In IntelliJ's Project window, right click on a given package which in our case is the package named four and select New-> Package Object.

package object four {

 println("Step 2: How to define a case class to represent a Donut object in a package object")
 case class Donut(name: String, price: Double, productCode: Option[Long] = None)

}
 
3. How to define an implicit class to augment or extend the Donut object with a uuid field
Next let's declare an Implicit class to extend the functionality of the Donut type which will add an additional uuid method to donut objects.
 
Obviously since we have access to the Donut case class as per Step 2, we could have easily added a uuid method. But we are simply re-using the example from the tutorial on Implicit Classes,


println("\nStep 3: How to define an implicit class to augment or extend the Donut object with a uuid field")
implicit class AugmentedDonut(donut: Donut) {
 def uuid: String = s"${donut.name} - ${donut.productCode.getOrElse(12345)}"
}
 
4. How to alias JodaTime to a DateTime type
Storing type aliases inside Package Objects is typically a good idea because the type alias will be available package wide. To this end, we can create a DateTime type alias which will refer to the JodaTime we imported from Step 1.

println("\nStep 4: How to alias JodaTime to a DateTime type")
type DateTime = org.joda.time.DateTime

 
5. How to create instances or objects for the Donut case class from package object
With our Package Object created, we can now create a new Scala Application named PackageObject_Tutorial and instantiate a Donut object without having to add any import statements.

object PackageObject_Tutorial extends App {

println("\nStep 5: How to create instances or objects for the Donut case class from package object")
val vanillaDonut: Donut = Donut("Vanilla", 1.50)
println(s"Vanilla donut name = ${vanillaDonut.name}")
println(s"Vanilla donut price = ${vanillaDonut.price}")
println(s"Vanilla donut produceCode = ${vanillaDonut.productCode}")
println(s"Vanilla donut uuid = ${vanillaDonut.uuid}")

You should see the following output when you run your Scala application in IntelliJ:

Step 5: How to create instances or objects for the Donut case class from package object
Vanilla donut name = Vanilla
Vanilla donut price = 1.5
Vanilla donut produceCode = None
Vanilla donut uuid = Vanilla - 12345
NOTE:
•	The Donut type also had access to the Implicit Class which added the uuid method.
6. How to create new JodaTime instance using DateTime alias from package object
We can also create a new DateTime as shown below but keep in mind that DateTime is a type alias to JodaTime.

println("\nStep 6: How to create new JodaTime instance using DateTime alias from package object")
val today = new DateTime()
println(s"today = $today, datetime class = ${today.getClass}")

You should see the following output when you run your Scala application in IntelliJ:

Step 6: How to create new JodaTime instance using DateTime alias from package object
today = 2016-10-17T21:08:57.168+01:00, datetime class = class org.joda.time.DateTime
 
This concludes our tutorial on Learn How To Use Package Object and I hope you've found it useful!
Scala Tutorial - Learn How To Extend Class - Class Inheritance
By Nadim Bahadoor | Last updated: March 16, 2018 at 15:14 pm
Overview
In this tutorial, we will learn the basics of Class Inheritance in Scala by creating an abstractclass and then extending it to create other sub-classes.
 
If you recall from the tutorial on What is Scala programming language, Scala is both an Object Oriented and Functional programming language. As a result of its Object Orientednature, it has full support of object hierarchies through the use of class inheritance.
 
Steps
1. How to define an abstract class called Donut 
When dealing with class and object hierarchies, you typically have a base class which encapsulates common behaviour. As an example, let's create an abstract class name Donut which defines a method signature for printName.

println("Step 1: How to define an abstract class called Donut")
 abstract class Donut(name: String) {

   def printName: Unit

}
 
NOTE:
•	Any class which extends the abstract class Donut will have to provide an implementation for the printName method.
2. How to extend abstract class Donut and define a sub-class of Donut called VanillaDonut
To create a sub-class of the abstract Donut class from Step 1, you have to use the extendskeyword, pass-through the name constructor parameter and also provide an implementation for the printName method.
 
As shown in the example below, the class VanillaDonut extends the abstract class Donut and also provides an implementation for the printName method.

println("\nStep 2: How to extend abstract class Donut and define a sub-class of Donut called VanillaDonut")
 class VanillaDonut(name: String) extends Donut(name) {

   override def printName: Unit = println(name)

 }

 object VanillaDonut {

   def apply(name: String): Donut = {
     new VanillaDonut(name)
   }

}
NOTE:
•	We've also created a Companion Object for the VanillaDonut class.
3. How to extend abstract class Donut and define another sub-class of Donut called GlazedDonut
Similar to Step 2, let's create another sub-class named GlazedDonut for the abstract Donut class.


println("\nStep 3: How to extend abstract class Donut and define another sub-class of Donut called GlazedDonut")
 class GlazedDonut(name: String) extends Donut(name) {

   override def printName: Unit = println(name)

 }

 object GlazedDonut {

   def apply(name: String): Donut = {
     new GlazedDonut(name)
   }

 }
NOTE:
•	Similar to Step 2, we've also created a Companion Object for the GlazedDonut class.
4. How to instantiate Donut objects
Let's create two Donut objects, one using the VanillaDonut class and the other one using the GlazedDonut class. Note that we are specifying the type for both vanillaDonut and glazedDonut to be of base type Donut.

println("\nStep 4: How to instantiate Donut objects")
val vanillaDonut: Donut = VanillaDonut("Vanilla Donut")
vanillaDonut.printName

val glazedDonut: Donut = GlazedDonut("Glazed Donut")
glazedDonut.printName

You should see the following output when you run your Scala application in IntelliJ:

Step 4: How to instantiate Donut objects
Vanilla Donut
Glazed Donut
NOTE:
VanillaDonut and GlazedDonut are sub-classes of the base class Donut, they both have access to the printName methodScala Tutorial - Learn How To Extend Case Class - Case Class Inheritance
By Nadim Bahadoor | Last updated: March 16, 2018 at 15:14 pm
Overview
In this tutorial, we will continue from what we've learned from the previous tutorial on Class Inheritance in Scala.  The examples in this tutorial will be focused on case classes which will extend an abstract class - case class inheritance.
 
If you recall from the tutorial on What is Scala programming language, Scala is both an Object Oriented and Functional programming language. As a result of its Object Orientednature, it has full support of object hierarchies through the use of class inheritance.



 
Steps
1. How to define an abstract class called Donut 
When dealing with class and object hierarchies, you typically have a base class which encapsulates common behaviour. As an example, let's create an abstract class name Donut which defines a method signature for printName.

println("Step 1: How to define an abstract class called Donut")
 abstract class Donut(name: String) {

   def printName: Unit

}
NOTE:
•	Any class which extends the abstract class Donut will have to provide an implementation for the printName method.
2. How to extend abstract class Donut and define a case class called VanillaDonut
To create a sub-class of the abstract Donut class from Step 1, you have to use the extendskeyword, pass-through the name constructor parameter and also provide an implementation for the printName method.
 
As shown in the example below, the case class VanillaDonut extends the abstract class Donut and also provides an implementation for the printName method.

println("\nStep 2: How to extend abstract class Donut and define a case class called VanillaDonut")
 case class VanillaDonut(name: String) extends Donut(name) {

   override def printName: Unit = println(name)

 }

NOTE:
•	Unlike the previous tutorial on Class Inheritance, we did not have to create aCompanion Object for the VanillaDonut case class because the case class will automatically provide a companion object.
3. How to extend abstract class Donut and define another case class of Donut called GlazedDonut
Similar to Step 2, let's create another case class named GlazedDonut which extends the abstract Donut class.


println("\nStep 3: How to extend abstract class Donut and define another case class called GlazedDonut")
 case class GlazedDonut(name: String) extends Donut(name) {

   override def printName: Unit = println(name)

 }

NOTE:
•	Similar to Step 2, we did not have to create a Companion Object for the GlazedDonut class.
4. How to instantiate Donut objects
Let's create two Donut objects, one using the VanillaDonut class and the other one using the GlazedDonut class. Note that we are specifying the type for both vanillaDonut and glazedDonut to be of base type Donut.

println("\nStep 4: How to instantiate Donut objects")
val vanillaDonut: Donut = VanillaDonut("Vanilla Donut")
vanillaDonut.printName

val glazedDonut: Donut = GlazedDonut("Glazed Donut")
glazedDonut.printName

You should see the following output when you run your Scala application in IntelliJ:

Step 4: How to instantiate Donut objects
Vanilla Donut
Glazed Donut
NOTE:
•	Since VanillaDonut and GlazedDonut are sub-classes of the base class Donut, they both have access to the printName method.
Scala Tutorial - Learn How To Create Typed Class
By Nadim Bahadoor | Last updated: March 16, 2018 at 15:14 pm
Overview
In this tutorial, we will continue from what we've learned from the previous tutorials on Class Inheritance and Case Class Inheritance in Scala.
 
The examples in this tutorial will be a review of inheritance in Scala with classes and case classes which extend an abstract class. In addition, we will also define a class which expects a given type - type class.
 
NOTE: A class which expects a given type should not be confused with a Type-Class which supports ad-hoc polymorphism. We will show examples of Type-Classes under Chapter 5 on Traits.
 
If you recall from the tutorial on What is Scala programming language, Scala is both an Object Oriented and Functional programming language. As a result of its Object Orientednature, it has full support of object hierarchies through the use of class inheritance.
 
Steps
1. How to define an abstract class called Donut 
When dealing with class and object hierarchies, you typically have a base class which encapsulates common behaviour. As an example, let's create an abstract class name Donut which defines a method signature for printName.

println("Step 1: How to define an abstract class called Donut")
 abstract class Donut(name: String) {

   def printName: Unit

}
NOTE:
•	Any class which extends the abstract class Donut will have to provide an implementation for the printName method.
2. How to extend abstract class Donut and define a case class called VanillaDonut
To create a sub-class of the abstract Donut class from Step 1, you have to use the extendskeyword, pass-through the name constructor parameter and also provide an implementation for the printName method.
 
As shown in the example below, the case class VanillaDonut extends the abstract class Donut and also provides an implementation for the printName method.

println("\nStep 2: How to extend abstract class Donut and define a case class called VanillaDonut")
 case class VanillaDonut(name: String) extends Donut(name) {

   override def printName: Unit = println(name)

 }

NOTE:
•	Unlike the previous tutorial on Class Inheritance, we did not have to create aCompanion Object for the VanillaDonut case class because the case class will automatically provide a companion object.
3. How to extend abstract class Donut and define another case class of Donut called GlazedDonut
Similar to Step 2, let's create another case class named GlazedDonut which extends the abstract Donut class.


println("\nStep 3: How to extend abstract class Donut and define another case class called GlazedDonut")
 case class GlazedDonut(name: String) extends Donut(name) {

   override def printName: Unit = println(name)

 }

NOTE:
•	Similar to Step 2, we did not have to create a Companion Object for the GlazedDonut class.
4. How to instantiate Donut objects
Let's create two Donut objects, one using the VanillaDonut class and the other one using the GlazedDonut class. Note that we are specifying the type for both vanillaDonut and glazedDonut to be of base type Donut.

println("\nStep 4: How to instantiate Donut objects")
val vanillaDonut: Donut = VanillaDonut("Vanilla Donut")
vanillaDonut.printName

val glazedDonut: Donut = GlazedDonut("Glazed Donut")
glazedDonut.printName

You should see the following output when you run your Scala application in IntelliJ:

Step 4: How to instantiate Donut objects
Vanilla Donut
Glazed Donut
NOTE:
•	Since VanillaDonut and GlazedDonut are sub-classes of the base class Donut, they both have access to the printName method.
5. How to define a ShoppingCart type class which expects Donut types
The above steps should be familiar already if you have followed the previous tutorials on Class Inheritance and Case Class Inheritance.
 
What if you had to define a class which expects a particular type parameter? As an example, let us define a ShoppingCart class which expects a sequence of Donut types.

println("\nStep 5: How to define a ShoppingCart type class which expects Donut types")
class ShoppingCart[D <: Donut](donuts: Seq[D]) {

  def printCartItems: Unit = donuts.foreach(_.printName)

}
NOTE:
•	With the notation [D <: Donut], we are restricting only Donut types to be passed-through to the ShoppingCart class.
6. How to create instances or objects of ShoppingCart class
The example below shows how to instantiate a ShoppingCart class of type Donut.

println("\nStep 6: How to create instances or objects of ShoppingCart class")
val shoppingCart: ShoppingCart[Donut] = new ShoppingCart(Seq[Donut](vanillaDonut, glazedDonut))
shoppingCart.printCartItems

You should see the following output when you run your Scala application in IntelliJ:

Step 6: How to create instances or objects of ShoppingCart class
Vanilla Donut
Glazed Donut
NOTE:
•	You will get compiler error if you try to instantiate a ShoppingCart class with a different type other than the Donut type.
•	As an example, you will get a compiler error if you tried to create ShoppingCart of type String

val shoppingCart2: ShoppingCart[Donut] = new ShoppingCart[String](Seq("Vanilla Donut"))
This conclud
Scala Tutorial - Learn How To Create Covariance Type Class
By Nadim Bahadoor | Last updated: March 16, 2018 at 15:14 pm
Overview
In this tutorial, we will continue from what we've learned from the previous tutorials on Class Inheritance, Case Class Inheritance and Type Class in Scala.
 
The examples in this tutorial will be a review of inheritance in Scala with classes and case classes which extend an abstract class. In addition, we will also define a class which expects a given type - type class.
 
To follow on from the previous tutorial on Type Class, we will show example of enforcing type hierarchies through the use of variance - in particular covariance.
 
If you recall from the tutorial on What is Scala programming language, Scala is both an Object Oriented and Functional programming language. As a result of its Object Orientednature, it has full support of object hierarchies through the use of class inheritance.
 
Steps
1. How to define an abstract class called Donut 
When dealing with class and object hierarchies, you typically have a base class which encapsulates common behaviour. As an example, let's create an abstract class name Donut which defines a method signature for printName.

println("Step 1: How to define an abstract class called Donut")
 abstract class Donut(name: String) {

   def printName: Unit

}
NOTE:
•	Any class which extends the abstract class Donut will have to provide an implementation for the printName method.
2. How to extend abstract class Donut and define a case class called VanillaDonut
To create a sub-class of the abstract Donut class from Step 1, you have to use the extendskeyword, pass-through the name constructor parameter and also provide an implementation for the printName method.
 
As shown in the example below, the case class VanillaDonut extends the abstract class Donut and also provides an implementation for the printName method.

println("\nStep 2: How to extend abstract class Donut and define a case class called VanillaDonut")
 case class VanillaDonut(name: String) extends Donut(name) {

   override def printName: Unit = println(name)

 }

NOTE:
•	Unlike the previous tutorial on Class Inheritance, we did not have to create aCompanion Object for the VanillaDonut case class because the case class will automatically provide a companion object.
3. How to extend abstract class Donut and define another case class of Donut called GlazedDonut
Similar to Step 2, let's create another case class named GlazedDonut which extends the abstract Donut class.


println("\nStep 3: How to extend abstract class Donut and define another case class called GlazedDonut")
 case class GlazedDonut(name: String) extends Donut(name) {

   override def printName: Unit = println(name)

 }

NOTE:
•	Similar to Step 2, we did not have to create a Companion Object for the GlazedDonut class.
4. How to instantiate Donut objects
Let's create two Donut objects, one using the VanillaDonut class and the other one using the GlazedDonut class. Note that we are specifying the type for both vanillaDonut and glazedDonut to be of base type Donut.

println("\nStep 4: How to instantiate Donut objects")
val vanillaDonut: Donut = VanillaDonut("Vanilla Donut")
vanillaDonut.printName

val glazedDonut: Donut = GlazedDonut("Glazed Donut")
glazedDonut.printName

You should see the following output when you run your Scala application in IntelliJ:

Step 4: How to instantiate Donut objects
Vanilla Donut
Glazed Donut
NOTE:
•	Since VanillaDonut and GlazedDonut are sub-classes of the base class Donut, they both have access to the printName method.
5. How to define a ShoppingCart type class which expects Donut types
The above steps should be familiar already if you have followed the previous tutorials on Class Inheritance and Case Class Inheritance.
 
What if you had to define a class which expects a particular type parameter? As an example, let us define a ShoppingCart class which expects a sequence of Donut types.

println("\nStep 5: How to define a ShoppingCart type class which expects Donut types")
class ShoppingCart[D <: Donut](donuts: Seq[D]) {

  def printCartItems: Unit = donuts.foreach(_.printName)

}
NOTE:
•	With the notation [D <: Donut], we are restricting only Donut types to be passed-through to the ShoppingCart class.
6. How to create instances or objects of ShoppingCart class
The example below shows how to instantiate a ShoppingCart class of type Donut.

println("\nStep 6: How to create instances or objects of ShoppingCart class")
val shoppingCart: ShoppingCart[Donut] = new ShoppingCart(Seq[Donut](vanillaDonut, glazedDonut))
shoppingCart.printCartItems

You should see the following output when you run your Scala application in IntelliJ:

Step 6: How to create instances or objects of ShoppingCart class
Vanilla Donut
Glazed Donut
NOTE:
•	You will get compiler error if you try to instantiate a ShoppingCart class with a different type other than the Donut type.
•	As an example, you will get a compiler error if you tried to create ShoppingCart of type String

val shoppingCart2: ShoppingCart[Donut] = new ShoppingCart[String](Seq("Vanilla Donut"))
•	But what if you need to create a ShoppingCart of type VanillaDonut? You will get a compiler error for a ShoppingCart of type VanillaDonut:

val shoppingCart: ShoppingCart[Donut] = new ShoppingCart[VanillaDonut](Seq(vanillaDonut))
 
7. How to enable covariance on ShoppingCart
The example below shows how to instantiate a ShoppingCart2 class of type VanillaDonut by first enabling covariance for Donut types on ShoppingCart2 class.

println(s"\nStep 7: How to enable covariance on ShoppingCart")
 class ShoppingCart2[+D <: Donut](donuts: Seq[D]) {

 def printCartItems: Unit = donuts.foreach(_.printName)

 }

 val shoppingCart2: ShoppingCart2[Donut] = new ShoppingCart2[VanillaDonut](Seq(vanillaDonut))
 shoppingCart2.printCartItems

You should see the following output when you run your Scala application in IntelliJ:

Step 7: How to enable covariance on ShoppingCart
Vanilla Donut
NOTE:
•	We've enabled covariance of type Donuts using the notation [+D <: Donut]
•	In other words, you can now create instances of ShoppingCart of type Donut or sub-types of Donuts such as VanillaDonut.
Scala Tutorial - Learn How To Create Contra-Variance Type Class
By Nadim Bahadoor | Last updated: March 16, 2018 at 15:14 pm
Overview
In this tutorial, we will continue from what we've learned from the previous tutorials on Class Inheritance, Case Class Inheritance, Type Class and Covariance Type Parameter in Scala.
 
The examples in this tutorial will be a review of inheritance in Scala with classes and case classes which extend an abstractclass. In addition, we will also define a class which expects a given type - type class.
 
To follow on from the previous tutorials on Type Class and Covariance Type Parameter, we will show example of enforcing type hierarchies through the use of variance - in particular contra-variance.
 
If you recall from the tutorial on What is Scala programming language, Scala is both an Object Oriented and Functional programming language. As a result of its Object Oriented nature, it has full support of object hierarchies through the use of class inheritance.
 
Steps
1. How to define an abstract class called Donut 
When dealing with class and object hierarchies, you typically have a base class which encapsulates common behaviour. As an example, let's create an abstract class name Donut which defines a method signature for printName.

println("Step 1: How to define an abstract class called Donut")
 abstract class Donut(name: String) {

   def printName: Unit

}
NOTE:
•	Any class which extends the abstract class Donut will have to provide an implementation for the printName method.
2. How to extend abstract class Donut and define a case class called VanillaDonut
To create a sub-class of the abstract Donut class from Step 1, you have to use the extends keyword, pass-through the nameconstructor parameter and also provide an implementation for the printName method.
 
As shown in the example below, the case class VanillaDonut extends the abstract class Donut and also provides an implementation for the printName method.

println("\nStep 2: How to extend abstract class Donut and define a case class called VanillaDonut")
 case class VanillaDonut(name: String) extends Donut(name) {

   override def printName: Unit = println(name)

 }

NOTE:
•	Unlike the previous tutorial on Class Inheritance, we did not have to create a Companion Object for the VanillaDonut case class because the case class will automatically provide a companion object.
3. How to extend abstract class Donut and define another case class of Donut called GlazedDonut
Similar to Step 2, let's create another case class named GlazedDonut which extends the abstract Donut class.


println("\nStep 3: How to extend abstract class Donut and define another case class called GlazedDonut")
 case class GlazedDonut(name: String) extends Donut(name) {

   override def printName: Unit = println(name)

 }

NOTE:
•	Similar to Step 2, we did not have to create a Companion Object for the GlazedDonut class.
4. How to instantiate Donut objects
Let's create two Donut objects, one using the VanillaDonut class and the other one using the GlazedDonut class. Note that we are specifying the type for both vanillaDonut and glazedDonut to be of base type Donut.

println("\nStep 4: How to instantiate Donut objects")
val vanillaDonut: Donut = VanillaDonut("Vanilla Donut")
vanillaDonut.printName

val glazedDonut: Donut = GlazedDonut("Glazed Donut")
glazedDonut.printName

You should see the following output when you run your Scala application in IntelliJ:

Step 4: How to instantiate Donut objects
Vanilla Donut
Glazed Donut
NOTE:
•	Since VanillaDonut and GlazedDonut are sub-classes of the base class Donut, they both have access to the printNamemethod.
5. How to define a ShoppingCart type class which expects Donut types
The above steps should be familiar already if you have followed the previous tutorials on Class Inheritance and Case Class Inheritance.
 
What if you had to define a class which expects a particular type parameter? As an example, let us define a ShoppingCart class which expects a sequence of Donut types.

println("\nStep 5: How to define a ShoppingCart type class which expects Donut types")
class ShoppingCart[D <: Donut](donuts: Seq[D]) {

  def printCartItems: Unit = donuts.foreach(_.printName)

}
NOTE:
•	With the notation [D <: Donut], we are restricting only Donut types to be passed-through to the ShoppingCart class.
6. How to create instances or objects of ShoppingCart class
The example below shows how to instantiate a ShoppingCart class of type Donut.

println("\nStep 6: How to create instances or objects of ShoppingCart class")
val shoppingCart: ShoppingCart[Donut] = new ShoppingCart(Seq[Donut](vanillaDonut, glazedDonut))
shoppingCart.printCartItems

You should see the following output when you run your Scala application in IntelliJ:

Step 6: How to create instances or objects of ShoppingCart class
Vanilla Donut
Glazed Donut
NOTE:
•	Assume you want a ShoppingCart of VanillaDonut but would also like to inject Donut types.

val shoppingCart: ShoppingCart[VanillaDonut] = new ShoppingCart[Donut](Seq(glazedDonut))
•	You will get a compiler error when trying to have a ShoppingCart[VanillaDonut] reference a ShoppingCart[Donut]
7. How to enable contra-variance on ShoppingCart
The example below shows how to instantiate a ShoppingCart2 class of type VanillaDonut by first enabling contra-variance for Donut types on ShoppingCart2 class.

println(s"\nStep 7: How to enable contra-variance on ShoppingCart")
class ShoppingCart2[-D <: Donut](donuts: Seq[D]) {

  def printCartItems: Unit = donuts.foreach(_.printName)

}
 
val shoppingCart2: ShoppingCart2[VanillaDonut] = new ShoppingCart2[Donut](Seq(glazedDonut))
shoppingCart2.printCartItems

You should see the following output when you run your Scala application in IntelliJ:

Step 7: How to enable contra-variance on ShoppingCart
Glazed Donut
NOTE:
•	We've enabled contra-variance of type Donuts using the notation [-D <: Donut]
•	In other words, you can now have a ShoppingCart of type VainllaDonut ShoppingCart[VanillaDonut] reference ShoppingCart of type Donut ShoppingCart2[Donut]

