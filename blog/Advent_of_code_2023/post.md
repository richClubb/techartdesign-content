# Advent of code 2023

TLDR: See the github repo [AoC](https://github.com/richClubb/adventofcode)

I try to do Advent of Code every year but it usually gets sidelined. In 2023 I set myself the task of doing it in Python, Rust and Zig to expose myself to new languages and play around with the idiomatic way to do things in different languages.

I started well and got to day 5 but then I got distracted by some fun.

Day 05 is a great example of a AoC problem. Part A introduces a pretty basic problem, but Part B blows the trivial solution out of the water by just increasing the search space by orders of magnitude.

In a nutshell the problem is this. You start with an initial value, and a series of mappings. You have to put the value through the mappings and then find the lowest value, that's your answer.

Part A starts out with 14 values so it's pretty quick, Part B changes this to pairs, so you have a start value and a size. This means that instead of 14 values you have 4,000,000,000.

## Brute Force

Using the basic brute force approach for Part B was pretty silly. On the original Python implementation it was taking many hours which wasn't really a 'good' solution, so I thought of doing it in parallel. 

It was pretty easy to rewrite to use multiprocessing pools which was a pretty linear improvement based on the number of cores in the system. 8 cores made it about 8 times faster.

The Rust implementation was a similar speed improvement, it was orders of magnitude faster just out of the box, and using the `par_iter` function had a similar improvement in speed to python.

It was still taking many minutes which was not ideal

## Calculating the ranges

It was pretty easy to figure out that it should be possible to translate the entire range through the mappings and this would reduce it from 4,000,000,000 back down to a small number of operations.

TLDR, this approach took the python implementation down from hours to less than 1 second.

## Functional Programming

I was playing around with F# and tried to solve the problem fully functionally, but it ended up being a bit of an issue.

Using the brute force method it would use about 16 gig of RAM just to compute the input and output vectors using `map`, so coding tit imperatively was the only way I figured out how to solve the problem. Still trying to figure out if there is a nicer way to do it.

# Conclusion

I did a proper [write up](https://github.com/richClubb/adventofcode/blob/main/2023/day05/Day%205%20notes.md) which I presented at work as an education session at work.

I'll fill this out when I've got more time, but this ended up being a really good problem to solve in different ways. These kind of experiments are just what you need sometimes to blow out the cobwebs. It's why things like AoC and Leet Code can be useful learning experiences. You set yourself challenges to go along with the inherent challenge of the problem. Try solving it in a new language, or just using recursive functions, or using functional programming techniques.

For 2024 I'm going to try doing the same kind of thing but probably focus on doing it in Rust first where possible. I really want to get better at Rust as it does look to be the successor to C.

## To-do

* Solve day 05 in Zig (just for giggles) to see how the brute force compares to Rust.
* Solve day 05 in C to see how it compares in speed to Rust.
