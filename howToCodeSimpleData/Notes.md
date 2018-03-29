[Link to Dr. Racket](http://racket-lang.org/download/)

(string-append "Ada" " " "Lovelace" )
(string-length "apple")
(substring "Caribou" 2 4)
(require 2htdp/image)
(circle 10 "solid" "red")
(rectangle 30 60 "outline" "blue")
(text "hello" 24 "orange")
(above
(circle 10 "solid" "red")
(circle 20 "solid" "blue")
(circle 30 "solid" "orange")
)
above, beside, overlay

(define WIDTH 400)
(define CAT "cat.jpg")
(rotate -10 CAT)
(rotate 10 CAT)

;(define RCAT (rotate -10 CAT))
;(define LCAT (rotate 10 CAT))

### Functions

(above
(circle 30 "solid" "red")
(circle 30 "solid" "yellow")
(circle 30 "solid" "green")
)

(define (bulb c)
(circle 30 "solid" c))

(above (bulb "red")(bulb "yellow")(bulb "green"))

### Booleans

(define WIDTH 400)
(define HEIGHT 400)

(> WIDTH HEIGHT) --> false
(>= WIDTH HEIGHT) --> true

(string=? "foo" "bar") --> false

(define I1 (rectangle 10 20 "outline" "blue"))
(define I2 (rectangle 20 10 "solid" "blue"))

(require 2htdp/image)
(< (image-width I1)
(image-width I2)) --> true

### if

(if (< (image-width I1)
(image-height I1))
"tall"
"wide")

(and (> (image-height I1) (image-height I2))
(> (image-width I1) (image-width I2))
)

## How to design Functions

1.  Function signature
2.  Function purpose:
    A purpose statement should describe what result is produced and how that is based on the argument(s).
3.  Write stub
4.  Write tests (check-expect)
5.  Run the tests and see them run but fail
6.  Inventory - table && constants
7.  Code body
8.  Test and debug
