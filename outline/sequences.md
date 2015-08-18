---
layout: default
title: Sequences and Loops
permalink: /outline/sequences.html
---

{::options parse_block_html="true" /}

{% comment %}

http://clojurebridge.github.io/curriculum/outline/sequences.html

{% endcomment %}

<section>
[BONUS]

Sequences and Loops
-------------------------
{: .slide-title .chapter}

* What are sequences
* `doseq`
* Loops in Clojure
    - `loop`
    - `dotimes`
    - `for`
</section>

<section>
### What are sequences?
{: .slide_title .slide}

#### Clojure's data structures <button class="link" ng-model="block11" ng-click="block11=!block11">Details</button>

> In Clojure, we can say every data structure is a sequence.
> So far, we learned `vector` and `map`, both of which are sequence.
> String is also a sequence. When something is **seq-able**, it is a sequence.
{: ng-show="block11" .description}

#### `first` item or not <button class="link" ng-model="block12" ng-click="block12=!block12">Details</button>

> If something is **seq-able**, it returns the first item in the sequence
> by the `first` function. This is a good test whether it is a sequence or not.
{: ng-show="block12" .description}
</section>

<section>
#### Results of `first`

```clojure
(turtle-names)
;=> [:trinity :smith0 :smith1]  ; vector
(first (turtle-names))
;=> :trinity                    ; the first item

(:trinity (state))
;=> {:x 0, :y 0, :angle 90, :color [30 30 30]}  ; map
(first (:trinity (state)))
[:x 0]                                          ; the first item

(first "Hello, World!")  ; string
;=> \H                   ; the first item

(first :trinity)         ; keyword is not seq-able
;=> IllegalArgumentException Don't know how to create ISeq from:
clojure.lang.Keyword  clojure.lang.RT.seqFrom (RT.java:528)
```
</section>

<section>
### `doseq`

<button class="link" ng-model="block31" ng-click="block31=!block31">Details1</button>
<button class="link" ng-model="block32" ng-click="block32=!block32">Details2</button>

> Clojure is very good at *iterate* over a sequence.
> There are many functions that interact on sequences.
> The `doseq`(for **do a sequence**) is one of the well-used functions
> of such. This function works quite similar to `map` function we have
> already studied.
{: ng-show="block31" .description}

> The `doseq` function takes two parameters:
> 1. The sequence of things, for instance, a vector
> 2. A function which is repeatedly called with each element in the sequence
>
> Notice that the first argument to `doseq` specifies the sequence as
> an odd-looking vector: `[variable value ...]`.
> The number of elements in this vector need to be even, since the
> first element will be the **variable** and the next one will be
> evaluated for its **value**.
{: ng-show="block32" .description}

```clojure
;; doseq example
(doseq [n (turtle-names)] (forward n 40))
```
</section>

<section>
#### EXERCISE

* Twinkle Little Star (making sounds)
* Turtles Walk (more function study)
</section>

<section>
### Loops in Clojure
<button class="link" ng-model="block51" ng-click="block51=!block51">Intro</button>

> If you have experiences of other languages,
> probably, you will struggle to understand Clojure's loops.
> Loops in Clojure are very different from so-called **for-loop**.
>
> The `loop` function is the closest to the idea of so-called
> for-loop. However, it is actually a recursion.
> The `dotimes` function may be the second closest.
> Clojure has a `for` function, but it is a sequence function like
> `map`. Let's look at these functions.
{: ng-show="block51" .description}
</section>

<section>
#### `loop`
{: .slide_title .slide}

#### <button class="link" ng-model="block61" ng-click="block61=!block61">Details</button>



> Reference:
> [`recur`](http://clojurebridge.github.io/community-docs/docs/clojure/recur/),
> [`loop`](http://clojurebridge.github.io/community-docs/docs/clojure/loop/)
{: ng-show="block61" .description}

```clojure

```
</section>

<section>
#### `dotimes`
{: .slide_title .slide}

#### <button class="link" ng-model="block71" ng-click="block71=!block71">Details</button>

> `if` statements are not limited to testing only one thing. You can
> test multiple conditions using boolean logic. _Boolean logic_ refers
> to combining and changing the results of predicates using `and`,
> `or`, and `not`.
{: ng-show="block71" .description}

</section>

<section>
#### `for`

#### <button class="link" ng-model="block81" ng-click="block81=!block81">Details</button>

> `and`, `or`, and `not` work like other functions (they aren't
> exactly functions, but work like them), so they are in _prefix
> notation_, like we've seen with arithmetic.
{: ng-show="block81" .description}

> Reference:
> [`for`](http://clojurebridge.github.io/community-docs/docs/clojure/for/)
{: ng-show="block81" .description}
</section>
