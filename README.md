# Spring Cloud Gateway Configuration

This repository contains the configuration for Spring Cloud Gateway, a powerful and flexible gateway
solution.

## Overview

The configuration includes routes for two APIs: User Management API and Campsite API. The gateway is
set up to handle cross-origin resource sharing (CORS) for better compatibility with frontend
applications.

## Configuration Details

### User Management API

- **ID:** user-api
- **URI:** [http://localhost:9001](http://localhost:9001)
- **Predicates:**
  - Path=/api/v1/users/**
- **Filters:**
  - RewritePath=/api/v1/users/(?<path>.*), /api/v1/users/$\{path}

### Campsite API

- **ID:** campsite-api
- **URI:** [http://localhost:9002](http://localhost:9002)
- **Predicates:**
  - Path=/api/v1/campsites/**
- **Filters:**
  - RewritePath=/api/v1/campsites/(?<path>.*), /api/v1/campsites/$\{path}

## CORS Configuration

- **Default Filters:**
  - DedupeResponseHeader=Access-Control-Allow-Origin Access-Control-Allow-Credentials
- **Global CORS Settings:**
  - Allowed Origins: [http://localhost:3000](http://localhost:3000)
  - Allowed Methods: *
  - Allowed Headers: *
  - Allow Credentials: true

## Running the Gateway

To run the Spring Cloud Gateway, ensure that you have the necessary dependencies installed. You can
customize the configuration further based on your specific requirements.

```bash
# Build and run the gateway
./mvnw clean spring-boot:run
