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
data.frame is a list of columns(id) x list of rows(passed), so typeof is list and length is 2. Dimensions are 2 rows x 2 columns since each column has two elements. Thus, dim is 2x2.

## P10
Matrix is stored by columns, so `matrix(1:6, nrow = 2L) holds 1,2,3,4,5,6. Since nrow = 2, add the first 2 elements with their corresponding order in the second vector. Recycle rule in c(10L,20L) adds 10 and 20 to elements alternately; add 10 to 1,3,5 and add 20 to 2,4,6.

## P11
Using a mean with an argument of NA by itself alone returns NA, a special case with length 1. Annihilating the other values and deeming them irrelevant since NA overrides. Therefore, [NA] is the result, with length 1 and no dimensions.

## P12
Since this time na.rm = TRUE(ignores missing values; na.rm = FALSE by default)
It technically becomes quote(mean(c(8,9))). Type is double to avoid precision loss, generalized for all cases, even when the mean should’ve been an int.

## P13
Reassigning a double value type to index 2(R is 1-indexed) changes the other values to double due to coercion from int >double. Mixed-mode assignment widens the vector to double to accommodate the reassignment. This also makes the other values double with length 3 and no dimensions.

## P14
is.na(scores) returns FALSE, TRUE, FALSE, TRUE. If true, set the value to 0; otherwise, double it. And for those values greater than 15, set their value to 15, giving [1,2.5,3], type double, length 3, no dimensions.

## P15
An array of atomic vector with dim as its attribute. 1:8 indicates the type, which is an integer of length 8, and the c(2L,2L,2L) shows how it is being stored. Thus, the dim is 2x2x2.

## P16
R is 1-indexed, so selecting an integer from that vector returns a zero-length vector with the original type, integer. 