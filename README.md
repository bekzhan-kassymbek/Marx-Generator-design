## Marx-Generator-design

A design of Marx generator to investigate the nature of high voltages.

## Overview

This project explores the design and simulation of a 10-stage Marx
generator using LTspice.

A Marx generator operates by charging multiple capacitor stages and
then switching them from a parallel charging configuration toward a
series discharge configuration through spark gaps. This allows the individual capacitor
voltages to contribute to a significantly higher output
voltage.

The objective is to study high-voltage output through the operation of a Marx generator.

## Circuit Components

The circuit consists of:

- capacitors with valuef of 100nF and fully charged to 10kv
- The DC supply source of 10kV
- Resistors with 1MOhm value
- Switching elements modelled as spark gaps

## Spark gap model

The simulation uses SPICE directive `.model SparkGap sw(Vt=10k Vh=-2k Ron=0.01 Roff=10meg)`
- Vt = 10kV - breakdown voltage
- Vh = -2k - hysterisis voltage
- Ron = 0.01Ohm - resistance in closed state
- Roff = 10MOhm - resistance in open state


## Circuit Architecture

The design consists of 10 cascades of capacitors and resistors connected through switching elements.

### Charging 

The capacitors are charged from the input source through the resistors.

### Discharging

The spark-gap models start to conduct high voltage. This changes the effective configuration
of the capacitors from parallel to series, and produces a high-voltage output.

## Simulation

Open `simulation/Marx_generator.asc` in LTspice.

The simulation includes SPICE directives:
- `.model SparkGap sw(Vt=10k Vh=-2k Ron=0.01 Roff=10meg)`
- `.tran 20u uic`

## Result

Open `result/marx_generator_graph.png`

The switching elements simulated spark gaps. Voltage was increased after each cascade. 
The output voltage was around 74.8kV.

## Future Improvements

- Add inductors


