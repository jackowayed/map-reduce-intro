!SLIDE

# Map & Reduce

## Functions that exist in a number of languages

## Especially "functional languages"

## Inspired MapReduce

!SLIDE

# Map

## Apply function to every element of array/list

    @@@ruby
    [1,2,3,4,5].map(square)
    # [square(1), square(2), square(3), ...]
    # [1,4,9,16,25]

## Has forms that take several parameters

    @@@ruby
    Map(max, [1, 7, -3, 2, 8],
             [6, 4, 0, 4, -4])
           # [6, 7, 0, 4, 8]

!SLIDE

# Map

    @@@ruby
    [1,2,3,4,5].map(square)
    # [1,4,9,16,25]

## Note: square(2) doesn't depend on square(1)

## Opportunity to parallelize

!SLIDE

# Reduce

## Combine a list/array 

## Function takes 2 parameters and returns 1

    @@@ruby
    [1,2,3,4,5].reduce(+)
    ((((1 + 2) + 3) + 4) + 5) #15

!SLIDE

# Reduce

    @@@ruby
    [1,2,3,4,5].reduce(+)
    ((((1 + 2) + 3) + 4) + 5) #15

## In this case, could parallelize

    @@@ruby
    ((((1 + 2) + 3) + 4) + 5)
    == ((1+2) + (3 + 4) + 5)

## But not always