# FIFO
# Asynchronous FIFO Design

A parameterized asynchronous FIFO implemented in Verilog HDL using
Gray-code pointers for safe clock-domain crossing between independent
write and read clock domains.

## Features

- Asynchronous FIFO architecture
- Independent read and write clock domains
- Gray-code based FIFO pointers
- Clock-domain synchronization
- Full and empty flag generation
- Parameterized data width and FIFO depth
- Synthesizable Verilog RTL

## Architecture

The design consists of the following modules:

- `fifo1.v` — Top-level FIFO module
- `fifomem.v` — FIFO memory
- `sync_r2w.v` — Read-to-write clock-domain synchronizer
- `sync_w2r.v` — Write-to-read clock-domain synchronizer
- `rptr_empty.v` — Read pointer and empty-flag logic
- `wptr_full.v` — Write pointer and full-flag logic

## Working Principle

The FIFO uses two independent clock domains:

- `wclk` — Write clock
- `rclk` — Read clock

The read and write pointers are maintained independently.
Gray-coded pointers are synchronized into the opposite clock domain
before generating the FIFO `full` and `empty` conditions.

## Parameters

| Parameter | Description | Default |
|-----------|-------------|---------|
| `DSIZE` | Data width | 8 bits |
| `ASIZE` | Address width | 4 bits |
| FIFO Depth | `2^ASIZE` | 16 |

## 📁 Project Structure

```text
async-fifo/
│
├── rtl/
│   ├── fifo1.v
│   ├── fifomem.v
│   ├── sync_r2w.v
│   ├── sync_w2r.v
│   ├── rptr_empty.v
│   └── wptr_full.v
│
├── tb/
│   └── fifo_tb.v
│
├── simulation/
│   └── waveform/
│
├── README.md
└── LICENSE
