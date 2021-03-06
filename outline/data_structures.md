---
layout: default
title: Vectors and Maps
permalink: /outline/data_structures.html
---

{::options parse_block_html="true" /}

{% comment %}

http://clojurebridge.github.io/curriculum/outline/data_structures.html

{% endcomment %}

<section>
Data Structures
----------------------------------------
{: .slide-title .chapter}

* Vectors
* Maps
</section>

<section>
### Group of data - Collections
{: .slide_title .slide}

#### <button class="link" ng-model="block11" ng-click="block11=!block11">Intro</button>

> So far, we've dealt with discrete pieces of data: one number, one
string, one value. When programming, it is more often the case that
you want to work with groups of data.
{: ng-show="block11" .description}

> Clojure has great facilities for working with these groups, or
*collections*, of data. Not only does it provide four different types
of collections, but it also provides a uniform way to use all of these
collections together.
{: ng-show="block11" .description}
</section>

<section>
### Vectors
{: .slide_title .slide}

#### Sequential collection <button class="link" ng-model="block21" ng-click="block21=!block21">Details</button>

> Vectors are sequential collections of data. You could say they are
lists of data, but we also have another collection called a list. If
you have programmed in another language, these might have been
called arrays in that language.
{: ng-show="block21" .description}

#### Compartment-like structure <button class="link" ng-model="block22" ng-click="block22=!block22">Details</button>

> To imagine a vector, imagine a box split into some number of
> equally-sized compartments. Each of those compartments has a number.
> You can put a piece of data inside each compartment and always know
> where to find it, as it has a number.
{: ng-show="block22" .description}

> Note that the numbers start with 0. That may seem strange, but we
> often count from zero when programming.
{: ng-show="block22" .description}

![Vector](img/vector.png)

</section>

<section>
#### Syntax <button class="link" ng-model="block31" ng-click="block31=!block31">Details</button>

>Vectors are written using square brackets with any number of pieces
>of data inside them, separated by spaces. Here are some examples of
>vectors:
{: ng-show="block31" .description}

```clojure
[1 2 3 4 5]
[56.9 60.2 61.8 63.1 54.3 66.4 66.5 68.1 70.2 69.2 63.1 57.1]
[]
```
</section>

<section>
#### Example <button class="link" ng-model="block41" ng-click="block41=!block41">Details</button>

> When there are a couple of turtles,
> `(turtle-names)` command will return turtle names in the form of a
> vector.
{: ng-show="block41" .description}

```clojure
(turtle-names)
;=> [:trinity :smith0 :smith1 :smith2 :neo]
```
</section>


<section>
#### Creation <button class="link" ng-model="block61" ng-click="block61=!block61">Details</button>

> The next two functions are used to make new vectors. The `vector`
> function takes any number of items and puts them in a new vector.
> `conj` is an interesting function that you'll see used with all the
> data structures. With vectors, it takes a vector and an item and
> returns a new vector with that item added to the end of the vector.
> Why the name `conj`? The verb "conjugate" has an archaic meaning "to
> join together," which is what we're doing: we're joining the new
> item to the vector.
{: ng-show="block61" .description}

```clojure
(vector 5 10 15)
;=> [5 10 15]

(conj [5 10] 15)
;=> [5 10 15]
```
</section>

<section>
#### Extraction <button class="link" ng-model="block81" ng-click="block81=!block81">Details</button>

> Now, take a look at these four functions. `count` gives us a
count of the number of items in a vector. `nth` gives us the nth
item in the vector. Note that we start counting at 0, so in the
example, calling `nth` with the number 1 gives us what we'd call the
second element when we aren't programming. `first` returns the first
item in the collection. `rest` returns all except the first item.
Try not to think about that and `nth` at the same time, as they can
be confusing.
{: ng-show="block81" .description}

```clojure
(count [5 10 15])
;=> 3
(nth [5 10 15] 1)
;=> 10
(first [5 10 15])
;=> 5
(rest [5 10 15])
;=> (10 15)
```
</section>

<section>
#### EXERCISE 1: See turtle names
{: .slide_title .slide}

* Go to `walk.clj` file
* Type `(add-turtle)` and evaluate this line
* Repeat adding a turtle a couple of times
* Type `(turtle-names)` and see the result
</section>

<section>
#### EXERCISE 2: Make a vector
{: .slide_title .slide}

* Go to insta-REPL
* Make a vector of the high temperatures for the next 7 days in the
  town where you live.
* Then use the `nth` function to get the high temperature for next
  Tuesday.
</section>


<section>
### Maps

#### key value pairs <button class="link" ng-model="block101" ng-click="block101=!block101">Details</button>

>Maps hold a set of keys and values associated with them. You can
>think of it like a dictionary: you look up things using a word (a
>keyword) and see the definition (its value). If you've programmed in
>another language, you might have seen something like maps--maybe
>called dictionaries, hashes, or associative arrays.
{: ng-show="block101" .description}

![Map](img/map.png)
</section>

<section>
#### Syntax <button class="link" ng-model="block102" ng-click="block102=!block102">Details</button>

> We write maps by enclosing alternating keys and values in curly braces, like so.
{: ng-show="block102" .description}

> Maps are useful because they can hold data in a way we normally
> think about it. Take our made up example, Sally Brown. A map can
> hold her first name and last name, her address, her favorite food,
> or anything else. It's a simple way to collect that data and make it
> easy to look up. The last example is an empty map. It is a map that
> is ready to hold some things, but doesn't have anything in it yet.
{: ng-show="block102" .description}

```clojure
{:first "Sally" :last "Brown"}
{:a 1 :b "two"}
{}
```
</section>

