A8DH202X ECUFlash AFR Safety Definition Extension

File:
  A8DH202X_MerpMod_AFR_Safety.xml

Install:
  Place this XML beside the ECUFlash Subaru definition files so that the
  include reference "A8DH202X" resolves to the matching base definition.
  Keep the existing A8DH202X.xml unchanged.
  Select the extension only when opening the matching custom ROM candidate.

Exposed calibrations:
  Wideband AFR Safety Threshold
    Data: 0xE253C
    X axis: 0xE251C, 4 float32 values, engine load
    Y axis: 0xE252C, 4 float32 values, RPM
    Data type: uint16 big-endian
    Conversion: displayed AFR = raw * 0.01
    Raw 1000 displays 10.00 AFR; raw 2500 displays 25.00 AFR.

  Wideband Safety Pedal Release Threshold
    Address: 0xE24E8
    Data type: float32 big-endian
    Current value: 1.00
    This is provisional; validate against a live pedal-angle log.

Table contents currently in candidate:
                  Load 1.0   1.5   2.0   2.5
    2500 RPM       25.00 25.00 25.00 25.00
    3000 RPM       25.00 10.00 10.00 10.00
    4500 RPM       25.00 10.00 10.00 10.00
    6000 RPM       25.00 10.00 10.00 10.00

Important:
  The 10.00 AFR cells are deliberately set to trip as a bench/logic test.
  They are not a safe road calibration.
  The XML is well-formed and its addresses/data scaling were cross-checked
  against the candidate binary, but it has not been opened in ECUFlash itself.
  The definition does not prove that the custom runtime routine is correct.
  Do not flash or road-test the candidate on the strength of this XML alone.
