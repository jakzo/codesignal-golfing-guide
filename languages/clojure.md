# Clojure

## Function Declaration
``` clojure
(def challenge #(* % 2))
(defn challenge [x] (* x 2))

(def challenge #(* %1 %2 %3))
(defn challenge [x y z]
  (+ x y z))
```

## Logging
``` clojure
(defn challenge [x y z]
  (println (* x y) (* y z))
  (+ x y z))
```

## Variables
Values are immutable (cannot be modified) by default, but variables can be rebound.
`atom`s are mutable variables.
``` clojure
(def a 1) ;; a = 1
(def a 2) ;; a rebound to 2 (original value of 1 is not modified)

;; TODO: atom example...
```

## Ranges
``` clojure
;; All ranges are half-open (start inclusive, end exclusive)
(range 5)     ;; (range end) 0 1 2 3 4
(range 2 5)   ;; (range start end) 2 3 4
(range 1 7 2) ;; (range start end step) 1 3 5
```

## Map
``` clojure
;; Example: square each number
(def a [4 7 5])

(map #(* % %) a)
```

## Reduce
``` clojure
;; Example: sum of array
(def a [4 7 5])

(apply + a)  ;; applies each item of `a` to the `+` function `(+ a[0] a[1] ...)`
(reduce + a)
(reduce #(+ %1 %2) a)
(reduce #(+ %1 %2) 0 a)
```
