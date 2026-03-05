# Agentic

MCP Data Query Builder (Project B)

1. Project Overview

This project consists of an MCP (Model Context Protocol) server designed to allow an AI agent to query and analyze CSV files in a structured manner via an in-memory SQLite database.

The objective is to transform raw data (CSV) into a temporary relational database to enable complex analyses (SQL, aggregates, statistics) without the user needing to manually manipulate code or files.

2. Technical Architecture

Language: Python 3.10+

Framework: FastMCP

Database: SQLite (In-memory)

Structure:

server.py: Server entry point and MCP tools definition.

sqlite.py: Logical module for database management.

sample_data.csv: Example data for testing purposes.

3. Tool Inventory

Tool

Description

Parameters

load_csv

Imports a CSV file into a SQL table.

file_path, table_name

list_tables

Lists loaded tables and their row counts.

(none)

describe_schema

Displays the structure (columns/types) of the tables.

(none)

run_query

Executes a secure SELECT SQL query.

sql, limit

get_statistics

Calculates Min, Max, and Average of a column.

table_name, column

4. Security

The server implements "Read-Only" security. Any attempt to execute modification commands (DROP, DELETE, INSERT, UPDATE, ALTER, TRUNCATE) via the run_query tool is blocked by a keyword filter.

5. Installation and Usage

Prerequisites

Python installed.

uv tool (recommended) or pip.

Installation

Clone this repository.

Create a virtual environment:

uv venv
source .venv/bin/activate  # (or .venv\Scripts\activate on Windows)


Install dependencies:

uv pip install "mcp[cli]"


Launching in Test Mode (Inspector)

To test the tools in the web interface:

mcp dev server.py


6. Comparative Analysis (H5)

In accordance with the workshop objectives, we compared AI performance with and without this MCP server:

Task

Without MCP (Copy-Paste)

With MCP (SQL Tools)

Calculation Reliability

Risk of hallucination errors on large volumes.

100% reliable (calculated by SQLite).

Context Limits

Blocked by the maximum prompt size.

Capable of analyzing files of several GBs.

Complexity

Difficult to perform complex joins or filters.

Full SQL available for cross-analyses.

Security

AI has access to all raw text.

Access is controlled by defined tools.

Project developed as part of the "Building Agentic Systems with MCP" Workshop.
