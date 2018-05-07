---

layout: post
title: "Primes in Ruby"
---

![26/366 Discrete Mathematical Structures](http://tech.karbassi.com/images/posts/2008-09-10/discrete.jpg "26/366 Discrete Mathematical Structures"):http://www.flickr.com/photos/10324788@N03/2227014216/

While working on some homework for a mathematics course, I ran into a problem; I needed a list of primes. I could manually produce a list of 10, maybe 20 primes but what's the fun in that. Having my trusty MacBook near me, I loaded up TextMate and started to write a simple Ruby program to produce primes.

After a few minutes, the code turned into something much bigger than I expected. Researching to see if my formulas were correct, I continued on to create a separate file for this class. The outcome produced this:

```ruby
class Primes
attr\_reader :primes

def initialize(len = nil)
return nil if len.nil?

state = Numeric.new
@primes = \[2, 3\]

i = 4
count = 0
while count \< len.abs - 2
(2..(Math.sqrt(i).ceil)).each do
|x|
state = true
if (i.divmod(x)\[1\] == 0)
state = false
break
end
end

if state
@primes \<\< i
count +=1
end
i += 1
end

return @primes
end
end
```

To run, we do:

```ruby
p = Primes.new(10)
puts p.primes

1.  Output
2.  ———
3.  2
4.  3
5.  5
6.  7
7.  11
8.  13
9.  17
10. 19
11. 23
12. 29
    ```

I know this isn't perfect, but it was a fun 20 minute side project. If you want to improve on it, just head over to my [gist](http://gist.github.com/10159) "Ruby class to return primes".
