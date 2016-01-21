# Sum of square of digits

## Problem

Write a function which takes a collection of integers as an argument. Return the count of how many elements are smaller than the sum of their squared component digits. For example: 10 is larger than 1 squared plus 0 squared; whereas 15 is smaller than 1 squared plus 5 squared.

## Solutions

- Clojure

```clojure
(fn [xs]
  (count
    (filter
      (fn [x] (< x (reduce + (map #(* % %) (map (comp read-string str) (str x))))))
      xs)))
```

```clojure
(fn [inp]
  (let [square (fn [x] (* x x))
        cnt-fn (fn  [i]
                 (let [n (map #(Character/digit % 10) (str i))
                       zm (reduce + (map square n))
                       f (if (> zm i) 1 0)]
                   f))]
    (reduce + (map cnt-fn inp))))
```

