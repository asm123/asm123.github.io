---
layout: post
date: 2024-04-28
title: "Book notes - \"Algorithms to Live By: The Computer Science of Human Decisions\""
tags: book-notes science
last_updated: 2024-05-12
status: budding
---

Book: [Algorithms to Live By: The Computer Science of Human Decisions](https://www.goodreads.com/book/show/25666050-algorithms-to-live-by)
* Author: Brian Christian, Tom Griffiths
* Published in: 2016

## Official Summary

> What should we do, or leave undone, in a day or a lifetime? How much messiness should we accept? What balance of the new and familiar is the most fulfilling? These may seem like uniquely human quandaries, but they are not. Computers, like us, confront limited space and time, so computer scientists have been grappling with similar problems for decades. And the solutions they’ve found have much to teach us.
> 
> In a dazzlingly interdisciplinary work, Brian Christian and Tom Griffiths show how algorithms developed for computers also untangle very human questions. They explain how to have better hunches and when to leave things to chance, how to deal with overwhelming choices and how best to connect with others. From finding a spouse to finding a parking spot, from organizing one’s inbox to peering into the future, _Algorithms to Live By_ transforms the wisdom of computer science into strategies for human living.

--- From [book website](https://algorithmstoliveby.com/#aboutthebook)


## Chapter notes

* [Chapter 3: Sorting - Making Order](#chapter-3-sorting---making-order)
* [Chapter 4: Caching - Forget About It](#chapter-4-caching---forget-about-it)

## Chapter 3: Sorting - Making Order

- StackOverflow has an over [12k word debate]((https://stackoverflow.com/questions/14415881/how-can-i-pair-socks-from-a-pile-efficiently)) over pairing socks from a pile efficiently.
- Sorting is at the very heart of what computers do.
- The ecstacy of sorting:
	- Herman Hollerith devised a machine that was used in 1890 US census. This was the first sorting machine. Hollerith's firm eventually became IBM.
	- The first code ever written for a stored program was for efficient sorting.
	- Sorting is a useful form to human eyes.
	- Search engines are really sort engines.
- The agony of sorting:
  - With sorting, size is a recipe for disaster. The first and most fundamental insight of sorting theory: scale hurts. Minimize the number of things to sort to minimize the suffering.
  - Record for sorting a deck of 52 cards is 36.16 seconds.
  - Unlike races, computer science almost never cares about the best case scenario. It wants to know the average and worst case times.  
- Big-O notation provides a way to talk about the kind of relationship that holds between the size of the problem and the program's running time.
  - O(1) - constant time - time required to clean the house regardless of how many guests are arriving.
  - O(n) - linear time - time required to pass a dish around the table seating n guests.
  - O(n^2) - quadratic time - time required for all the n guests to hug each other.
  - O(2^n) - exponential time - each additional guest doubles your work.
  - O(n!) - factorial time - time required to shuffle a deck of cards until it is sorted.
- The squares:
	- Bubble sort:
	    - [Barack Obama apparently knows about bubble sort!](https://youtu.be/koMpGeZpu4Q)
	    - Simple, intuitive and extremely inefficient.
	    - n books out of order, scan across the shelf looking for out of order pairs and flipping them around.
	- Insertion sort:
		- More intuitive than bubble sort, still inefficient.
		- Pull all the books off the shelf, put them back in place one-by-one by comparing the booking put with books already placed and inserting at its correct place.
- Breaking the quadratic barrier with divide and conquer:
	- IBM produced a line of "collator" machines that merged two separately sorted stacks into one.
	- John von Neumann extended this idea to fully sort an ordered stack - Mergesort!
		- Collate a pair of two-card stacks -> collate then into an ordered stack of 4 -> keep building bigger stacks until only one stack remains.
		- O(n log n) - linearithmic time!
- Beyond comparison: outsmarting the logarithms:
  - New York and Brooklyn Public Libraries compete with Washington's King County Library (Preston Sort Center) in mechanical book sorting. Preston Sort Center sorts the books in O(n) time with Bucket sort.
  - Bucket sort groups items together in a number of sorted categories, intracategory sorting comes later if required.
	* As long as the number of buckets m is relatively small compared to the number of items n, time required is O(n).
	* Most beneficial if buckets are chosen based on the distribution of the items to be sorted.

- Sort is prophylaxis for search
  - One of the most central tradeoffs in computer science is between sorting and searching.
  - Sorting is valuable only to support future search. Sorting something you will never search is a complete waste; searching something you never sorted is merely inefficient.
  - Search engines sort results up-front.
  

- Types of tournaments in sports dependent on sorting and searching - single elimination, round-robin, ladder.

- Comparison counting sort:
  - Each item is compared to all the others, generating a tally of how many items it is bigger than. This tally is used as its rank.
    - Most robust sorting algorithm known. Robustness = reliable.
    - Round-robin sports tournaments.

- Blood sort
  - Decentralized sorting: pecking order, animal behaviour, dominance hierarchies.
  - Displacement - when an animal uses its knowledge of the hierarchy to determine that a particular confrontation simply isn't worth it.

> Much as we bemoan the daily rat race, the fact that it's a race rather than a fight is a key part of what sets us apart from the monkeys, the chickens - and for that matter, the rats.


## Chapter 4: Caching - Forget About It

> In the practical use of our intellect, forgetting is as important a function as recollecting.
> 
> --- William James

* The memory hierarchy:
	* Tradeoff between size and speed.
	* Arthur Burks, Herman Goldstine and Jon von Neumann proposed a hierarchy of memories in 1946, each of which has a greater capacity than preceding but is less quickly accessible - to achieve the best of both size and speed.
		* Analogous to using a library for research. Bring home the books you need from library, go back to library only when need another book not already brought home.
	* A supercomputer called Atlas in Manchester used a larger principal memory and a smaller, faster working memory in 1962 - first implementation of the memory hierarchy concept.
	* Maurice Wilkes proposed using the smaller, faster memory to hold information likely needed later - implemented by IBM in 1960s as "cache".
	* Computer science has caches everywhere - processor, OS, HDD, web browsers.
	* Memory wall: Number of transistors in CPUs would double every two years according to Moore's Law, but the performance of memory hasn't kept pace with this rate.
		* Current solution: six layered memory hierarchy.
* Eviction and clairvoyance:
	* How to make room when a cache fills up?
	* Minimize the page fault or cache misses - number of times you have to go to the slower main memory when you can't find what you are looking for in the cache.
	* Bélády's Algorithm: evict whichever item we'll need again the longest from now.
		* Clairvoyant - informed by data from the future. Hard to come by.
	* Random eviction: randomness is not too bad.
	* First-in, first-out (FIFO)
	* Least recently used (LRU): 
		* Next thing we expect to need is the last one we needed, last thing we expect to need is the one we've already gone the longest without.
		* Consistently performs closest to clairvoyance due to the principle of temporal locality - something needed now is likely needed again in the near future.
		* Quite common: applications listed in order of use in GUI-based OS, library system, [Noguchi Filing System](https://fernandogros.com/the-noguchi-filing-system/).

> Our best guide to the future is a mirror image of the past. The nearest thing to clairvoyance is to assume that history repeats itself - backwards.

* A quarter of all Internet traffic at present is handled by Akamai with Content Distribution Networks (CDN).
	* Caching webpage content that is physically, geographically closer to the people who want it by keeping copies of the content on computers all across the world.
* Amazon's fulfillment centers place incoming items anywhere they find a place, but high demand items are kept together.

* The forgetting curve:
  * Hermann Ebbinghaus formally started the science of human memory in 1879 by performing memory experiments on himself.
  * Ebbinghaus established many of the most basic results in human memory research, including [the forgetting curve](https://elearningindustry.com/forgetting-curve-combat) - a graph of how memory fades over time.
  * According to John Anderson's theory, mind has infinite capacity to store information, but finite time to search through it, which leads to forgetting.
  * The key to a good human memory is predicting which items are most likely to be wanted in future.
  * Reality itself has a statistical structure that mimics the Ebbinghaus curve - the pattern by which things fade from our minds is the very pattern by which things fade from use around us.
  * Cognitive decline may not be about the search process slowing or deteriorating, but having to navigate bigger information as we age.
    * The length of a delay is partly an indicator of the extent of your experience.

> The disproportionate occasional lags in information retrieval are a reminder of just how much we benefit the rest of the time by having what we need at the front of our minds.
