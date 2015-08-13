# How To Walk Turtles 

Here are some basic instructions to walk turtles.
Walk them and draw lines by your imagination!

#### 0. Before getting started

- initial state

![initial state](img/initial-state.png)


See [TURTLE.md](TURTLE.md) for commands that turtles understand.


- `undo`, `clean`, and `home`

When the turtle has gone unexpectedly long or short distance, we can delete the
line one by one using `undo`.
If the turtle should start from its initial state,
a combination of `clean` and `home` commands make the turtle back to
the home position.

- `init`

When you messed up turtles' move and want to start over from the
initial state, use `init` command.

- `state`

When the turtle goes far away beyond the boundary, or you lost which
one is what, you can check where they are by this command. The command
returns absolute values.

[note] The `forward`/`backward` or `right`/`left` commands take a
relative value to the current state.

- `doc`

Without looking at command reference, we can check how to use each
function by Clojure's `doc`. For examples, `(doc forward)` displays
its usage.


#### 1. Basic movement - forward, backward, right and left

- forward

```clojure
clojurebridge-turtle.walk=> (forward 40)
{:trinity {:length 40}}
```

![forward 40](img/forward40.png)


- right

```clojure
clojurebridge-turtle.walk=> (right 90)
{:trinity {:angle 90}}
```

![right 90](img/right90.png)

- combinations of forward and right

```clojure
clojurebridge-turtle.walk=> (forward 40)
{:trinity {:length 40}}
clojurebridge-turtle.walk=> (right 90)
{:trinity {:angle 90}}
clojurebridge-turtle.walk=> (forward 50)
{:trinity {:length 50}}
clojurebridge-turtle.walk=> (right 90)
{:trinity {:angle 90}}
clojurebridge-turtle.walk=> (forward 60)
{:trinity {:length 60}}
clojurebridge-turtle.walk=> (right 90)
{:trinity {:angle 90}}
clojurebridge-turtle.walk=> (forward 70)
{:trinity {:length 70}}
clojurebridge-turtle.walk=> (right 90)
{:trinity {:angle 90}}
clojurebridge-turtle.walk=> (forward 80)
{:trinity {:length 80}}
```

![combination](img/forwardsandrights.png)


- combination of various commands

```clojure
clojurebridge-turtle.walk=> (init)
:trinity
clojurebridge-turtle.walk=> (forward 50)
{:trinity {:length 50}}
clojurebridge-turtle.walk=> (right 45)
{:trinity {:angle 45}}
clojurebridge-turtle.walk=> (backward 100)
{:trinity {:length -100}}
clojurebridge-turtle.walk=> (left 45)
{:trinity {:angle -45}}
clojurebridge-turtle.walk=> (forward 50)
{:trinity {:length 50}}
clojurebridge-turtle.walk=> (state)
{:trinity {:x -70.71068094436272, :y 29.289320335914155, :angle 90, :color [30 30 30]}}
```

![movement sample](img/various-combination.png)



#### 2. Multiple turtles

- add turtles

```clojure
clojurebridge-turtle.walk=> (init)
:trinity
clojurebridge-turtle.walk=> (add-turtle)
{:smith0 {:x 0, :y 0, :angle 90, :color [10 107 30]}}
clojurebridge-turtle.walk=> (add-turtle)
{:smith1 {:x 0, :y 0, :angle 90, :color [10 107 30]}}
clojurebridge-turtle.walk=> (add-turtle)
{:smith2 {:x 0, :y 0, :angle 90, :color [10 107 30]}}
clojurebridge-turtle.walk=> (turtle-names)
[:trinity :smith0 :smith1 :smith2]
```

![four turtles](img/four-turtles.png)

- make smiths tilt different angles

```clojure
clojurebridge-turtle.walk=> (right :smith0 (* 1 45))
{:smith0 {:angle 45}}
clojurebridge-turtle.walk=> (right :smith1 (* 2 45))
{:smith1 {:angle 90}}
clojurebridge-turtle.walk=> (right :smith2 (* 3 45))
{:smith2 {:angle 135}}
```

![four directions](img/four-directions.png)

- walk four turtles forward

```clojure
clojurebridge-turtle.walk=> (forward :trinity 40)
{:trinity {:length 40}}
clojurebridge-turtle.walk=> (forward :smith0 40)
{:smith0 {:length 40}}
clojurebridge-turtle.walk=> (forward :smith1 40)
{:smith1 {:length 40}}
clojurebridge-turtle.walk=> (forward :smith2 40)
{:smith2 {:length 40}}
```

![four moves](img/four-forwards.png)



License
-------
<a rel="license"
href="http://creativecommons.org/licenses/by/4.0/deed.en_US"><img
alt="Creative Commons License" style="border-width:0"
src="http://i.creativecommons.org/l/by/4.0/88x31.png" /></a><br
/><span xmlns:dct="http://purl.org/dc/terms/"
href="http://purl.org/dc/dcmitype/Text" property="dct:title"
rel="dct:type">ClojureBridge Curriculum</span> by <span
xmlns:cc="http://creativecommons.org/ns#"
property="cc:attributionName">ClojureBridge</span> is licensed under a
<a rel="license"
href="http://creativecommons.org/licenses/by/4.0/deed.en_US">Creative
Commons Attribution 4.0 International License</a>.
