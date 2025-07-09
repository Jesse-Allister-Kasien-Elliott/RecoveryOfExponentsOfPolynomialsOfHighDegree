# Sparse Multivariate Polynomial Interpolation

This project implements a high-degree sparse interpolation algorithm in Maple. It extends the Ben-Or and Tiwari method using Kronecker substitution and modular techniques to recover multivariate exponents and coefficients efficiently, even for large degrees and many variables.

## Summary

We address a key challenge in sparse multivariate polynomial interpolation: recovering exponents modulo large primes becomes impractical when the degree is high. Our algorithm avoids this by:
- Applying Kronecker substitution to reduce to univariate interpolation.
- Running exponent recovery modulo several smooth machine primes.
- Using a modular Berlekamp–Massey algorithm and discrete logarithm computation.
- Combining results via a generalized Chinese Remainder Theorem.

This method supports polynomials with hundreds of variables and large degrees, as shown in the provided examples.

## Key Features

- **Sparse interpolation via Ben-Or/Tiwari framework**
- **Exponent recovery using modular techniques**
- **Kronecker substitution and inverse**
- **Custom smooth prime generation**
- **Robust for high-degree, multivariate inputs**
- **Fully implemented in Maple**

## Files and Structure

- `rand_poly`: Generates random sparse multivariate polynomials.
- `smooth_primes`: Finds primes of the form \( p = \Delta \cdot m + 1 \) for exponent recovery.
- `BM`: Berlekamp–Massey algorithm for linear recurrence.
- `interp_exps_mod_p_minus_one`: Modular exponent recovery per prime.
- `GCHREM`: Generalized Chinese Remainder Theorem.
- `K_SUB` / `kronecker_inverse`: Kronecker substitution and inversion.
- `HIGH_DEGREE_POLYNOMIAL_INTERPOLATION`: Main interpolation routine.
- `mod_coeff_interp`: Recovers coefficients via modular linear system.

## Running the Code

You need Maple installed. To run:
```maple
with(NumberTheory):
P, vars := rand_poly(10, 10, 50, 100):
HIGH_DEGREE_POLYNOMIAL_INTERPOLATION(P, vars);
```

This will:
- Generate a sparse random polynomial.
- Run the full interpolation pipeline.
- Verify that the reconstructed polynomial equals the original.

## Example Output

```
Evaluations time=    0.0110s
Solve time=          0.0780s
Roots time=          0.0630s
ModularLog time=     0.2250s
"constructed Polynomial = original polynomial: true"
```

## References

- Z. Ben-Or and P. Tiwari, "A Deterministic Algorithm for Sparse Multivariate Polynomial Interpolation", STOC 1988.
- E. Kaltofen, "Sparse Multivariate Interpolation with Kronecker Substitution", 1982.
