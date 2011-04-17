!SLIDE

# Specifics

!SLIDE

# 2 Steps we specify

## Map

### Process single piece of data independently

## Reduce

### Combine the pieces of data

!SLIDE

# Map

## Process one piece of data at a time

## Can't be based on any other data

### (key:value)->[(key1:value1), (key1:value1), ...]

!SLIDE

# Reduce

## Combine Pieces of Data

## Reducer Gets All Values for a Given Key at Once

### (key:[value1,value2,value3])->[(key:value)]

!SLIDE

# Count Words

## Map

### (identifier:text)->[(word1:1),(word2:1),...]

## Reduce

### (word:[1,1,1...]) -> (word:count)

!SLIDE

# Count Words Example

## Map

### (in->out)

### (identifier:text)->[(word1:1),(word2:1),...]

### ("mr.txt":"hello map reduce! I like map reduce") -> [(hello:1), (map:1), ...]

## Reduce

### (word:[1,1,1...]) -> (word:count)

### ("hello":[1]) -> ("hello":1)

### ("map":[1,1]) -> ("map":2)

!SLIDE

# Often need several MapReduce tasks in sequence

## Example

!SLIDE

## Have every individual grade (each test, homework, etc) for every student

## Want to find their final grade

## Compute final grade by computing marking period grade, then averaging marking periods

!SLIDE bullets incremental

# Map 1

* (grade-id:"student id, marking period, points, possible points")->
* (student-id+marking-period:[points, possible points])

!SLIDE bullets incremental

# Reduce 1

* (student-id+marking-period:[[points1, possible points1],[points2, possible points2],...])->
* (student-id+marking-period:average)

!SLIDE bullets incremental

# Map 2

* (student-id+marking-period:average)->
* (student-id:average)

!SLIDE bullets incremental

# Reduce 2

* (student-id:average)->
* (student-id:final grade)

!SLIDE bullets

# PageRank

* More important pages are linked to more
* Value of a link is proportional to the PageRank of the linking page

!SLIDE center

![PageRank](pagerank.png)

!SLIDE bullets

# Problem

* Chicken-egg
* PageRank of a page depends on the PageRank of every page linking to it

!SLIDE bullets

# Solution

* First MapReduce run assembles the graph (what links to what?)
* Then, assume all have same PR
* Repeatedly run more MapReduce runs that adjust the values
* It will converge on the true values

!SLIDE

# Want to Use It?

## Hadoop

## Cloudera

## Amazon Elastic Map Reduce (or just EC2)

## Scripts

    $ cat input.txt | ./map | sort | ./reduce

!SLIDE

# Thank You

## These Slides:

## github.com/jackowayed/map-reduce-intro/
    
