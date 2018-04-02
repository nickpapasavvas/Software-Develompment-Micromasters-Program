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


## Week 2

### cond

(define (aspect-ratio img)
  (cond [Q A]
        [Q A]
        [else A]
  )
 )

 ## How to design Data

#### Atomic Data

 ;; CityName is String
 ;; interp. the name of the city
 (define CN1 "Boston")
 (define CN1 "Vancouver")
                 city      cn
 (define (fn-for-type-name x)
 (... cn))

 ;; Template rules used:
 ;; - atomic non-distinct:String

Run the program to test for errors

#### Interval

;; SeatNum is Natural[1,32]
;; interp. seat numbers in a row, 1 and 32 are aisle seats

(define SN1 1)  ;aisle
(define SN2 7)  ;middle
(define SN3 32) ;aisle

(define (fn-for-seat-num sn)
    (... sn)
)

;; Template rules used:
;;  - atomic non distinct : Natural[1,32]

#### Enumaration

;; LetterGrade is one of
;; - A
;; - B
;; - C
;; interp. the letter grade in a course
;; <examples are redundant for enumerations>

(define (fn-for-letter-grade lg)
  (cond [(string=? lg "A" ) (...)]
        [(string=? lg "B" ) (...)]
        [(string=? lg "C" ) (...)]
  )
)

;; Template rules used;
;; - one of: 3 cases  
;; atomic distinct value: "A" 
;; atomic distinct value: "B" 
;; atomic distinct value: "C"  

#### Itemization

;; Countdown is one of:
;;  - false
;;  - Natural[1,10]
;;  - "complete" 
;; interp.
;;      false means countdown has not started yet
;;      Natural[1,10] means countdown is running and how manyseconds left
;;      'complete' means countdown is over
(define CD1 false)  
(define CD2 10)     ;just started
(define CD3 1)      ;almost over
(define CD4 "complete")

(define (fn-for-countdown c)
  (cond [Q A]
        [Q A]
        [Q A]
  )
)

(define (fn-for-countdown c)                         ;; If a given subclass is the last subclass of its type
(cond [(false? c) (...)]                             ;; we can reduce the test to just the guard, ie. (number? c) 
      [(and (number? c) (<= 1 c) (<= c 10) (... c)] --> [(number? c) (... c)]
      [else (...)]
)
)                                                    ;; If all remaining subclasses are of the same type,
                                                     ;; then we can eliminate all of the guards.        


;; Template rules used:
;;  - one of: 3 cases
;;  - atomic distinct: false
;;  - atomic non-distinct: Natural[1,10]
;;  - atomic distinct: "complete"