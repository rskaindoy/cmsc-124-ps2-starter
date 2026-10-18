# Reasoning Before Execution

Write the rule behind each case before you commit your predictions. Replace
every placeholder line below with one to three sentences that name the rule
producing that case's value, type, length, and dimensions. One rule is enough.
After you run and find a miss, add a short correction entry under that case in a
later commit.

## P01
The coercion ladder runs logical, integer, double, character. The third value is a double, so the case’s type is double, with TRUE becoming double 1 and 5L becoming 5. The value is [1, 2, 3.5] with length three and no dimensions.

## P02
Following the coercion ladder runs logical, integer, double, character, the case’s type becomes character because of the second argument “2”. Hence, 1L and TRUE become characters, with “1” and  “TRUE” as their respective values. The value is [“1”,“2”,“TRUE”] with length three and no dimensions.

## P03
Since all the arguments are integers, the case type is integer. Recycling is used since a 2-element vector is added to a 4-element vector, repeating the 2-element vector twice, so 1 is added to 10 and 30, and 2 is added to 20 and 40. Thus, the value is [11,22,31,42] with length 4 and no dimensions.

## P04
The values are written with L, so the type is integer, and the names attached to each value are just labels, which doesn’t change the storage type. The positions requested are 3 and 1, which get the third and first values respectively, along with their attached name in the order when it was requested. Hence, the value is [third = 9,first = 8] with length 2 and no dimensions.

## P05
The values are written with L, so the type is integer. The negative index 2 indicates to exclude the value in that index, so it returns only the values in index 1 and 3, which are 4 and 9 respectively. Hence, the value is [4,9] with length 2 and no dimensions.

## P06
Since the values are written with L and NA_integer_ creates a missing integer value, the type is integer. R binds the 4 integers to vector x, then evaluates the conditions to get the index of which either condition results to TRUE due to the logical operator |. The condition is.na(x) evaluates TRUE for the second element only, while the condition x>10 evaluates TRUE for the third element only, hence, the value is [NA,12] with length 2 and no dimensions.

## P07
The type that typeof() gives  is integer instead of characters, because factor actually stores each element as an integer based on their order in levels, not as strings. Here, levels specify that low is level 1 and high is level 2, so the stored values are 1 2 1, and these are the top-level elements so length is 3. Hence, the value is factor[low,high,low];levels=[low,high] with length 3 and no dimensions.

## P08
The top-level elements here are two, namely scores and label, thus it has a length of 2. R’s list can have components of different types, so typeof() will just return “list”. Hence, the value is list{scores=[3, 5],label=["A"]} with length 2 and no dimensions.

## P09
Replace this line with the rule that decides this case.

## P10
Replace this line with the rule that decides this case.

## P11
Replace this line with the rule that decides this case.

## P12
Replace this line with the rule that decides this case.

## P13
Replace this line with the rule that decides this case.

## P14
Replace this line with the rule that decides this case.

## P15
Replace this line with the rule that decides this case.

## P16
Replace this line with the rule that decides this case.
