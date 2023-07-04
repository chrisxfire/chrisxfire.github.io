---
title: notes > code > .net > user interfaces > winui 3 > design > layouts > transforms
date: 2023-01-05T19:10:42-0700
draft: false
---
# Overview
Transforms define how to map points from one coordinate space to another.

Four types of transforms:
- `TranslateTransform` — move an element in x-y space by setting X and Y values.
- `ScaleTransform` — grow/shrink an element based on a center point by setting values for CenterX, CenterY, ScaleX, and ScaleY.
- `RotateTransform` — rotate an element in x-y space by setting Angle, CenterX, and CenterY.
- `SkewTransform` — skew or shear in x-y space by setting AngleX, AngleY, CenterX, and CenterY.

`TranslateTransform` and `ScaleTransform` are most commonly used.
