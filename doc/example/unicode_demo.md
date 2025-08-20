title: Unicode Demo
---

# Unicode Demo

This example demonstrates mathematical symbols and Unicode support in plots.

## Source Files

## Source Code

🔷 **Fortran:** [unicode_demo.f90](https://github.com/lazy-fortran/fortplot/blob/main/example/fortran/unicode_demo/unicode_demo.f90)

```fortran
program unicode_demo
    !! Demonstration of Unicode and Greek letter support in fortplot
    !!
    !! This example shows how to use LaTeX-style Greek letter commands
    !! in titles, axis labels, and legend entries across all backends.
    !!
    !! Features demonstrated:
    !! - Greek letters in mathematical expressions
    !! - Unicode rendering in PNG, PDF, and ASCII outputs
    !! - Scientific notation with proper symbols
    !! - Mixed ASCII and Unicode content

    use fortplot
    use, intrinsic :: iso_fortran_env, only: wp => real64
    implicit none

    ! Mathematical functions for demonstration
    real(wp), parameter :: pi = 3.14159265359_wp
    integer, parameter :: n_points = 100
    real(wp) :: t(n_points), x(n_points), y(n_points), z(n_points)
    integer :: i
    type(figure_t) :: fig

    ! Generate sample data representing wave functions
    do i = 1, n_points
        t(i) = real(i-1, wp) / real(n_points-1, wp) * 4.0_wp * pi
        x(i) = sin(t(i)) * exp(-t(i) / (2.0_wp * pi))  ! Damped sine wave
        y(i) = cos(t(i)) * exp(-t(i) / (3.0_wp * pi))  ! Damped cosine wave
        z(i) = sin(2.0_wp * t(i)) * 0.5_wp             ! Higher frequency wave
    end do

    print *, "=== Unicode/Greek Letter Demo for fortplot ==="
    print *, ""
    print *, "This demo creates plots with Greek letters and Unicode symbols"
    print *, "showing mathematical wave functions in three output formats:"
    print *, ""

    ! Create figure with Unicode-rich content
    call fig%initialize(800, 600)

    ! Title with Greek letters and mathematical notation
    call fig%set_title("Wave Functions: \psi(\omega t) = A e^{-\lambda t} sin(\omega t + \phi)")

    ! Axis labels with Greek letters and units
    call fig%set_xlabel("Time \tau (normalized: \tau = \omega t / 2\pi)")
    call fig%set_ylabel("Amplitude \Psi (V)")

    ! Add plots with Greek letter labels
    call fig%add_plot(t, x, label="\alpha damped: sin(\omega t)e^{-\lambda\tau}")
    call fig%add_plot(t, y, label="\beta damped: cos(\omega t)e^{-\mu\tau}")
    call fig%add_plot(t, z, label="\gamma oscillation: sin(2\omega t)")

    ! Show legend with Unicode content
    call fig%legend("upper right")

    ! Save to all three backends to demonstrate Unicode support

    ! 1. PNG - High quality with antialiased Unicode
    call fig%savefig('output/example/fortran/unicode_demo/unicode_demo.png')
    print *, "  (High-quality antialiased Greek letters via STB TrueType)"

    ! 2. PDF - Vector graphics with Unicode
    call fig%savefig('output/example/fortran/unicode_demo/unicode_demo.pdf')
    print *, "  (Vector Unicode characters, scalable and professional)"

    ! 3. ASCII - Terminal output with Unicode
    call fig%savefig('output/example/fortran/unicode_demo/unicode_demo.txt')
    print *, "  (Terminal-friendly Unicode display)"

    print *, ""
    print *, "=== Greek Letters Supported ==="
    print *, ""
    print *, "Lowercase: \alpha \beta \gamma \delta \epsilon \zeta \eta \theta"
    print *, "           \iota \kappa \lambda \mu \nu \xi \omicron \pi"
    print *, "           \rho \sigma \tau \upsilon \phi \chi \psi \omega"
    print *, ""
    print *, "Uppercase: \Alpha \Beta \Gamma \Delta \Epsilon \Zeta \Eta \Theta"
    print *, "           \Iota \Kappa \Lambda \Mu \Nu \Xi \Omicron \Pi"
    print *, "           \Rho \Sigma \Tau \Upsilon \Phi \Chi \Psi \Omega"
    print *, ""
    print *, "=== Usage Examples ==="
    print *, ""
    print *, "In your Fortran code, simply use LaTeX-style commands:"
    print *, ""
    print *, '  call fig%set_title("Wave: \psi = A sin(\omega t)")'
    print *, '  call fig%set_xlabel("Frequency \nu (Hz)")'
    print *, '  call fig%add_plot(x, y, label="\alpha decay")'
    print *, ""
    print *, "The library automatically converts LaTeX commands to Unicode"
    print *, "characters in all backends (PNG, PDF, ASCII)."
    print *, ""
    print *, "=== Mathematical Examples ==="
    print *, ""

    ! Create a second figure showing common mathematical expressions
    call fig%initialize(800, 600)
    call fig%set_title("Common Physics: E = mc², \Delta E = h\nu, F = q(E + v×B)")
    call fig%set_xlabel("Parameter \xi")
    call fig%set_ylabel("Observable \Theta")

    ! Generate data for common mathematical functions
    do i = 1, n_points
        x(i) = real(i-1, wp) / real(n_points-1, wp) * 6.0_wp
        y(i) = exp(-x(i)**2 / 2.0_wp) / sqrt(2.0_wp * pi)  ! Gaussian
        z(i) = x(i)**2 * exp(-x(i))                         ! Gamma-like
    end do

    call fig%add_plot(x, y, label="Gaussian: \rho(\xi) = e^{-\xi²/2\sigma²}/\sqrt{2\pi\sigma²}")
    call fig%add_plot(x, z, label="Modified \Gamma: f(\xi) = \xi² e^{-\xi}")
    call fig%legend("upper right")

    ! Save mathematical examples figure
    call fig%savefig('output/example/fortran/unicode_demo/math_examples.png')
    call fig%savefig('output/example/fortran/unicode_demo/math_examples.pdf')
    call fig%savefig('output/example/fortran/unicode_demo/math_examples.txt')

    print *, ""
    print *, "Demo completed! Check the generated files to see Unicode rendering."

end program unicode_demo
```

## Features Demonstrated

- **Greek letters**: α, β, γ, δ, π, θ, φ, ψ, ω
- **Mathematical symbols**: ∞, ∑, ∏, ∫, √, ∂
- **Subscripts/Superscripts**: Via LaTeX-like syntax
- **Special characters**: °, ±, ≤, ≥, ≠

## Unicode Support

### Direct Unicode
- Use actual Unicode characters in strings
- Full UTF-8 support in PNG and PDF backends
- ASCII backend shows approximations

### LaTeX-like Commands
- `\alpha` → α
- `\beta` → β
- `\pi` → π
- `\infty` → ∞
- `\sum` → ∑

## Output

### Unicode Demo
### Math Examples
