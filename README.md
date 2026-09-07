# ECE 2112: Advanced Computer Programming and Algorithms
## Experiment 2: Numerical Python (NumPy)

**Student Name:** Bendicio, Sedric Lance B.  
**Section:** 2ECE-A  
**Date Submitted:** September 8, 2026  

---

## I. Objectives
The objectives of this laboratory activity are to:
1. Gain proficiency in creating, reshaping, and manipulating multidimensional arrays using the Numerical Python (`numpy`) library.
2. Apply vectorized operations, mathematical broadcasting, and statistical functions (`mean`, `std`) on NumPy matrices.
3. Utilize boolean indexing and conditional array masking techniques to query, filter, and extract elements matching specific numerical criteria.
4. Implement reproducible pseudorandom number generation using `np.random.seed()` and export resulting array data into binary `.npy` format.

---

## II. Repository Contents
* `Programming Assignment 2 (BENDICIO_2ECE-A).ipynb`: Jupyter Notebook containing the step-by-step Python code, NumPy array operations, verification checks, and cell output displays.
* `X_normalized.npy`: Binary NumPy array file containing the normalized $5 \times 5$ random matrix from Problem A.
* `div_by_4.npy`: Binary NumPy array file containing all cubes from 1 to 100 divisible by 4 from Problem B.
* `above_mean.npy`: Binary NumPy array file containing all squares from 1 to 36 greater than the mean from Problem C.
* `README.md`: Overview, objectives, detailed discussion of the programming problems, constraints, verification results, and execution instructions.

---

## III. Detailed Discussion of the Experiment

### Problem A: Reproducible Normalization Problem (`X_normalized`)
* **Objective:** Generate a $5 \times 5$ matrix $X$ of random integers between 10 and 100 using a fixed random seed (`2112`). Compute the mean ($\mu$) and standard deviation ($\sigma$) of $X$, and normalize $X$ using the standard score formula:
  $$X_{\text{normalized}} = \frac{X - \mu}{\sigma}$$
  Verify that $X_{\text{normalized}}$ has a mean of $0.0$ and a standard deviation of $1.0$, then save the normalized array as `X_normalized.npy`.
* **Implementation Strategy:**
  1. Set the random seed via `np.random.seed(2112)` to guarantee exact numerical reproducibility across test environments.
  2. Generate a $5 \times 5$ integer matrix `X` using `np.random.randint(10, 101, size=(5, 5))`.
  3. Calculate scalar array statistics `X_mean = np.mean(X)` ($46.36$) and `X_std = np.std(X)` ($25.864$).
  4. Perform element-wise matrix normalization `X_normalized = (X - X_mean) / X_std`.
  5. Conduct verification checks by calculating `np.mean(X_normalized)` ($0.0$) and `np.std(X_normalized)` ($1.0$).
  6. Export the normalized array to disk via `np.save("X_normalized.npy", X_normalized)`.
* **Example Output / Check:**
  * **Normalized Mean:** `0.0`
  * **Normalized Standard Deviation:** `1.0` (0.9999999999999999)

---

### Problem B: Cubes Divisible by 4 Problem (`div_by_4`)
* **Objective:** Construct a $10 \times 10$ matrix $C$ containing the cubes of integers from 1 to 100 ($1^3, 2^3, \dots, 100^3$). Extract all elements in $C$ that are evenly divisible by 4, verify the shape of $C$ and count of selected elements, and save the array as `div_by_4.npy`.
* **Implementation Strategy:**
  1. Generate an integer sequence from 1 to 100 using `np.arange(1, 101)`, compute element-wise cubes (`** 3`), and reshape into a $10 \times 10$ grid using `.reshape(10, 10)`.
  2. Filter elements divisible by 4 using boolean indexing with the modulo operator: `div_by_4 = C[C % 4 == 0]`.
  3. Verify matrix dimensions with `C.shape` (`(10, 10)`), display the full 1D extracted array, and confirm element count using `div_by_4.size` ($50$ elements).
  4. Export the resulting array to disk via `np.save("div_by_4.npy", div_by_4)`.
* **Example Output / Check:**
  * **Shape of C:** `(10, 10)`
  * **Number of Selected Elements:** `50`
  * **First 5 Divisible Cubes:** `[8, 64, 216, 512, 1000]`

---

### Problem C: Above-Mean Squares Problem (`above_mean`)
* **Objective:** Create a $6 \times 6$ matrix $S$ containing the squares of integers from 1 to 36 ($1^2, 2^2, \dots, 36^2$). Calculate the arithmetic mean of $S$, filter for elements strictly greater than the mean, verify the count of selected elements, and save the filtered array as `above_mean.npy`.
* **Implementation Strategy:**
  1. Generate integer sequence from 1 to 36, compute element-wise squares (`** 2`), and reshape into a $6 \times 6$ grid using `(np.arange(1, 37) ** 2).reshape(6, 6)`.
  2. Compute the overall array mean `S_mean = np.mean(S)` ($450.1667$).
  3. Apply relational boolean masking `above_mean = S[S > S_mean]` to extract all elements exceeding the mean.
  4. Perform verification checks: display original grid $S$, mean value, filtered 1D array, and verify total element count using `above_mean.size` ($15$ elements).
  5. Export the filtered array to disk via `np.save("above_mean.npy", above_mean)`.
* **Example Output / Check:**
  * **Mean of S:** `450.1666666666667`
  * **Number of S-values above mean:** `15`
  * **Selected Elements:** `[484, 529, 576, 625, 676, 729, 784, 841, 900, 961, 1024, 1089, 1156, 1225, 1296]`

---

## IV. Constraints & Requirements
* **NumPy Vectorization:** All matrix creations, exponentiations, and filtering operations must leverage NumPy vectorized methods and boolean masking without using explicit Python `for` loops or iteration constructs.
* **Reproducibility:** Random matrix generation in Problem A requires explicit seeding (`np.random.seed(2112)`) to ensure deterministic output across execution environments.
* **File Persistence:** Each problem requires saving its final 1D/2D NumPy array into binary `.npy` format using `np.save()`.

---

## V. How to Run
1. Clone this repository to your local machine:
   ```bash
   git clone https://github.com/moriaean/ECE2112_PA2.git
