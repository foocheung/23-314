# Fostamatinib SoloTE Analysis

## Overview

Previous scRNA-seq analysis of PBMCs from fostamatinib-treated patients identified limited conventional differential gene expression in monocytes, but a stronger signal in dendritic cells.

The purpose of this analysis is to use SoloTE to evaluate whether fostamatinib treatment is associated with changes in transposable element expression, particularly in monocytes and dendritic cells.

## CVFO Dataset

The CVFO dataset contains PBMCs from placebo- and fostamatinib-treated subjects collected approximately 60 days after treatment.

| Treatment    | Subjects                                              |
| ------------ | ----------------------------------------------------- |
| Placebo      | `CVFO-1`, `CVFO-3`, `CVFO-8`, `CVFO-29`, `CVFO-38`    |
| Fostamatinib | `CVFO-15`, `CVFO-18`, `CVFO-25`, `CVFO-42`, `CVFO-50` |

Each subject was assessed under two stimulation conditions:

* `LPSm`
* `LPSp`

This produces four analysis groups:

* `Placebo_LPSm`
* `Placebo_LPSp`
* `Fostamatinib_LPSm`
* `Fostamatinib_LPSp`

## Analysis Plan

SoloTE expression will be summarized separately for each major PBMC cell type, with particular attention to:

* monocytes
* dendritic cells

The analysis will test whether fostamatinib changes baseline TE expression, alters the response to LPS stimulation, or produces a distinct TE-response pattern compared with placebo.

## Contrasts

### Fostamatinib versus Placebo under LPSm

```text
Fostamatinib_LPSm vs Placebo_LPSm
```

Tests whether TE expression differs between treatment groups under the LPSm condition.

### Fostamatinib versus Placebo under LPSp

```text
Fostamatinib_LPSp vs Placebo_LPSp
```

Tests whether TE expression differs between treatment groups under the LPSp condition.

### LPS Response in Placebo Subjects

```text
Placebo_LPSp vs Placebo_LPSm
```

Defines the TE response to LPS stimulation in the placebo group.

### LPS Response in Fostamatinib Subjects

```text
Fostamatinib_LPSp vs Fostamatinib_LPSm
```

Defines the TE response to LPS stimulation following fostamatinib treatment.

### Treatment-by-LPS Interaction

```text
(Fostamatinib_LPSp - Fostamatinib_LPSm)
-
(Placebo_LPSp - Placebo_LPSm)
```

Tests whether fostamatinib changes the TE response to LPS stimulation.

This is the key contrast for identifying treatment-specific TE reactivation associated with trained immune responses.

## Expected Output

The analysis will identify:

* differentially expressed SoloTE features for each cell type and contrast
* TE signatures associated with fostamatinib treatment
* TE responses specific to monocytes and dendritic cells
* candidate TE features for comparison with the earlier Day 3 or Day 5 fostamatinib dataset
