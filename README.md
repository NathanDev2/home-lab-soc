# Home SOC Lab with Wazuh

## Overview

This project documents the setup of a home Security Operations Center lab using Ubuntu Server, Wazuh, and a Windows endpoint agent. The goal is to practice endpoint monitoring, log collection, alert investigation, and basic incident response workflows in a controlled lab environment.

## Lab Architecture

```text
Windows Endpoint
└── Wazuh Agent
    └── Sends endpoint security events

        ↓

Ubuntu Server
├── Wazuh Manager
├── Wazuh Indexer
└── Wazuh Dashboard