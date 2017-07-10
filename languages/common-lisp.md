# Common Lisp

## Function Declaration
``` common-lisp
(defun challenge (x y z)
  (+ x y z))
```

## Logging
``` common-lisp
(defun challenge (x y z)
  (write-line (format nil "~a ~a" (* x y) (* y z)))
  (+ x y z))
```
