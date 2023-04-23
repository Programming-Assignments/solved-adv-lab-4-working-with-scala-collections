Download Link: https://assignmentchef.com/product/solved-adv-lab-4-working-with-scala-collections
<br>
In this lab you will gain further practice in functional programming in Scala. You will work with functions, maps, lists and tuples. You can use whichever of the tools introduced in Lab 1 you prefer to attempt the following exercises. You should use your lecture notes (part 4&amp;5) and references listed under ‘Further reading’ to help you.

Task 1. Mapping and folding

The <strong><em>map</em></strong> method of <em>List</em> applies a function to each element of the list in turn, and returns a new list containing the resulting elements. The following example applies a function that calculates the square of each element:

List(1,2,3,4,5).map(x=&gt;x * x)

and returns

List(1, 4, 9, 16, 25)

The example can also be written with variations on the syntax such as the following:

List(1,2,3,4,5) map {x=&gt;x * x}

<ol>

 <li>Use <em>map</em> to transform the list <em>List(“1″,”2″,”3″,”4″,”5”)</em> to the list of integers <em>List(1,2,3,4,5).</em> Use whichever of the above styles of writing map above that you prefer.</li>

 <li>Use <em>map</em> to transform the list <em>List(“aa”,”bb”,”cc”,”dd”,”ee”)</em> to the list of strings <em>List(“AA”,”BB”,”CC”,”DD”,”EE”)</em></li>

</ol>

The <strong><em>foldLeft</em></strong> method of <em>List</em> transforms the list to a value by applying a function in turn to each element and the result of applying it to previous elements. The following example calculates the factorial of 6 by multiplying the values in the range 1 to 6. The second parameter of <em>foldLeft</em> is a function of two parameters <em>x</em> and <em>y</em> that represent the total so far (<em>x</em>) and the current element (y). The first parameter of <em>foldLeft</em>, 1, is the initial value for <em>x</em> when applying to the first element:

List(1,2,3,4).foldLeft(1)((x,y) =&gt; x * y)

This can also be written with some variations on the syntax, for example:

List(1,2,3,4).foldLeft(1){(x,y) =&gt; x * y}

The function can also be written in shorthand form, where the two _ represent the parameters:

List(1,2,3,4).foldLeft(1)(_ * _)

<ol start="3">

 <li>Create a list of integers <em>list</em>, using whatever syntax you prefer for creating a list, containing the values 1 to 19.</li>

 <li>Define and test a function <em>sum</em> that uses the <em>foldLeft</em> method of <em>List</em> to evaluate <u>the sum of the list elements</u>. Use whichever of the above styles of writing <em>foldLeft</em> above that you prefer. The signature of the sum function should be:</li>

</ol>

def sum1(list:List[Int]):Int =  …

What must the value of the first parameter of <em>foldLeft</em> be?

<ol start="5">

 <li>Define and test a function <em>length</em> that uses the <em>foldLeft</em> method to compute <u>the length of the list</u>. Again, the function should have a single parameter of type <em>List[Int]</em> and return type <em>Int</em>.</li>

 <li>Define and test a function <em>average</em> that uses the <em>foldLeft</em> method to compute <u>the average (mean) of the list elements</u> (hint: this will need two calls to <em>foldLeft</em>). The parameter of this list will be as before, but what should the return type be?</li>

 <li>Define and test a function last that uses the <em>foldLeft</em> method to find <u>the last element of the list</u>. In this case, the first parameter of <em>foldLeft</em> (the initial value) needs to be <em>head</em>, and the function applied should simply return the current element.</li>

</ol>

You have already seen <u>recursive</u> functions that perform some of these computations – which do you prefer, folding or recursion?

