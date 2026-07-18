# SPARC-CL

**Subspace Projection and Contrastive Unlearning for Cross-Domain Adaptation**

SPARC-CL is a lightweight, self-supervised domain adaptation framework. It is fully label-agnostic during adaptation — no target labels are needed — and is designed to work across heterogeneous data modalities (image, time-series, tabular) while remaining small enough for edge deployment.

## Overview

The core of SPARC-CL is a three-stage SPARC layer inserted into a backbone network:

1. **Measure** — quantifies domain discrepancy using Cohen's d-based gating
2. **Isolate** — projects domain-specific variation into an orthonormal subspace (B ∈ R^{M×K×D})
3. **Clean** — applies adaptive residual cleaning (λ ∈ [0.1, 0.6]) to remove domain-specific signal while preserving task-relevant features

Adaptation is driven by an NT-Xent contrastive loss combined with gate entropy regularization (β = 0.001), which empirically produces more stable adaptation than contrastive loss alone.

Built on a MobileNetV2 backbone, with INT8 TFLite quantization for edge deployment (~1.77 MB model size).

## Results

- Source domain: PlantVillage
- Primary target: Rice Disease Dataset
- Secondary evaluation: BCDD
- Ablations show gate entropy loss + SimCLR are synergistic: full model reaches 80.45% (stable)

The framework is also being extended and validated on time-series (Sleep-EDF, UCI-HAR, CWRU) and tabular benchmarks.

## Citation

A paper describing this work is in preparation. Citation details will be added on publication.

## License

TBD