<section>
#### Example <button class="link" ng-model="block103" ng-click="block103=!block103">Details</button>

> When turtle received commands such that `forward` or `right`,
> those return the result as a form of map of map.
{: ng-show="block103" .description}

```clojure
(forward 40)
;=> {:trinity {:length 40}}
(right 90)
;=> {:trinity {:angle 90}}
```
</section>

<section>
#### Creation <button class="link" ng-model="block104" ng-click="block104=!block104">Details</button>

> `assoc` and `dissoc` are paired functions: they associate and disassociate items from a map. See how we add the last name "Brown" to the map with `assoc`, and then we remove it with `dissoc`. `merge` merges two maps together to make a new map.
{: ng-show="block104" .description}

```clojure
(assoc {:first "Sally"} :last "Brown")
;=> {:first "Sally", :last "Brown"}

(dissoc {:first "Sally" :last "Brown"} :last)
;=> {:first "Sally"}

(merge {:first "Sally"} {:last "Brown"})
;=> {:first "Sally" :last "Brown"}
```
</section>

<section>
#### Extraction 1 <button class="link" ng-model="block105" ng-click="block105=!block105">Details</button>

> `count`, every collection has this function. Why do you think the
> answer is two? `count` is returning the number of associations.
{: ng-show="block105" .description}

> Since map is a key-value pair, the key is used to get a value from a
> map. One of the ways often used in Clojure is the examples below.
> We can use a keyword like using a function in order to look
> up values in a map. In the last example, we supplied the key `:MISS`.
> This works when the key we asked for is not in the map.
{: ng-show="block105" .description}

```clojure
(count {:first "Sally" :last "Brown"})
;=> 2

(:first {:first "Sally" :last "Brown"})
;=> "Sally"
(:last {:first "Sally"})
;=> nil
(:last {:first "Sally"} :MISS)
;=> :MISS
```
</section>

<section>
#### Extraction 2 <button class="link" ng-model="block106" ng-click="block106=!block106">Details</button>

> Then we have `keys` and `vals`, which are pretty simple: they return
> the keys and values in the map. The order is not guaranteed, so we
> could have gotten `(:first :last)` or `(:last :first)`.
{: ng-show="block106" .description}

```clojure
(keys {:first "Sally" :last "Brown"})
;=> (:first :last)

(vals {:first "Sally" :last "Brown"})
;=> ("Sally" "Brown")
```
</section>

<section>
### Collections of Collections

#### <button class="link" ng-model="block101" ng-click="block101=!block101">Intro</button>

> Simple values such as numbers, keywords, and strings are not the
> only types of things you can put into collections. You can also put
> other collections into collections, so you can have a vector of
> maps, or a list of vectors, or whatever combination fits your data.
{: ng-show="block101" .description}
</section>

<section>
#### Vector of Maps

```clojure
(state-all)
;=> [{:trinity {:x -1.7484556000744965E-6, :y 39.99999999999996, :angle 90, :color [30 30 30]}}
{:smith0 {:x 30.0, :y 0.0, :angle 0, :color [10 107 30]}}
{:smith1 {:x 0, :y 0, :angle 90, :color [10 107 30]}}]

(def states (state-all))
;=> #'clojurebridge-turtle.walk/states

(first states)
;=> {:trinity {:x -1.7484556000744965E-6, :y 39.99999999999996, :angle
90, :color [30 30 30]}}
```
</section>

<section>
#### Map of Maps

```clojure
(def st (first states))
;=> #'clojurebridge-turtle.walk/st

st
;=> {:trinity {:x -1.7484556000744965E-6, :y 39.99999999999996, :angle
90, :color [30 30 30]}}

(:trinity st)
;=> {:x -1.7484556000744965E-6, :y 39.99999999999996, :angle 90, :color [30 30 30]}

(get-in st [:trinity :angle])
;=> 90
```
</section>


<section>
#### EXERCISE 1: See turtles states
{: .slide_title .slide}

* Go to `walk.clj` file
* Try examples of previous two slides
* See what values you get

> Every time you write a line of code,
> hit <kbd>Ctrl</kbd> + <kbd>Enter</kbd> or <kbd>Cmd</kbd> +
> <kbd>Enter</kbd> to evaluate it one by one.

```clojure
(state-all)
(def states (state-all))
(first states)
(def st (first states))
st
(:trinity st)
(get-in st [:trinity :angle])
```
</section>

<section>
#### EXERCISE 2: Modeling Yourself
{: .slide_title .slide}

* Go to insta-REPL
    - (Option) You may create a new file and write code in the file. To
    evaluate, paste code block on `lein repl`
* Make a map representing yourself
* Make sure it contains your first name and last name
* Then, add your hometown to the map using [assoc](http://grimoire.arrdem.com/1.6.0/clojure.core/assoc/) or [merge](http://grimoire.arrdem.com/1.6.0/clojure.core/merge/).
</section>

<section>
#### EXERCISE 3 [BONUS]: Modeling your classmates
{: .slide_title .slide}

* First, take the map you made about yourself in previous exercise.
* Then, create a vector of maps containing the first name, last name and hometown of two or three other classmates around you.
* Lastly, add your map to their information using [conj](http://grimoire.arrdem.com/1.6.0/clojure.core/conj/).
</section>

{% comment %}

:star2: Links below is for slide only. Go to [README.md](../README.md)
instead. :star2:

{% endcomment %}

<section>
Return to the <a href="javascript:;" onClick="Reveal.slide(1);">first slide</a>,
or go to the [curriculum outline](/curriculum/#/1).
</section>