<ol start="8">

 <li>Look up the Scala documentation for the <em>List</em> class and compare the entries for <em>foldLeft</em> and <em>foldRight</em>. Do you think it will make any difference if you had used <em>foldRight</em> instead of <em>foldLeft</em> in any of these examples (you can try it to check)?</li>

 <li><em>(Challenge)</em> Define and test functions that take a parameter of type <em>List[Int]</em> and compute, using <em>foldLeft</em>, each of the following. You will need to think carefully about the type to be returned, and the starting value:</li>

 <li>the penultimate element of the list</li>

 <li>the list in reverse order</li>

 <li>the distinct elements of the list (test this with a list containing the elements (1,2,2,3,3,4,5) – the result should contain no repeated values)</li>

</ol>

<h3>Task 2. Maps</h3>

A <u>map</u> in Scala is a collection of key/value pairs. Keys and values can be of any type. For this exercise you may find it useful to refer to the Scaladocs fo the Map classes.

<strong>Creating maps</strong>

You can create a map like this:

val french = Map(1-&gt;”un”, 2-&gt;”deux”, 3-&gt;”trois”)

Maps are immutable by default. If you want to create a mutable map you need to specify a mutable type explicitly:var mutableFrench = scala.collection.mutable.Map(1-&gt; “un”, 2-&gt;”deux”, 3-&gt;”trois”)

If a map is mutable, you can add a new entry using the + operator or += operator, for example:mutableFrench += 4 -&gt; “quatre”

You can concatenate maps using the ++ or ++= operator, for example:

val moreFrench = Map(5-&gt; “cinq”, 6-&gt;”six”)mutableFrench ++= moreFrench

<ol>

 <li>Create a mutable map <em>airports</em> containing the following key/value pairs representing cities and the codes of their airports (as strings):</li>

</ol>

Glasgow -&gt; GLA

Dubai -&gt; DXB

Berlin -&gt; TXL

<ol start="2">

 <li>Create a map <em>moreAirports</em> containing a single pair:</li>

</ol>

Helsinki -&gt; HEL

<ol start="3">

 <li>Create a map <em>evenMoreAirports</em> containing the pairs:</li>

</ol>

Glasgow -&gt; PIK

Los Angeles -&gt; LAX




<ol start="4">

 <li>Create a new map <em>newAirports</em> by concatenating <em>moreAirports</em> and <em>evenMoreAirports</em> using the ++ operator.</li>

</ol>




<ol start="5">

 <li>Add (concatentate) <em>newAirports</em> to <em>airports</em> using the ++= operator. Look at the result – what happened to Glasgow?</li>

</ol>







<ol start="6">

 <li>Add the following single entry to <em>airports</em> using the += operator.</li>

</ol>




Tokyo -&gt; HAN




<strong>Extracting data from maps</strong>




<ol>

 <li>You can get the keys of a map as a list using the <em>keys</em> method:</li>

</ol>




val cities = airports.keys.toList




Use a different method of <em>Map</em> to get a list containing the airport codes in <em>airports</em>.




<ol start="2">

 <li>You can get the value for a specified key using the <em>get</em> method:</li>

</ol>




val gla = airports.get(“Glasgow”)




Try this. What type is the result? Try finding the value for the key “London”. Why do you think the <em>get</em> method returns the type that it does?




<ol start="3">

 <li>Where a method returns an <em>Option</em>, the safest way to extract the value you want from the <em>Option</em> is to use pattern matching:</li>

</ol>




val gla2 = airports.get(“Glasgow”) match {case Some(ap) =&gt; apcase None =&gt; “not found”}




Try this, and try also with the key “London”.







Include use of find – tweak this example to fit:

find method of map

give an example, e.g.:

val airports = Map(“GLA” -&gt; “Glasgow”, “TXL” -&gt; “Berlin”, “PIK” -&gt; “Glasgow”, “LAX” -&gt; “Los Angeles”)

val default = (“not found”,””)

var value = “Berlin”

airports.find(_._2==value).getOrElse(default)._1

value = “Los Angeles”

<strong>airports.find(x =&gt;x._2==value).getOrElse(default)._1</strong>

value = “Glasgow”

airports.find(_._2==value).getOrElse(default)._1







<strong>Iterating</strong>




Sometimes it is useful to iterate through a collection without returning a result. For example, you might simply want to print the contents of the collection. (In functional terms, this would be an example of a side-effect as it changes the state of the console display).




