# wanderBricksSemtantics

A teaching project demonstrating how to use **Genie Code** to build the **Unity Catalog Semantic Layer** — from metric view authoring through to Genie Agent consumption.

## Purpose

This repo walks through the end-to-end workflow of:

1. Defining and registering **metric views** in Unity Catalog using Genie Code
2. Surfacing those metric views inside a **Genie Agent** so business users can query curated metrics in natural language

The goal is to provide a reproducible, opinionated reference for teams adopting the UC Semantic Layer pattern.

## Repository Structure

This is a monorepo containing two Databricks Asset Bundles (Declarative Automation Bundles):

```
wanderBricksSemtantics/
├── wb-metric-views/       # Bundle 1: Create & register metric views
│   └── databricks.yml
├── wb-genie-agent/        # Bundle 2: Genie Agent consuming metric views
│   └── databricks.yml
└── README.md
```

### `wb-metric-views`

This bundle handles the **authoring and registration** of metric views in Unity Catalog:

* Define metric view DDL (`CREATE VIEW ... WITH METRICS LANGUAGE YAML`)
* Curate business-friendly metric definitions (names, descriptions, time grains, dimensions)
* Deploy metric views to target catalogs/schemas via bundle deployment

### `wb-genie-agent`

This bundle provisions a **Genie Agent** (Genie Space) that consumes the registered metric views:

* Configure the Genie Space with the metric-view-backed tables
* Provide sample questions and instructions for natural-language metric exploration
* Demonstrate how the semantic layer enables self-serve analytics through Genie

## Getting Started

1. Deploy `wb-metric-views` first to register metric views in your target schema
2. Deploy `wb-genie-agent` to create the Genie Space wired to those views
3. Open the Genie Space and ask questions against your curated metrics

## Prerequisites

* Databricks workspace with Unity Catalog enabled
* Databricks CLI configured
* Source tables with data to build metrics on
