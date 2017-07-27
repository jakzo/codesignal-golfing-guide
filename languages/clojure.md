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

## Reduce
``` clojure
(def a [4 7 5])

;; Example: sum of array
(apply + a)  ;; 9 chars
(reduce + a) ;; 10 chars

;; Example: double each item and sum
(apply + (map #(* % 2) a))    ;; 20 chars
(reduce #(+ %1 (* %2 2)) 0 a) ;; 22 chars
```
