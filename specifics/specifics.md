!SLIDE

# Specifics

!SLIDE

# 2 Steps we specify

## Map

### Process single piece of data independently

## Reduce

### Combine the pieces of data

!SLIDE

# Count Words

## Map

### (name:document)->list(word:1)

## Reduce

### (word:list(1,1,1...)) -> (word:count)

!SLIDE

# Count Words

     @@@python
     void map(String name, String document):
       // name: document name
       // document: document contents
       for each word w in document:
         EmitIntermediate(w, "1");

     void reduce(String word,
                 Iterator partialCounts):
       // word: a word
       // partialCounts: a list of partial counts
       int result = 0;
       for each pc in partialCounts:
         result += ParseInt(pc);
       Emit(AsString(result));

!SLIDE

# Often need several MapReduce tasks in sequence

## Example

!SLIDE

## Start with file that has the temperature of each day

## Want to find the year with highest average temperature

!SLIDE

# First

## Map

### "day month year: temperature" -> (year, value)

## Reduce

## (year, list(value,value,...)) -> (year, average of values)

!SLIDE

# Second

## Map

### (year, average of values) -> (year, average of values)

## Reduce

### (year, average of values) -> keep it if it's the max



!SLIDE