# Vector and Scalar Evaluation

Replace this paragraph after your checks pass. Trace one input, including the
missing value, through `clean_scores_vector()` and `clean_scores_scalar()`.
Compare the two evaluation models, identify where recycling would change the
answer, and explain which implementation you would keep in an R program.

## Trace
Given: sample_scores `c(Ada = 8, Grace = NA_real_, Linus = 12, Barbara = 4)`
 
In `clean_scores_vector()`, `out[is.na(out)] <- 0` turns Grace’s NA into 0, then `2*out` makes 16, 0, 24, 8 and `out[out > 20] <- 20` caps Linus to 20.
In `clean_scores_scalar()`, the loop reaches Grace on pass 2, where `is.na(value)` is TRUE, so `out[[2]] <- 0` runs and the doubling is skipped. 
Both return `c(Ada = 16, Grace = 0, Linus = 20, Barbara = 8)`. 

## 1.

## 2.

## 3.
R recycles a short logical index to match the length of a longer vector. If we wrote `out[is.na(out[1:2])] <- 0`, the mask would be c(FALSE, TRUE), which R would recycle to c(FALSE, TRUE, FALSE, TRUE). This would zero both Barbara and Grace, when Barbara should remain 8. The result would be  `c(Ada = 16, Grace = 0, Linus = 20, Barbara = 0)`, with no error raised. `clean_scores_scalar()` avoids this mistake, since it reads and updates one out[[i]] at a time.

## 4.
We would keep `clean_scores_vector()` since it is shorter and potentially faster on long inputs because of R’s built-in operations on entire vectors. However, incorrect masks and operation order can cause errors, which fall silent. Meanwhile, `clean_scores_scalar()` is easier to debug, but it costs speed and length, so we accept the vectorized approach’s risks and mitigate them through testing.