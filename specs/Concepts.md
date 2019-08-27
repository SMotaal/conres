<div markout-class=primer>

<!--prettier-ignore-start-->
# ConRes Specifications
## Concepts
<!--prettier-ignore-end-->

### **`1.` Test Suite**

> **Important Note**: The definitions below involve _opinionated stipulations_ for historically fuzzy terminology, largely open to interpretation and disagreement, especially in edge-cases dealing only with a limited subset of the defined concepts, subject to over-generalization, preferences and/or conventions.

#### **`1.a.` Logical**

<ul>

**`1.a.1.` Test Target** — A distinct set of one or more measurable features (ie image elements) intended for the systematic quantification of a specific process capability for certain operating conditions.

<ul>

**`1.a.1.a.` Supplementary Test Target(s)** — One or more operationally significant but logically distinct test targets meant for caliration and/or validation of the operating conditions.

</ul>

**`1.a.2.` Test Block** — A contiguous array (image area) containing a subset of measurable features, which may either be autonomously or practically divided depending on the testing requirements and constraints.

**`1.a.3.` Test Patch** — A distinct measurable feature (image element) with well-defined sampling criteria and aimpoints.

</ul>

#### **`1.b.` Operational**

<ul>

**`1.b.1.` Test Forme** — an "imposed" sheet containing one or more test elements.

- From the producer side, test elements will usually be "arranged" according to the measurement and/or capture requirements, with clear instructions for handling by the operator, where it is important to clearly mark enclosing areas with test images, intended for reliable processing and sampling.

- From the operator side, sheets will usually be "labeled", "trimmed" and "collated" following instructions and marked enclosing areas.

**`1.b.2.` Test Chart** — trimmed sheet(s) containing individual or sequential test area _normally_ intended for measurement by specialized equipment that often rely on track marks for alignment and positioning.

> **Note**: The special case when printing a single [_Test Target_](#test-target), where generally (but not strictly) the target is a single page, and irrespective of the intended measurement method, such a sheet may also be referred to as a chart in appropriate contexts where it is not ambiguous to any consumer(s).

<ul>

- From the operator side, charts will usually be "stored" using a data interchange format which will often involve quantitative measurements, reference data, and which (in most cases) will encompass measurements across the entire set of charts for the same [_Test Target_](#test-target).

- From the implementor side, an abstract `Asset` class `TestChart` would provide the capabilities to `encode`, `decode`, and `iterate` over measured data `structures` and/or `views`, and where it can also provide the `loadFrom…` (retrieved) and `saveTo…` (stored) operations for "measured" and/or "analyzed" charts.

**`1.b.2.a.` Test Chart Page** (for measurement) — a trimmed sheet containing a single sequentially identifiable, which is _normally_ applicable for test charts that extend beyond the limits of the output and/or scanning device(s), but also, in the right context, may apply to "page 1 of 1".

> **Note**: Redundancies which are not explicitly defined as sequentially ordered parts of the single respective [_Test Definition_](#test-definition) are not considered under this definition.

</ul>

**`1.b.3.` Test Leaf** — a trimmed sheet containing a single individually identifiable test area _normally_ intended for captured by an image scanner with explicit constraints and controls.

<ul>

- From the operator side, leafs will usually be "recorded" as a lossless bitmap image, but may would still involve straightening and/or cropping once "consumed" by the appropriate software implementation.

- From the implementor side, the abstract class `TestImage` would provide the capabilities to `optimize` (straightening and cropping), and `extract` (synthetic slicing), and where it can also provide the `loadFrom…` and `saveTo…` operations meant for "retrieving" and "recording" of scanned and/or optimized leafs.

**`1.b.3.a.` Test Slice** — synthetic segments of the "optimized" leaf directly associated with a particular _Test Block_ or _Test Patch_ (below).

> **Note**: The term "synthetic" here applies to operations that may be accomplished in virtual memory — ie without additional requirements for storage allocations of the respective content.

</ul>
</ul>

</div>
<style src="/markout/styles/playground.primer.css"></style>

<!-- revisions -->
