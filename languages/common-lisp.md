# Common Lisp

## Function Declaration
``` common-lisp
(defun challenge (x y z)
  ...
  (+ x y z))
```

## Logging
``` common-lisp
(defun challenge (x y z)
  (write-line (format nil "~a ~a" (* x y) (* y z)))
  (+ x y z))
```

## Variables
``` common-lisp
(setq a 1)                        ;; 1
(setq a (list (+ x y) (+ y z)))   ;; [x+y, y+z] as list
(setq a #(1 2 x))                 ;; [1, 2, "x"] as vector
(setq a (vector (+ x y) (+ y z))) ;; [x+y, y+z] as vector
```

## Loops
``` common-lisp
-- While
(loop while (!= x y)
      do ...)

-- Range (3 4 5 6 7 8)
(loop for i from 3 to 8 ...)
```
