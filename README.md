# Dengue Bleeder Calculator

A web-based clinical tool for predicting occult bleeding in dengue patients based on haematocrit changes and fluid balance.

🔗 **Live Calculator**: [https://SAIFULSAFUAN.COM/bleeders/](https://SAIFULSAFUAN.COM/bleeders/)

## Overview

The Dengue Bleeder Calculator implements a mathematical model to help healthcare professionals identify potential occult bleeding in dengue patients. By comparing observed haematocrit values with estimated values based on fluid balance, the tool can flag cases where undetected bleeding may be occurring.

## Clinical Background

In dengue fever, two major complications affect haematocrit levels:
- **Plasma leakage**: Causes haemoconcentration (increased haematocrit)
- **Occult bleeding**: Causes decreased haematocrit, but may be masked by concurrent plasma leakage

This calculator helps differentiate between these conditions by accounting for fluid balance and comparing expected vs. observed haematocrit values.

## How It Works

### Mathematical Model

The calculator uses the following core formula:

```
Hct₁ = (Hct₀ × Weight × F) / (Weight × F + Balance)
```

Where:
- `Hct₁` = Estimated haematocrit after fluid shift
- `Hct₀` = Baseline haematocrit
- `Weight` = Patient weight (kg)
- `F` = Correction factor (75 ml/kg for males, 65 ml/kg for females)
- `Balance` = Fluid input - Fluid output (ml)

### Prediction Logic

The tool calculates a lower limit threshold:
```
Lower Limit = Hct₁ - (Hct₀ - Hct₁) × x
```

Where `x` is an adjustable correction factor for insensible losses (0-0.5).

**Interpretation**:
- If observed Hct < lower limit → Occult bleeding likely
- If observed Hct ≥ lower limit → Bleeding unlikely

## Features

- **Gender-specific calculations** with appropriate blood volume correction factors
- **Real-time fluid balance tracking** (input/output)
- **Adjustable correction factor** for insensible losses
- **Visual indicators** for quick interpretation
- **Mobile-responsive design** for bedside use
- **No installation required** - runs entirely in browser

## Usage Instructions

1. **Select patient gender** (affects blood volume calculation)
2. **Enter patient weight** in kilograms
3. **Input baseline haematocrit** (Hct₀) - the initial reference value
4. **Input observed haematocrit** (Hct_observed) - the current measurement
5. **Record fluid input** - total fluids given (IV, oral, etc.) in ml
6. **Record fluid output** - total measured output (urine, drainage, etc.) in ml
7. **Adjust correction factor** if needed (default 0.2 is recommended)
8. **Click Calculate** to see the prediction

## Clinical Considerations

⚠️ **Important Notes**:
- This tool is designed to assist clinical decision-making, not replace it
- Always consider the full clinical picture
- The model assumes a 2g/dl Hb drop represents significant bleeding
- Correction factor may need adjustment based on clinical conditions
- Best used during the critical phase of dengue


## Deployment

The calculator is deployed via GitHub Pages and accessible at:
- Primary URL: https://SAIFULSAFUAN.COM/dengue-calculator/
- GitHub Pages URL: https://[username].github.io/[repository]/dengue-calculator/


## Mathematical Basis

This calculator is based on the mathematical model described in:
> "Underlying Mathematics to the Dengue Bleeder Calculator/Predictor Tool"

The model leverages the principle that in dengue:
- Pure plasma leakage → Observed Hct ≈ Estimated Hct, or higher
- Plasma leakage + occult bleeding → Observed Hct < Estimated Hct


## Disclaimer

This calculator is intended for use by qualified healthcare professionals as a clinical decision support tool. It should not be used as the sole basis for diagnosis or treatment decisions. Always correlate with clinical findings and other laboratory results.

## Contact

For questions, suggestions, or bug reports, please:
- Open an issue on GitHub
- Contact: [saifulsafuan@moh.gov.my]

---

**Quick Start**: Visit [https://SAIFULSAFUAN.COM/bleeders/](https://SAIFULSAFUAN.COM/bleeders/) to use the calculator immediately.

*Developed with the aim of improving dengue patient care through early detection of occult bleeding.*
