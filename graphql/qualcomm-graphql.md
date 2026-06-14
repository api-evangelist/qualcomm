# Qualcomm GraphQL Schema

## Overview

This document describes the conceptual GraphQL schema for the Qualcomm Developer API, covering Snapdragon chipsets, AI inference, connectivity, software development kits, and device platform support.

## Provider

- **Name**: Qualcomm
- **Developer Portal**: https://developer.qualcomm.com/
- **Base URL**: https://developer.qualcomm.com/api

## Schema File

- [qualcomm-schema.graphql](qualcomm-schema.graphql)

## Type Summary

The schema models the full Qualcomm developer ecosystem:

| Domain | Types |
|---|---|
| Chipsets and Processors | Chipset, SnapdragonChip, SnapdragonGeneration, CoreArchitecture |
| CPU, GPU, AI Subsystems | CPUSpec, GPUSpec, AISpec, DSPSpec, NPUSpec |
| Connectivity | ModemSpec, WirelessSpec, BluetoothSpec, WiFiSpec, FiveGSpec, LTESpec |
| Media and Sensors | CameraSpec, VideoSpec, AudioSpec |
| Performance and Power | PerformanceData, BenchmarkScore, PowerProfile, ThermalData, TDP, BatterySavings |
| Security | SecurityFeature, TrustZone, SecureElement |
| AI / ML Platform | AI, QNN, QAIHub, MLModel, QuantizedModel, ModelParam, Inference, BatchSize, Latency |
| Developer Tools | QEP, SDK, APIEndpoint, SoftwareStack, Platform |
| Devices and Designs | DeviceSupport, ReferenceDesign, EVKit, SnapdragonDevice |
| Device Verticals | MobileDevice, AutoDevice, IoTDevice, XRDevice, ComputeDevice, ConnectedHome |
| Identity and Access | Developer, APIKey, Token |

## Key Queries

- `chipset(id: ID!)` — fetch a specific Qualcomm chipset by identifier
- `snapdragonChips(generation: String, tier: ChipTier)` — list Snapdragon chips, optionally filtered
- `mlModels(framework: String, quantized: Boolean)` — list ML models available on QAI Hub
- `sdks(platform: Platform)` — list available SDKs for a given platform
- `devices(category: DeviceCategory)` — enumerate certified Snapdragon devices
- `benchmarks(chipsetId: ID!, suite: String)` — retrieve benchmark scores for a chipset
- `developer(id: ID!)` — retrieve developer account information
- `apiKeys(developerId: ID!)` — list API keys for a developer

## Key Mutations

- `registerDeveloper(input: DeveloperInput!)` — create a new developer account
- `createAPIKey(developerId: ID!, label: String!)` — issue a new API key
- `revokeAPIKey(keyId: ID!)` — revoke an existing API key
- `submitModelForOptimization(input: MLModelInput!)` — upload an ML model to QAI Hub for optimization
- `deployModel(modelId: ID!, deviceTarget: String!)` — deploy a quantized model to a target device

## Notes

- This is a conceptual schema based on Qualcomm's public developer documentation and product catalog.
- Qualcomm does not currently publish a public GraphQL endpoint; this schema represents a potential GraphQL interface over their REST APIs and data model.
- Source: https://developer.qualcomm.com/