You can do this for a list using a <em>for</em> expression, for example




for (x &lt;- mylist) {println(x)}




or the <em>foreach</em> method of List

mylist foreach {x =&gt; println(x)}







For a map, you can iterate through the key/value pairs:




for ((k, v) &lt;- mymap) {println(s”$k – $v”)}

mymap foreach {case (k, v) =&gt; println(s”$k – $v”))}




<ol>

 <li>Using either <em>for</em> expressions or <em>foreach</em>, print the contents of the airports map as follows (first just the keys, then keys and values together):</li>

</ol>




Code – Helsinki

Code – Los Angeles

Code – Tokyo

Code – Glasgow

Code – Dubai

Code – Berlin




City:Helsinki – Code:HEL

City:Los Angeles – Code:LAX

City:Tokyo – Code:HND

City:Glasgow – Code:PIK

City:Dubai – Code:DXB

City:Berlin – Code:TXL




<h3></h3>




<strong> </strong>

<h3>Task 3. Tuples and zipping</h3>




A Scala <u>tuple </u>is a class that can contain a miscellaneous collection of elements. It is “1-indexed”, so the first element has index 1.




You can create a tuple and access its elements like this:




val tuple = (“apple”, “red”)val fruit = tuple._1val colour = tuple._2

Tuples can contain elements of different types:

val getUserInfo = (“Al”, 42, 200.0)

You can extract several elements at once and assign these to named variables:val(name, age, weight) = getUserInfo




<ol>

 <li>Try the examples above. Evaluate the variables name, age and weight to ensure they have the values you expect.</li>

</ol>




Tuples are useful in many situations and can be used along with other collections. For example, you can have a list of tuples:




val fruits = List((“apple”, “red”), (“banana”, “yellow”), (“orange”, “orange”))

If the tuples have two elements each, you can convert this to a Map:

val fruitMap = fruits toMap




You can also have a tuple containing lists:




val lists = (List(1,2,3), List(4,5,6), List(7,8,9))




<ol start="2">

 <li>Create a map of fruits/colours using the above code, and print the contents by iterating to give:</li>

</ol>




Fruit:apple – Colour:red

Fruit:banana – Colour:yellow

Fruit:orange – Colour:orange




<ol start="3">

 <li>Create the following lists:</li>

</ol>




val cities = List(“Glasgow”, “Dubai”, “Berlin”)val codes = List(“GLA”,”DXB”,”TXL”)




<ol start="4">

 <li>Evaluate the following expression, which uses the <em><u>zip</u></em><u> operator</u>, and describe the result and the effect of <em>zip</em>.</li>

</ol>




cities zip codes




<ol start="5">

 <li>Use the <em>zip</em> operator and a suitable method call to create a map of cities/codes (similar to the ones in task 2), and print the contents by iterating.</li>

</ol>




You have now seen how to use <em>zip</em> to join two lists to form a map. The next example shows another way to use <em>zip</em> to combine lists.




<ol start="6">

 <li>Create the following lists that represent golf players and their scores in two rounds of a tournament.</li>

</ol>




val players = List(“Stenson”, “Mickelson”, “Galllacher”)val round1 = List(70, 68, 70)val round2 = List(65, 72, 68)




<ol start="7">

 <li>Check that</li>

</ol>




round1 zip round2




creates a list of tuples, each of which contains one player’s scores for the two rounds:

List((70,65), (68,72), (70,68))




<ol start="8">

 <li>Instead of creating a map of the results, you can create a new list that contains the total score for each player by applying a suitable function to each tuple in the list:</li>

</ol>




val scores2 = round1 zip round2 map{case (x, y) =&gt; x + y}




Try this and check that the result is as you expect.




<ol start="9">

 <li>Finally, use <em>zip</em> again to create a map of players and total scores and print the contents by iterating, to give:</li>

</ol>




Player:Stenson – total score 135

Player:Mickelson – total score 140

Player:Galllacher – total score 138








