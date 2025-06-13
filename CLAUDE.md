# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

cx25 (cardXchange 2025) is a SwiftUI iOS app for digital business card sharing and synchronization. It's a remake of the original cardXchange idea from 2001, built with modern iOS technologies.

### Core Concept
- Users create and manage digital business cards (cx-cards) with personal/professional information
- Cards can be shared between users via iMessage
- Real-time synchronization of card updates across all linked users
- Data storage using Apple CloudKit for sharing capabilities

### Technology Stack
- **Framework**: SwiftUI with SwiftData for local data management
- **Platform**: iOS (Xcode project)
- **Data Storage**: SwiftData locally, Apple CloudKit for sharing
- **Testing**: Swift Testing framework for unit tests, XCTest for UI tests

## Development Commands

### Building and Running
```bash
# Open project in Xcode
open cx25/cx25.xcodeproj

# Build from command line
xcodebuild -project cx25/cx25.xcodeproj -scheme cx25 -configuration Debug build

# Build for release
xcodebuild -project cx25/cx25.xcodeproj -scheme cx25 -configuration Release build
```

### Testing
```bash
# Run unit tests
xcodebuild test -project cx25/cx25.xcodeproj -scheme cx25 -destination 'platform=iOS Simulator,name=iPhone 15'

# Run UI tests
xcodebuild test -project cx25/cx25.xcodeproj -scheme cx25 -destination 'platform=iOS Simulator,name=iPhone 15' -only-testing:cx25UITests

# Run specific test
xcodebuild test -project cx25/cx25.xcodeproj -scheme cx25 -destination 'platform=iOS Simulator,name=iPhone 15' -only-testing:cx25Tests/cx25Tests/example
```

## Architecture

### Current State (Generation 0)
- Basic SwiftUI app with NavigationSplitView structure
- SwiftData `Item` model with timestamp field (placeholder implementation)
- Standard iOS app structure with main app file, content view, and data model

### Data Models
- `Item.swift`: Current placeholder model with timestamp
- Future: Will expand to include user profile data (name, company, position, addresses, contacts, photo)

### CloudKit Integration (Planned)
- Comprehensive CloudKit sharing implementation documented in `/docs/features/future/share-contact-data/cloud-kit-explanation.md`
- Will use CKShare for record sharing between users
- Universal links for share invitations via iMessage/email
- Offline editing with conflict resolution
- Support for up to 100 participants per share

### File Structure
```
cx25/
├── cx25/                     # Main app target
│   ├── cx25App.swift        # App entry point with SwiftData container
│   ├── ContentView.swift    # Main UI with navigation structure
│   ├── Item.swift           # Data model (currently placeholder)
│   └── Assets.xcassets/     # App resources
├── cx25Tests/               # Unit tests using Swift Testing
├── cx25UITests/             # UI tests using XCTest
└── docs/                    # Project documentation
    ├── ARCHITECTURE.md      # Technical architecture docs
    ├── DATA_STRUCTURES.md   # Data model documentation
    └── features/future/     # Future feature documentation
```

## Development Guidelines

### Code Patterns
- Follow SwiftUI declarative patterns established in ContentView
- Use SwiftData for local data persistence
- Implement proper error handling for CloudKit operations
- Use Swift concurrency (async/await) for network operations

### Testing Approach
- Unit tests use Swift Testing framework (`@Test` annotations)
- UI tests use XCTest framework with XCUIApplication
- Test both local SwiftData operations and CloudKit synchronization

### CloudKit Development
- Enable CloudKit capabilities in project settings
- Configure proper entitlements for CloudKit sharing
- Implement CKShare-based sharing with universal links
- Handle offline scenarios with local caching and sync queues
- Implement field-level conflict resolution for concurrent edits