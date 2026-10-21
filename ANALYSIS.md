# Vector and Scalar Evaluation

## Trace
Given: sample_scores `c(Ada = 8, Grace = NA_real_, Linus = 12, Barbara = 4)`
 
In `clean_scores_vector()`, `out[is.na(out)] <- 0` turns Grace’s NA into 0, then `2*out` makes 16, 0, 24, 8 and `out[out > 20] <- 20` caps Linus to 20.

For `clean_scores_scalar()`, the loop checks and updates one index at a time.1st iteration stores 16 for Ada. 2nd iteration accesses Grace's `NA`, stores 0, and skips the doubling. 3rd iteration doubles Linus to 24, then caps it at 20. The last pass stores 8 for Barbara. 

Both return `c(Ada = 16, Grace = 0, Linus = 20, Barbara = 8)` including the names to show that both work to give the same output but with differing processes. 

## 1.
Under `clean_scores_vector()`, three expressions each act on the entirety of the vector. First, `out[is.na(out)] <- 0` is a guard check that replaces every missing score in a single sweep; that's why Grace's `NA` becomes 0 without ever explicitly calling index 2. Then, `out * 2` doubles all four elements' values together. And lastly, `out[out > 20] <- 20` caps those values greater than 20, and only Linus's 24 is manipulated back to 20.

## 2.
In `clean_scores_scalar()`, the `for` loop iterates through elements one by one. Grace is accessed on the second iteration, where `is.na(out[[i]])` returns TRUE, so it stores 0 and ignores the doubling. On the third pass, Linus is accessed, where its value doubles to 24 just for the inner `if` condition to cap it at 20. Since every line can be stopped by a debugger through iterating through it all, the order is therefore visible.

## 3.
R recycles a short logical index to match the length of a longer vector. If we wrote `out[is.na(out[1:2])] <- 0`, the mask would be c(FALSE, TRUE), which R would recycle to c(FALSE, TRUE, FALSE, TRUE). This would zero both Barbara and Grace, when Barbara should remain 8. The result would be  `c(Ada = 16, Grace = 0, Linus = 20, Barbara = 0)`, with no error raised. `clean_scores_scalar()` avoids this mistake, since it reads and updates one out[[i]] at a time.

## 4.
We would keep `clean_scores_vector()` since it is shorter and potentially faster on long inputs because of R’s built-in operations on entire vectors. However, incorrect masks and operation order can cause errors, which fall silent. Meanwhile, `clean_scores_scalar()` is easier to debug, but it costs speed and length, so we accept the vectorized approach’s risks and mitigate them through testing.