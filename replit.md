# Overview

This is a 3D browser-based airplane shooter game built with React Three Fiber and TypeScript. The application features a complete game loop with menu systems, 3D graphics, collision detection, sound effects, and persistent high score tracking. Players control an aircraft and defend against waves of enemy planes in an immersive 3D environment.

# User Preferences

Preferred communication style: Simple, everyday language.

# System Architecture

## Frontend Architecture
The application uses a modern React-based architecture with several key design decisions:

**Component Structure**: The frontend follows a component-based architecture with clear separation between game logic, UI components, and 3D rendering. Game components (Player, Enemy, Bullet, Explosion) handle 3D object rendering while UI components manage menus and overlays.

**State Management**: Uses Zustand for global state management with multiple specialized stores:
- `useGameState` - Manages core game logic, entities, and scoring
- `useAudio` - Handles sound effects and music
- `useGame` - Controls game phases and transitions

**3D Rendering**: Built on React Three Fiber (@react-three/fiber) for declarative 3D scene management, with @react-three/drei for additional utilities like keyboard controls and camera management.

**Styling**: Implements Tailwind CSS with a comprehensive design system using Radix UI components for consistent, accessible UI elements. Custom CSS variables define a dark theme optimized for gaming.

## Backend Architecture
The backend follows a minimal Express.js architecture designed for potential expansion:

**Server Structure**: Uses Express with TypeScript in ESM format. The current implementation includes basic route registration and error handling middleware, with placeholder storage interface for future database integration.

**Storage Interface**: Implements an abstraction layer with `IStorage` interface and `MemStorage` class for in-memory data persistence. This design allows easy migration to database storage without changing application logic.

**Development Setup**: Integrates Vite for hot module replacement and development server proxy, enabling seamless full-stack development experience.

## Data Storage Solutions
**Current Implementation**: Uses in-memory storage via `MemStorage` class for user data. Game state persistence uses browser localStorage for high scores and settings.

**Database Ready**: Configured with Drizzle ORM and PostgreSQL schema definitions for future database integration. The schema includes user authentication tables with proper type safety.

**Migration Strategy**: Database migrations are managed through Drizzle Kit with schema versioning support for production deployments.

## Authentication and Authorization
**Prepared Infrastructure**: Database schema includes user authentication tables with username/password fields and proper constraints.

**Current State**: Authentication is not currently implemented but the foundation exists for future user accounts and persistent game progress.

## Game Engine Architecture
**Entity Management**: Implements a custom entity-component system within Zustand stores for managing game objects (players, enemies, bullets, explosions) with unique IDs and lifecycle management.

**Physics and Collision**: Custom AABB collision detection system with utility functions for game physics calculations including distance, clamping, and linear interpolation.

**Game Loop**: Uses React Three Fiber's `useFrame` hook for 60fps game loop with delta-time calculations for frame-rate independent movement and animations.

**Audio System**: Comprehensive audio management with support for background music, sound effects, and user-controlled muting with proper audio object lifecycle management.

# External Dependencies

## 3D Graphics and Game Engine
- **React Three Fiber** - Declarative 3D rendering engine built on Three.js
- **@react-three/drei** - Essential utilities for R3F including controls, helpers, and components
- **@react-three/postprocessing** - Visual effects and post-processing pipeline
- **vite-plugin-glsl** - GLSL shader support for custom visual effects

## UI Framework and Styling
- **Radix UI** - Comprehensive unstyled component library for accessible UI primitives
- **Tailwind CSS** - Utility-first CSS framework with custom design system
- **Lucide React** - Modern icon library for UI elements
- **class-variance-authority** - Type-safe variant API for component styling

## State Management and Data
- **Zustand** - Lightweight state management with subscription support
- **@tanstack/react-query** - Server state management and caching (prepared for API integration)

## Database and ORM
- **Drizzle ORM** - Type-safe SQL ORM with excellent TypeScript integration
- **@neondatabase/serverless** - Serverless PostgreSQL database adapter
- **Neon Database** - Cloud PostgreSQL database service

## Development and Build Tools
- **Vite** - Fast build tool and development server
- **TypeScript** - Type safety and enhanced development experience
- **ESBuild** - Fast JavaScript bundler for production builds
- **tsx** - TypeScript execution for development

## Audio and Assets
- **Asset Support** - Configured for 3D models (.gltf, .glb) and audio files (.mp3, .ogg, .wav)
- **Font Loading** - Inter font family for consistent typography