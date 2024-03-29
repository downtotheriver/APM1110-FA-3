APM1110 - FA 3 - Dacanay
================
Jordan Dacanay

### 2) A binary communication channel carries data as one of two sets of signals denoted by 0 and 1. Owing to noise, a transmitted 0 is sometimes received as a 1, and a transmitted 1 is sometimes received as a 0. For a given channel, it can be assumed that a transmitted 0 is correctly received with probability 0.95, and a transmitted 1 is correctly received with probability 0.75. Also, 70% of all messages are transmitted as a 0. If a signal is sent, determine the probability that:

### (a) a 1 was received;

#### First, let t1 be the event that a one is transmitted. Second, let r1_t1 be the event that a one is received given that one is transmitted. Thirdly, let t0 be the event that a zero is transmitted. Lastly, let r1_t0 be the event that a zero is transmitted given that zero is transmitted.

``` r
t1 <- 0.3
r1_t1 <- 0.75
t0 <- 0.7
r1_t0 <- 0.05

p_r1 <- (t1 * r1_t1) + (t0 * r1_t0)
```

#### ANSWER

``` r
print(paste0("The probability that a 1 was received is ", p_r1, " or ", p_r1 * 100, "%."))
```

    ## [1] "The probability that a 1 was received is 0.26 or 26%."

### (b) a 1 was transmitted given that a 1 was received.

#### In this problem, we’ll use all the data provided in Section 2.a. Additionally, we’ll include the ‘p_r1’, which represents probability that a 1 was received.

``` r
p_t1_r1 <- (t1 * r1_t1) / p_r1
p_t1_r1_rounded <- round(p_t1_r1, 4)
```

#### ANSWER

``` r
print(paste0("The probability that a 1 was transmitted given that a 1 was received is ", p_t1_r1_rounded, " or ", p_t1_r1_rounded * 100, "%."))
```

    ## [1] "The probability that a 1 was transmitted given that a 1 was received is 0.8654 or 86.54%."

### 7) There are three employees working at an IT company: Jane, Amy, and Ava, doing 10%, 30%, and 60% of the programming, respectively. 8% of Jane’s work, 5% of Amy’s work, and just 1% of Ava‘s work is in error.

### (a) What is the overall percentage of error?

#### Let j be the event of Jane’s work percentage, am be the event of Amy’s work percentage, and av be the event of Ava’s work percentage. Additionally, let j_e be the event of error in Jane’s work, am_e be the event of error in Amy’s work, and av_e be the event of error in Ava’s work.

``` r
j <- 0.1
am <- 0.3
av <- 0.6

j_e <- 0.08
am_e <- 0.05
av_e <- 0.01


p_e <- (j * j_e) + (am * am_e) + (av * av_e)
p_e_percentage <- p_e * 100
```

#### ANSWER

``` r
print(paste0("The overall percentage of error is ", p_e_percentage, "%."))
```

    ## [1] "The overall percentage of error is 2.9%."

### (b) If a program is found with an error, who is the most likely person to have written it?

#### In this problem, we’ll use all the data provided in Section 7.a. Additionally, we’ll include the ‘p_e_percentage’, which represents the overall percentage of error, as part of our given information.

#### Let’s find out first the percentage of each employee’s error given that an error has occurred.

``` r
# Jane
p_je_oe <- (j * j_e) / p_e
p_je_oe_rounded <- round(p_je_oe, 3)
p_je_oe_rounded_percentage <- p_je_oe_rounded * 100

print(paste0("Jane's error given that an error occurred: ", p_je_oe_rounded, " or ", p_je_oe_rounded_percentage, "%"))
```

    ## [1] "Jane's error given that an error occurred: 0.276 or 27.6%"

``` r
# Amy
p_ame_oe <- (am * am_e) / p_e
p_ame_oe_rounded <- round(p_ame_oe, 3)
p_ame_oe_rounded_percentage <- p_ame_oe_rounded * 100
print(paste0("Amy's error given that an error occurred: ", p_ame_oe_rounded, " or ", p_ame_oe_rounded_percentage, "%"))
```

    ## [1] "Amy's error given that an error occurred: 0.517 or 51.7%"

``` r
# Ava
p_ave_oe <- (av * av_e) / p_e
p_ave_oe_rounded <- round(p_ave_oe, 3)
p_ave_oe_rounded_percentage <- p_ave_oe_rounded * 100
print(paste0("Ava's error given that an error occurred: ", p_ave_oe_rounded, " or ", p_ave_oe_rounded_percentage, "%"))
```

    ## [1] "Ava's error given that an error occurred: 0.207 or 20.7%"

#### ANSWER

``` r
# Compare probabilities and print the most likely person
if (p_je_oe_rounded_percentage > p_ame_oe_rounded_percentage && p_je_oe_rounded_percentage > p_ave_oe_rounded_percentage) {
  print(paste0("The most likely person to have written a program with an error, given that a program is found with an error, is Jane with ", p_je_oe_rounded_percentage, "%."))
} else if (p_ame_oe_rounded_percentage > p_je_oe_rounded_percentage && p_ame_oe_rounded_percentage > p_ave_oe_rounded_percentage) {
  print(paste0("The most likely person to have written a program with an error, given that a program is found with an error, is Amy with ", p_ame_oe_rounded_percentage, "%."))
} else if (p_ave_oe_rounded_percentage > p_je_oe_rounded_percentage && p_ave_oe_rounded_percentage > p_ame_oe_rounded_percentage) {
  print(paste0("The most likely person to have written a program with an error, given that a program is found with an error, is Ava with ", p_ave_oe_rounded_percentage, "%."))
} else {
  print(paste0("There is a tie in the error probabilities."))
}
```

    ## [1] "The most likely person to have written a program with an error, given that a program is found with an error, is Amy with 51.7%."
