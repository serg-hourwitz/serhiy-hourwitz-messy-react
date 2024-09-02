# serhiy-hourwitz-messy-react
test assignment for 99tech


List out the computational inefficiencies and anti-patterns found in the code block below.

1. This code block uses
  a. ReactJS with TypeScript.
  b. Functional components.
  c. React Hooks
2. You should also provide a refactored version of the code, but more points are awarded to accurately stating the issues and explaining correctly how to improve them.


Computational Inefficiencies and Anti-Patterns

1. Redundant Function Calls in useMemo:

  * The getPriority function is called multiple times within the useMemo hook: once in the filter method and twice in the sort method. This leads to unnecessary computation.
  * Improvement: Cache the priority values for each balance to avoid recalculating them.

2. Incorrect Condition in filter:

  * The filter logic is flawed because it doesn't correctly account for the condition when balance.amount <= 0. It should be checking the priority first before filtering based on the amount.
  * Improvement: Correct the condition to reflect the intended logic.

3. Inefficient Sorting Logic:

  * Sorting and filtering are happening together, which may lead to inefficiency. Sorting should ideally happen after filtering.
  * Improvement: Separate the filtering and sorting to optimize the logic.

4. Unnecessary useMemo:

  * The useMemo hook is used for sortedBalances, but its dependency array includes prices, which doesn't affect the sorting logic. This may lead to unnecessary recalculation.
  * Improvement: Refine the dependency array to only
include variables that affect the memoized value.

5. Unnecessary Re-mapping of sortedBalances:

  * The code maps sortedBalances twice: once for formattedBalances and again when creating rows. This introduces unnecessary computation.
  * Improvement: Combine the formatting and row creation into a single map function.

6. Unused formattedBalances Variable:

  * The formattedBalances variable is created but never used. This is a waste of resources.
  * Improvement: Remove the formattedBalances variable or incorporate it into the row creation process.


Summary of Improvements

* Cached Priority Values: Reduced redundant calls to getPriority.
* Corrected Filtering Logic: Improved the filtering condition to correctly reflect the logic.
* Optimized Sorting: Performed sorting only after filtering, enhancing performance.
* Refined useMemo: Adjusted the dependency array to avoid unnecessary recalculations.
* Combined Mapping Operations: Reduced computational overhead by combining formatting and row creation into a single step.
* Removed Unused Variables: Eliminated formattedBalances to avoid resource wastage.
