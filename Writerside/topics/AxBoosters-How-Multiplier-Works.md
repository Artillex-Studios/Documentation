# How Multiplier Works?

### Changes
- If you are updating from AxBoosters V2, this is very important to understand.
- Starting from AxBoosters 3.0.0, we have switched from a decimal format to a percentage format

- So if you are updating from an older version, you will need to use the following formula to change your old booster give commands:

**(OLD_MULTIPLIER - 1) * 100 = NEW_MULTIPLIER**

Example: old multiplier is 1.5, you subtract 1, you get 0.5, you multiply it by 100, and you get 50, which is +50%

### What does this mean?

- The percentage format (currently used) is a much more logical system, it uses numbers that are (generally) whole numbers.
- The decimal system had a big flaw, which is that negative boosters were much harder to understand, and in general it was harder to understand booster stacking (because 1.5 * 1.5 is not 3, which might be confusing why did someone get a certain boost amount if you have like 10+ boosters active)

### A bit more visual example:

| Goal                        | Percentage (**current**) | Decimal (old) |
|-----------------------------|--------------------------|---------------|
| 5 times booster             | +400%                    | 5x            |
| negative 15 percent booster | -15%                     | 0.85x         |
| 30 percent booster          | +30%                     | 1.3x          |

- Hopefully you can understand, that for example stacking 5 of these boosters internally is MUCH harder if we use the decimal format.
- Wth the percentage format we can start from 0 and add all the percentages together, meanwhile, with the decimal system we had to start from 1.0 and try to calculate what the user wants when they activate a second 2.5x booster

| Active Boosters         | Percentage (**current**) | Decimal (old)                                                            |
|-------------------------|--------------------------|--------------------------------------------------------------------------|
| 2x 5% boosters          | +5% + +5% = 10%          | 1.05 * 1.05 != 10%, so we had to use 1 + (1.05 - 1) + (1.05 - 1) = 10%   |
| a 5% and a -15% booster | +5% + -15% = -10%        | 1.05 * 0.85 != -10%, so we had to use 1 + (1.05 - 1) + (0.85 - 1) = -10% |