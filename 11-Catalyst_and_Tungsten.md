# Catalyst and Tungsten

## Spark SQL Optimization Goals

Reduce
- Query time
- Memory consumption

## Catalyst Defined

- is the Spark SQL built-in rule-based query optimizer
- Based on functional programming construct in Scala
- Supports the addition of new optimization technique and features
- Enables developers to add data source specific rules and supports new data types 

## Tugsten Defined

- Spark's cost based optimizer that maximizes CPU and memory performance 

## Tungsten Features

- Manages memory explicitly and does not rely on the JVM object model or garbage collection
- Enables cache-friendly computation of algorithms and data structures using both STRIDE-based memory access
- Supports on-demand JVM byte code generation
- Does not generate virtual function dispatches
- Places intermediate data in CPU registers
- Enables Loop unrolling