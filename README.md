# Calculator 1: Dengue Bleeder Calculator

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

## License

[GNU Affero 3.0]

## Disclaimer

This calculator is intended for use by qualified healthcare professionals as a clinical decision support tool. It should not be used as the sole basis for diagnosis or treatment decisions. Always correlate with clinical findings and other laboratory results.

**Quick Start**: Visit [https://SAIFULSAFUAN.COM/bleeders/](https://SAIFULSAFUAN.COM/bleeders/) to use the calculator immediately.

*Developed with the aim of improving dengue patient care through early detection of occult bleeding.*

---

# Calculator 2: Dengue Death Probability Calculator

## Overview

This web application implements a clinical decision support tool for predicting mortality risk in dengue patients using the REPROSED2017 Elastic Net Model. The calculator is based on a glmnet (elastic net regularized logistic regression) model trained on clinical parameters commonly available in dengue patient care settings.

## Features

### 1. Calculator Mode
- Direct input of clinical parameters
- Automatic BMI calculation from weight and height
- Real-time probability calculation
- Clean, intuitive interface for rapid clinical use

### 2. Simulator Mode
- Interactive sliders for exploring parameter relationships
- Visual feedback for understanding how each parameter affects mortality risk
- Useful for educational purposes and understanding model behavior

## Clinical Parameters

The model uses 8 key clinical parameters:

| Parameter | Description | Units | Clinical Significance |
|-----------|-------------|-------|----------------------|
| **Persistent Diarrhea** | Presence of ongoing diarrhea | Yes/No | Indicator of dengue with GI involvement |
| **BMI** | Body Mass Index | kg/m² | Nutritional status and body composition |
| **RR** | Respiratory Rate | breaths/min | Indicator of respiratory distress or compensation |
| **Platelets** | Platelet count | ×10³/µL | Marker of dengue severity and bleeding risk |
| **HCO₃** | Serum bicarbonate | mmol/L | Acid-base status, metabolic acidosis indicator |
| **Lactate** | Serum lactate | mmol/L | Tissue perfusion and shock severity |
| **Albumin** | Serum albumin | g/L | Capillary leak and nutritional status |
| **AST** | Aspartate aminotransferase | U/L | Liver involvement and organ dysfunction |

## Model Information

### REPROSED2017 Study
The model was developed as part of the REPROSED2017 study, which aimed to create a reliable prediction tool for dengue mortality in severe dengue cases using readily available clinical parameters.

### Elastic Net Regularization
- **Alpha**: 0.1 (10% L1 penalty, 90% L2 penalty)
- **Lambda**: Optimized through cross-validation
- **Family**: Binomial (logistic regression)

### Model Performance
The elastic net approach helps to:
- Handle correlated predictors common in clinical data
- Prevent overfitting through regularization
- Select the most informative features automatically

### Model Integration
**Important Note**: This demonstration uses placeholder coefficients. For clinical use, the actual model coefficients must be extracted from the `glmnetfin31.rda` file using:

```r
# In R, load the model and extract coefficients
load("glmnetfin31.rda")
coefficients <- coef(glmnetfin31$finalModel, s = glmnetfin31$bestTune$lambda)
print(coefficients)
```

## Usage Guidelines

### Clinical Context
This calculator should be used as a decision support tool in conjunction with clinical judgment. It is designed for:
- Risk stratification of dengue patients
- Identifying high-risk patients requiring intensive monitoring
- Supporting resource allocation decisions
- Educational purposes for understanding dengue severity factors

### Limitations
1. Model predictions are based on the training population and may not generalize to all settings
2. Does not replace clinical judgment or comprehensive patient assessment
3. Should be validated in local populations before widespread implementation
4. Requires accurate input of all parameters for reliable predictions

## License

[GNU Affero 3.0]

## Disclaimer

Clinical decisions should not be based solely on this calculator's output. Always use clinical judgment and consider the full clinical context when managing dengue patients.

## Contact

For questions, suggestions, or bug reports, please:
- Open an issue on GitHub
- Contact: [saifulsafuan@moh.gov.my]

---

