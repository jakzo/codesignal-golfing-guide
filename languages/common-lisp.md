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
(setq a 1)         ;; 1
(setq a #(1 2 3)) ;; [1, 2, 3]
```

## Loops
``` common-lisp
-- While
(loop while (!= x y)
      do ...)

-- Range (3 4 5 6 7 8)
(loop for TODO)
```
