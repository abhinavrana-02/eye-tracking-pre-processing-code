# eye-tracking-pre-processing-code
The algorithm used in this code is a combination of Dispersion-Threshold Identification (IDT) and Velocity-Threshold Identification (IVT) for classifying eye movements into fixations and saccades.

1. Dispersion-Threshold Identification (IDT)
Used to Detect Fixations

The IDT algorithm works by:

    Segmenting the gaze data into fixed time intervals (e.g., 100ms).
    Measuring dispersion, which is the spatial spread of gaze points:
    Dispersion=(max⁡(FPOGX)−min⁡(FPOGX))+(max⁡(FPOGY)−min⁡(FPOGY))
    Dispersion=(max(FPOGX)−min(FPOGX))+(max(FPOGY)−min(FPOGY))
    Classifying as a fixation if:
        Dispersion ≤ Threshold (8 pixels)
        Duration ≥ Threshold (50ms)

💡 If gaze points stay within a small area for a long enough time, it's a fixation.
2. Velocity-Threshold Identification (IVT)
Used to Detect Saccades

The IVT algorithm works by:

    Calculating gaze velocity:
    Velocity=Distance between two gaze pointsTime difference
    Velocity=Time differenceDistance between two gaze points​
    If velocity ≥ threshold (10 pixels/ms), it is classified as a saccade.
    Saccades are also detected when dispersion > threshold, meaning the gaze shifts quickly over a large area.

💡 If gaze moves too fast, it is a saccade (eye jump).
