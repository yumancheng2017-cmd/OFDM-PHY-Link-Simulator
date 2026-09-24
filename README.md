# OFDM PHY Link Simulator

MATLAB simulation of a coded OFDM physical-layer link with QPSK, convolutional coding, multipath fading, ZF equalization, Viterbi decoding, and BER evaluation.

## Overview

This project implements an end-to-end coded OFDM physical-layer link inspired by IEEE 802.11a parameters.

The system uses a 64-point OFDM waveform with a 16-sample cyclic prefix and evaluates the Bit Error Rate (BER) performance under both static multipath and block-fading channels.

## System

The simulated communication chain consists of:

**Transmitter**

Random Bits → Convolutional Encoding → QPSK Modulation → OFDM Modulation (IFFT) → Cyclic Prefix

**Receiver**

Cyclic Prefix Removal → FFT → Zero-Forcing Equalization → QPSK Demodulation → Viterbi Decoding → BER Calculation

Key system parameters:

- 64 OFDM subcarriers
- 16-sample cyclic prefix
- QPSK modulation
- Rate-1/2 convolutional coding
- Zero-Forcing frequency-domain equalization
- Hard-decision Viterbi decoding

## Channel Models

Two multipath channel models are considered:

### Static Multipath Channel

A fixed three-tap channel is used:

`h = [1, 0.5, 0.2]`

AWGN is added after multipath propagation.

### Block-Fading Multipath Channel

A three-tap complex Gaussian fading channel is independently generated for each OFDM symbol.

The average tap powers are:

`[0.7, 0.2, 0.1]`

AWGN is subsequently added to the received signal.

## Results

BER performance is evaluated over an Eb/N0 range from 0 dB to 20 dB.

The static multipath channel exhibits a rapid BER reduction as Eb/N0 increases. In contrast, the block-fading channel experiences significantly higher BER because deep fades can strongly attenuate individual OFDM symbols.

## Tools

- MATLAB
- Communications Toolbox
