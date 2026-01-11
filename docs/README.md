# Architecture Documentation

This directory contains the architecture documentation for the Shopping App

## Documents Included

### 1. Entity Relationship Diagram (ERD)
- **File**: `ERD.md`
- **Purpose**: Defines the main entities and their relationships in the system
- **Entities Covered**: Banner, Category, Items
- **Relationships**: Category to Items (inferred), data storage patterns

### 2. Data Relationship Diagram (DRD)
- **File**: `DRD.md`
- **Purpose**: Illustrates data flow and relationships between components
- **Components Covered**:
  - User Interface (Activities/Fragments)
  - Business Logic (Managers/Helpers)
  - Data Storage (TinyDB/Firebase)
  - Network Layer
  - Cache Layer
- **Flows Covered**: Initialization, category browsing, cart management, image loading, synchronization

### 3. User Journey and Flow Diagrams
- **File**: `UserJourneyFlow.md`
- **Purpose**: Maps out user interactions and system responses
- **Journeys Covered**:
  - Browse and Shop
  - Cart Management
- **Flows Covered**: App launch, category browsing, item details, cart management, checkout, error handling, offline scenarios

## Project Overview

This is an Android e-commerce application that allows users to browse fashion items by category, view item details, add items to cart, and complete purchases. The app uses:

- **Local Storage**: TinyDB (SharedPreferences wrapper) for caching and cart management
- **Remote Storage**: Firebase Storage for images and data
- **Data Format**: JSON structure with banners, categories, and items
- **Architecture**: Android app with Kotlin/Java components

## Key Architecture Decisions

1. **Data Storage**: Hybrid approach using local TinyDB for offline capability and Firebase for remote data
2. **Image Handling**: Remote storage with local caching for performance
3. **Cart Management**: Local storage to persist cart across sessions
4. **Offline Support**: App functions with cached data when network is unavailable

## Usage

These documents should be used by:
- Developers for understanding system architecture
- Designers for user experience validation
- Testers for identifying test scenarios
- Stakeholders for project overview

## Maintenance

Update these documents when:
- New features are added that change data relationships
- User flows are modified
- Architecture components are changed
- New entities or data flows are introduced
