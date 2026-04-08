---
topic: sports-analytics
tags: [concept, hardware, sensors, data-collection]
---

## Definition

**Inertial Measurement Units (IMUs)** are wearable sensors combining a 3-axis accelerometer (linear acceleration along X, Y, Z) and a 3-axis gyroscope (rotational velocity), producing 6 degrees-of-freedom (6-DoF) motion data at high sampling rates. In sports analytics, IMUs are attached to athletes' bodies to capture movement kinematics without the occlusion and infrastructure requirements of camera-based systems.

## Data characteristics

- Outputs time-series of 6 channels: AccX, AccY, AccZ, GyrX, GyrY, GyrZ
- Sampling rates typically 50–200 Hz for sports motion
- Data is continuous and must be segmented into windows aligned with discrete actions
- Susceptible to sensor drift (gyroscope), orientation ambiguity, and placement variability across sessions

## Common feature extraction from IMU windows

Statistical features computed per window per axis:
- Mean, standard deviation, RMS — amplitude and energy of movement
- Skewness — asymmetry of acceleration distribution (useful for impact events like spike/dig)
- Signal Magnitude Area (SMA) — overall movement intensity across all axes
- Inter-axis correlation — coupling between body segments during coordinated movements

## Advantages over video for sports HAR

- Works in any lighting and occlusion condition
- No camera infrastructure required; deployable on court/field
- Lower latency: direct sensor → classifier pipeline
- Privacy-preserving

## Limitations

- Sensitive to sensor placement; small positional shifts change readings significantly
- Cannot capture whole-body pose without many sensors
- Player-specific calibration often needed for generalisation

## Sensor modalities beyond 6-DoF

Full IMU packages often include additional sensors:
- **Magnetometer**: 3-axis compass, measures orientation relative to Earth's magnetic field; useful for distinguishing actions with similar acceleration profiles but different facing directions
- **Barometer**: atmospheric pressure sensor; used for altitude/elevation tracking; rarely useful for sports action classification (Salim et al. 2019 found it contributes little)

## Multi-sensor fusion for sports HAR

Decision fusion — combining the classification outputs (votes) of models trained on different sensor subsets — typically outperforms any single sensor. Salim et al. 2019 show that Acc+Mag fusion on both wrists achieves 86.9% UAR vs. 83.99% for the best single-sensor single-hand configuration. The combination is complementary: accelerometer captures movement intensity and direction; magnetometer captures orientation/rotation context.

## Sensor placement: dominant vs. non-dominant hand

A counter-intuitive finding from Salim et al. 2019: under imbalanced (real-distribution) training, the **non-dominant hand** provides higher UAR than the dominant hand for volleyball action detection. Under balanced training, the dominant hand is marginally better. The mechanism is unclear — may reflect biomechanical asymmetry in how non-dominant hand movement patterns distribute across action/non-action windows.

## Papers using this concept

- [[papers/2025-realtime-volleyball-movement-classification-lda|Real-Time Volleyball Movement Classification (Koteda et al., 2025)]] — 6-DoF IMU (accelerometer + gyroscope) for volleyball action classification; 6 statistical features per axis as input to LDA
- [[papers/2019-volleyball-action-modelling-imu-feedback|Volleyball Action Modelling (Salim et al., 2019)]] — dual-wrist 4-modality IMU (accel, gyro, mag, baro); evaluates sensor placement and fusion; best result: Acc+Mag both hands, 86.9% UAR
