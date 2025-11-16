# Lloyd SafeDrive – Responsible Mobility Scoring Platform

AI-powered driver scoring platform for *Lloyd Assurances* combining:

- *YOLO-based road sign detection* on real driving images.
- *Safety & eco-driving scores* converted into *points*, *pricing incentives* and *RSE indicators*.
- *Multi-role web interface* for drivers and Lloyd administrators.

Built as part of the **Hack For Good 4.0 – Lloyd Assurances** challenge.


---

## 1. Project overview

The goal of this project is to turn raw driving data into:

- A *transparent scoring system* for drivers (safety + eco-driving).
- A *business tool* for Lloyd to:
  - price risk more fairly,
  - reduce claim costs,
  - and report on *mobility-related RSE impact*.

Core idea:

- The camera + YOLO model detect *real road signs* (speed limits, STOP, etc.).
- Sensor data (speed, acceleration…) describe the *driver’s behaviour*.(saved for phase 2)
- A scoring engine turns all of this into:
  - *Safety score*, *Green driving score*, *points*, and *pricing coefficients*.

---

## 2. Main features

- *YOLO road sign detection*
  - YOLO model (Ultralytics-style) fine-tuned on *real images of road signs*.
  - Detects:
    - speed limit signs,
    - STOP / priority signs (if present in dataset),
    - other relevant road signs.
  - Output: bounding boxes + class labels + confidence.
  [🎥 Watch the demo video](./my_model/demo1.avi)


- *Violation & scoring engine*
  - Compares:
    - *actual speed* vs *speed limit* detected by YOLO.
  - Flags:
    - speeding,
    - behaviour inconsistent with road signs.
  - Computes:
    - *Safety score (0–100)*,
    - *Green driving score (0–100)*,
    - *Driver points* (used for discounts / advantages).
    

- *Driver interface (web)*
  - Dashboard with:
    - current safety/green scores,
    - points and estimated *premium discount*,
    - estimated *fuel and CO₂ savings*,
  - Trip detail:
    - list of violations,
    - speed vs limit,
    - associated frame / image as *proof*.
<img width="1898" height="917" alt="image" src="https://github.com/user-attachments/assets/8b386e16-afbc-4cc3-8431-26102c3c0007" />



- *Administrative client view (web)*
  - Full client list with:
    - contract ID, segment,
    - scores & points,
    - pricing coefficient,
    - status, last trip date.
  - Export to .csv for back-office.

---

## 3. Repository structure


```text
SafePath
    ├───data
    │   ├───images
    │   └───labels
    ├───my_model
    │   └───train
    │       └───weights
    └───TrafficSignes
    └─── interface
