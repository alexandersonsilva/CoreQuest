# Mission 001 — What Happens When the Power Button Is Pressed?

**Difficulty:** ⭐☆☆☆☆

**Category:** Computer Architecture

**Status:** ✅ Completed

**Estimated Study Time:** 40 minutes

**Date:** July 2026

## Objective

Understand the sequence of events that occurs from pressing the computer's power button until the CPU begins executing firmware.

---

## Initial Hypothesis

My initial idea was that a tiny memory chip (possibly smaller than 1 MB) remained in a dormant state waiting for the power button to be pressed. Once activated, this memory would wake up the CPU, which would then load the BIOS and eventually the operating system.

---

## What I Learned

The motherboard is never completely "dead" while connected to power.

A small standby power rail (5VSB) keeps part of the motherboard energized.

When the power button is pressed, it briefly shorts the two POWER_SW pins on the motherboard.

The chipset or embedded controller detects this signal and commands the power supply to enable all voltage rails.

Once every voltage becomes stable, the power supply sends the **Power Good (PWR_OK)** signal.

Only after receiving this signal does the CPU leave its reset state.

The CPU does not wake because another processor tells it to.

Instead, it is electrically released from reset.

Immediately after leaving reset, the CPU begins executing instructions from a predefined address that maps to the motherboard firmware (BIOS/UEFI).

This behavior is permanently designed into the processor's hardware.

The CPU cannot randomly decide to execute another program.

---

## Final Understanding

The CPU is born with one predefined starting point.

It cannot "choose" another path when it powers on.

Once released from reset, it immediately starts executing the motherboard firmware located at its reset vector.

From there, the firmware initializes the hardware and eventually loads the operating system.

---

## Key Concepts

- Standby Power (5VSB)
- Power Button (POWER_SW)
- Chipset / Embedded Controller
- Power Good (PWR_OK)
- CPU Reset State
- Reset Vector
- BIOS
- UEFI
- Firmware
- Boot Process

---

## Reflection

Before this mission I believed a tiny memory module awakened the processor.

Now I understand that the CPU itself already contains the logic required to begin execution.

The motherboard only provides stable power and releases the CPU from reset.

This was my first deep look into how a computer truly starts.
