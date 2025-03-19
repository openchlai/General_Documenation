# OpenCHS Design System
## Component Design Guidelines

**Version:** 1.0  
**Date:** March 19, 2025  
**Status:** Active

## Table of Contents
1. [Introduction](#1-introduction)
2. [Purpose & Principles](#2-purpose--principles)
3. [Core UI Components](#3-core-ui-components)
   - [3.1 Buttons](#31-buttons)
   - [3.2 Forms & Inputs](#32-forms--inputs)
   - [3.3 Cards & Containers](#33-cards--containers)
   - [3.4 Modals & Overlays](#34-modals--overlays)
   - [3.5 Navigation Elements](#35-navigation-elements)
   - [3.6 Tables & Data Displays](#36-tables--data-displays)
4. [Interaction Patterns](#4-interaction-patterns)
   - [4.1 Navigation & Wayfinding](#41-navigation--wayfinding)
   - [4.2 Feedback & Alerts](#42-feedback--alerts)
   - [4.3 Microinteractions & Animations](#43-microinteractions--animations)
5. [Accessibility Standards](#5-accessibility-standards)
6. [Implementation Guidelines](#6-implementation-guidelines)
7. [Development Workflow](#7-development-workflow)
8. [Future Roadmap](#8-future-roadmap)

---

## 1. Introduction

The OpenCHS Design System provides a comprehensive set of guidelines, components, and patterns that ensure a consistent user experience across all OpenCHS applications. This document serves as the definitive reference for implementing UI components that adhere to our established design standards.

These guidelines represent a collaborative effort between designers, developers, and product stakeholders to create a cohesive visual language that promotes usability while maintaining our brand identity.

---

## 2. Purpose & Principles

### Purpose
To standardize the implementation of UI components across OpenCHS applications, promoting:
- **Consistency** in appearance and behavior
- **Accessibility** for all users
- **Efficiency** in development
- **Scalability** across different platforms and devices
- **Visual coherence** that reinforces our brand identity

### Core Design Principles
1. **User-Centered Design**: Components prioritize ease of use and intuitive interaction
2. **Accessibility First**: Components are designed to be accessible by default
3. **Responsive & Adaptive**: Components function across all screen sizes and devices
4. **Performance Optimized**: Components are built for efficiency and minimal load times
5. **Maintainable & Scalable**: Components use consistent patterns that can evolve over time

---

## 3. Core UI Components

### 3.1 Buttons

Buttons provide users with clear actions they can take within the interface.

#### Variants
- **Primary**: High-emphasis, used for main actions
- **Secondary**: Medium-emphasis, used for secondary actions
- **Tertiary/Text**: Low-emphasis, used for tertiary actions
- **Icon**: Used for common actions with universal icons

#### States
- Default
- Hover
- Active/Pressed
- Focused
- Disabled
- Loading

#### Design Tokens
- Primary: `#007BFF` (Blue)
- Secondary: `#6C757D` (Gray)
- Tertiary: `transparent` with text color
- Hover: `darken(color, 10%)`
- Active: `darken(color, 15%)`
- Disabled: `opacity: 0.6`
- Border-radius: `4px`
- Padding: `8px 16px` (standard), `4px 8px` (small), `12px 24px` (large)

#### Accessibility Requirements
- Minimum touch target size: `44px × 44px`
- Color contrast ratio: 4.5:1 minimum (WCAG AA)
- Clear focus indicator for keyboard navigation
- Descriptive labels for screen readers

#### Usage Guidelines
- Use clear, action-oriented labels (e.g., "Save Changes" instead of "OK")
- Primary buttons should appear only once per section/view when possible
- Maintain consistent button ordering throughout the application
- Avoid using too many buttons in a single view

```html
<!-- Example implementation -->
<button class="btn btn-primary">Save Changes</button>
<button class="btn btn-secondary">Cancel</button>
<button class="btn btn-tertiary">Learn More</button>
```

---

### 3.2 Forms & Inputs

Forms and inputs allow users to enter, edit, and submit data.

#### Components
- **Text Fields**: Single and multi-line text input
- **Dropdowns/Select**: For choosing from a list of options
- **Checkboxes**: For multiple selection from a group
- **Radio Buttons**: For single selection from a group
- **Toggle Switches**: For binary states (on/off)
- **Date/Time Pickers**: For selecting temporal values
- **Sliders**: For selecting values from a range
- **File Uploads**: For attaching files

#### States
- Default/Empty
- Focused
- Filled
- Error
- Disabled
- Required
- Optional

#### Design Tokens
- Border: `#D1D5DB` (default), `#007BFF` (focused), `#EF4444` (error)
- Background: `#FFFFFF` (default), `#F9FAFB` (disabled)
- Text color: `#111827` (default), `#6B7280` (placeholder)
- Padding: `12px 16px`
- Border-radius: `4px`
- Error color: `#EF4444`
- Success color: `#10B981`

#### Accessibility Requirements
- Labels associated with form controls
- Error messages linked to inputs
- Keyboard navigable form elements
- Logical tab order
- Form validation that works with assistive technologies

#### Usage Guidelines
- Group related fields together
- Provide clear labels and helpful placeholder text
- Use consistent validation patterns and error messages
- Indicate required and optional fields clearly
- Provide contextual help where needed

```html
<!-- Example implementation -->
<div class="form-group">
  <label for="email" class="form-label">Email Address <span class="required">*</span></label>
  <input type="email" id="email" class="form-input" placeholder="your.email@example.com" required>
  <div class="form-hint">We'll never share your email with anyone else.</div>
</div>
```

---

### 3.3 Cards & Containers

Cards and containers organize related content and actions into cohesive units.

#### Variants
- **Standard Card**: General purpose container
- **Interactive Card**: Clickable container linking to content
- **Feature Card**: Highlights a feature with icon/image
- **Information Card**: Presents key information or status
- **Action Card**: Contains primary actions or workflows

#### States
- Default
- Hover (for interactive cards)
- Selected/Active
- Disabled

#### Design Tokens
- Background: `#FFFFFF`
- Border: `1px solid #E5E7EB` or none with shadow
- Border-radius: `8px`
- Shadow: `0px 2px 8px rgba(0, 0, 0, 0.1)`
- Padding: `24px`
- Gap between cards: `16px`

#### Accessibility Requirements
- Logical content structure with proper heading hierarchy
- Sufficient color contrast for text content
- Keyboard interaction for clickable cards
- Proper focus management

#### Usage Guidelines
- Maintain consistent spacing between and within cards
- Use cards to group related information and actions
- Ensure card hierarchy reflects content importance
- Keep content density balanced for readability

```html
<!-- Example implementation -->
<div class="card">
  <div class="card-header">
    <h3 class="card-title">Patient Summary</h3>
  </div>
  <div class="card-body">
    <p>Content goes here...</p>
  </div>
  <div class="card-footer">
    <button class="btn btn-primary">View Details</button>
  </div>
</div>
```

---

### 3.4 Modals & Overlays

Modals and overlays present focused content or interactions that temporarily block the main interface.

#### Variants
- **Dialog Modal**: For user decisions or confirmations
- **Form Modal**: For collecting user input
- **Information Modal**: For displaying important information
- **Full-screen Modal**: For complex workflows
- **Toast/Notification**: For brief, non-blocking messages

#### States
- Opening
- Open
- Closing
- Closed

#### Design Tokens
- Background: `#FFFFFF`
- Overlay: `rgba(0, 0, 0, 0.5)`
- Border-radius: `8px`
- Shadow: `0px 4px 16px rgba(0, 0, 0, 0.2)`
- Width: varies by type (small: `400px`, medium: `600px`, large: `800px`)
- Animation: `200ms ease-in-out`
- Z-index: `1000`

#### Accessibility Requirements
- Focus trap within the modal when open
- ESC key closes the modal
- ARIA roles and attributes
- Return focus to triggering element when closed
- Screen reader announcements

#### Usage Guidelines
- Use sparingly to avoid disrupting the user flow
- Provide clear dismissal methods (close button, ESC key, overlay click)
- Maintain consistent positioning and animation
- Ensure modal content is concise and focused
- Prevent background scrolling when modal is open

```html
<!-- Example implementation -->
<div class="modal" role="dialog" aria-labelledby="modal-title" aria-modal="true">
  <div class="modal-overlay"></div>
  <div class="modal-container">
    <header class="modal-header">
      <h2 id="modal-title">Confirm Action</h2>
      <button class="modal-close" aria-label="Close">×</button>
    </header>
    <div class="modal-body">
      <p>Are you sure you want to proceed?</p>
    </div>
    <footer class="modal-footer">
      <button class="btn btn-secondary">Cancel</button>
      <button class="btn btn-primary">Confirm</button>
    </footer>
  </div>
</div>
```

---

### 3.5 Navigation Elements

Navigation elements help users move through the application and understand their current location.

#### Components
- **Navigation Bar**: Top-level navigation
- **Sidebar**: Persistent vertical navigation
- **Breadcrumbs**: Shows hierarchical location
- **Tabs**: Content organization within a page
- **Pagination**: Navigation through multipage content
- **Links**: Inline navigation within content

#### States
- Default
- Active/Current
- Hover
- Focused

#### Design Tokens
- Active color: `#007BFF`
- Inactive color: `#6C757D`
- Hover color: `darken(color, 10%)`
- Font size: `14px` (standard), `16px` (headers)
- Icon size: `20px` × `20px`

#### Accessibility Requirements
- Keyboard navigable
- Skip-to-content link
- ARIA landmarks and roles
- Current page/section indicators for screen readers
- Sufficient contrast for all states

#### Usage Guidelines
- Maintain consistent navigation patterns across the application
- Use clear, concise labels for navigation items
- Indicate current location visually and programmatically
- Group related navigation items together
- Consider responsive behaviors for different screen sizes

```html
<!-- Example implementation -->
<nav class="sidebar" aria-label="Main Navigation">
  <ul class="nav-list">
    <li class="nav-item">
      <a href="/dashboard" class="nav-link active">
        <span class="nav-icon">📊</span>
        <span class="nav-text">Dashboard</span>
      </a>
    </li>
    <li class="nav-item">
      <a href="/patients" class="nav-link">
        <span class="nav-icon">👤</span>
        <span class="nav-text">Patients</span>
      </a>
    </li>
    <!-- More items -->
  </ul>
</nav>
```

---

### 3.6 Tables & Data Displays

Tables and data displays present structured information in a scannable format.

#### Components
- **Data Tables**: For detailed data with multiple attributes
- **Lists**: For simple collections of items
- **Cards Grid**: For visual data displays
- **Charts/Graphs**: For data visualization

#### States
- Default
- Hover
- Selected
- Sorted
- Filtered

#### Design Tokens
- Header background: `#F8F9FA`
- Border color: `#E5E7EB`
- Row hover: `#F9FAFB`
- Selected row: `#EBF5FF`
- Text color: `#111827` (primary), `#6B7280` (secondary)
- Font size: `14px` (body), `12px` (captions)

#### Accessibility Requirements
- Proper table markup (thead, tbody, th)
- Scope attributes for header cells
- Caption or aria-labelledby for table description
- Row and column headers for complex tables
- Keyboard navigation for interactive tables

#### Usage Guidelines
- Use appropriate display type for the data complexity
- Include sortable columns for large datasets
- Provide filtering and search for data discovery
- Show pagination for large datasets
- Maintain consistent alignment (left for text, right for numbers)
- Include empty and loading states

```html
<!-- Example implementation -->
<table class="data-table">
  <caption>Patient Appointments: March 2025</caption>
  <thead>
    <tr>
      <th scope="col">Patient Name</th>
      <th scope="col">Date</th>
      <th scope="col">Time</th>
      <th scope="col">Department</th>
      <th scope="col">Status</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>John Smith</td>
      <td>2025-03-20</td>
      <td>09:30 AM</td>
      <td>Cardiology</td>
      <td><span class="badge badge-success">Confirmed</span></td>
    </tr>
    <!-- More rows -->
  </tbody>
</table>
```

---

## 4. Interaction Patterns

### 4.1 Navigation & Wayfinding

Consistent navigation patterns help users understand their location and available paths through the application.

#### Key Patterns
- **Hierarchical Navigation**: Clear parent-child relationships
- **Hub and Spoke**: Central dashboard with branching sections
- **Sequential Flow**: Step-by-step processes
- **Persistent Navigation**: Always-available core navigation
- **Contextual Navigation**: Context-specific actions and links

#### Implementation Guidelines
- Maintain consistent navigation placement and behavior
- Provide clear visual indicators for current location
- Use breadcrumbs for deep hierarchical structures
- Ensure back navigation is predictable
- Include search functionality for complex applications

---

### 4.2 Feedback & Alerts

Feedback mechanisms inform users about system status, actions, and results.

#### Types
- **Success Messages**: Confirm completed actions
- **Error Messages**: Indicate failures or problems
- **Warning Messages**: Alert potential issues
- **Information Messages**: Provide neutral information
- **Progress Indicators**: Show system activity

#### Design Tokens
- Success: `#10B981` (Green)
- Warning: `#F59E0B` (Yellow)
- Error: `#EF4444` (Red)
- Information: `#3B82F6` (Blue)
- Background opacity: `0.1` for colored backgrounds
- Icon size: `20px` × `20px`

#### Implementation Guidelines
- Position feedback close to the relevant action or content
- Use consistent colors and icons for each feedback type
- Make error messages actionable with clear recovery paths
- Provide appropriate persistence (e.g., toasts auto-dismiss, critical errors remain)
- Ensure all feedback is accessible to screen readers

```html
<!-- Example implementation -->
<div class="alert alert-success" role="alert">
  <span class="alert-icon">✓</span>
  <div class="alert-content">
    <h4 class="alert-title">Success!</h4>
    <p>Patient record has been updated successfully.</p>
  </div>
  <button class="alert-close" aria-label="Close">×</button>
</div>
```

---

### 4.3 Microinteractions & Animations

Subtle animations and interactions enhance usability and provide feedback on user actions.

#### Types
- **Transition Animations**: Smooth changes between states
- **Loading Indicators**: Show system progress
- **Hover Effects**: Indicate interactive elements
- **Feedback Animations**: Confirm user actions
- **Focus Indicators**: Show keyboard focus location

#### Design Tokens
- Duration: `200ms` (short), `300ms` (medium), `500ms` (long)
- Timing function: `ease-in-out` (standard), `ease-out` (entering), `ease-in` (exiting)
- Loading spinner size: `24px` × `24px`

#### Implementation Guidelines
- Use subtle animations that don't interfere with usability
- Ensure animations respect reduced motion preferences
- Keep durations appropriate to the context
- Maintain consistent animation patterns throughout
- Use animations purposefully to guide attention and provide feedback

```css
/* Example implementation */
.btn {
  transition: background-color 200ms ease, transform 100ms ease;
}
.btn:hover {
  background-color: var(--color-hover);
}
.btn:active {
  transform: scale(0.98);
}
```

---

## 5. Accessibility Standards

Accessibility is a core requirement for all OpenCHS components, ensuring usability for all users regardless of ability or context.

### WCAG Compliance
- All components must meet WCAG 2.1 AA standards at minimum
- Work toward AAA compliance where feasible

### Key Requirements
- **Keyboard Accessibility**: All interactive elements must be keyboard accessible
- **Screen Reader Support**: Appropriate ARIA roles, labels, and descriptions
- **Color Contrast**: Minimum 4.5:1 ratio for text, 3:1 for UI components
- **Text Sizing**: Support 200% text size without loss of content or functionality
- **Focus Management**: Clear visual indicators for keyboard focus
- **Alternative Inputs**: Support for touch, mouse, keyboard, and assistive technologies
- **Reduced Motion**: Respect user preferences for reduced animation

### Testing Requirements
- Automated testing with accessibility linters
- Manual testing with screen readers (NVDA, JAWS, VoiceOver)
- Keyboard-only testing
- Contrast and color perception checks
- User testing with people with disabilities

### Documentation
- Document accessibility features for each component
- Provide implementation examples that meet accessibility standards
- Include ARIA usage patterns and requirements

---

## 6. Implementation Guidelines

### Code Standards
- Semantic HTML structure
- CSS naming conventions using BEM methodology
- JavaScript component patterns using React
- TypeScript for type safety
- Responsive design using flexible layouts and breakpoints

### Component Architecture
- Component-based design with clear separation of concerns
- Props for configuration and customization
- Composition patterns for complex components
- Stateful and stateless component separation
- Consistent event handling patterns

### Design Token Implementation
- CSS variables for design tokens
- Theming support via token overrides
- Dark mode support via color scheme tokens
- Responsive tokens for different breakpoints

### Documentation Standards
- JSDoc comments for all component APIs
- Usage examples for common scenarios
- Props tables with types and default values
- Accessibility documentation for each component
- Edge cases and limitations noted

---

## 7. Development Workflow

### Design to Development Handoff
- Figma design system as source of truth
- Component specifications in Storybook
- Design token exports from Figma to code
- Regular sync meetings between design and development

### Quality Assurance
- Unit tests for component logic
- Visual regression tests for appearance
- Integration tests for component interactions
- Accessibility testing (automated and manual)
- Cross-browser and device testing

### Versioning and Release
- Semantic versioning (MAJOR.MINOR.PATCH)
- Changelog maintenance
- Deprecation policies and migration guides
- Beta releases for major changes

### Contribution Process
- Component proposal template
- Design review process
- Code review requirements
- Documentation standards
- Testing expectations

---

## 8. Future Roadmap

### Short-term Goals (Next 3-6 Months)
- Complete dark mode implementation for all components
- Improve mobile responsiveness for complex components
- Enhance animation and transition patterns
- Expand internationalization support

### Medium-term Goals (6-12 Months)
- Develop adaptive component sizing based on viewport
- Create specialized clinical components for healthcare contexts
- Implement advanced theming capabilities
- Enhance performance optimization

### Long-term Vision
- Component A/B testing framework
- AI-assisted component suggestions
- Extended reality (XR) component adaptations
- Automated accessibility remediation

---

## Appendix

### Glossary of Terms

### Version History
- **1.0.0** (March 19, 2025): Initial comprehensive guidelines
- **0.9.0** (February 15, 2025): Beta release for internal review
- **0.5.0** (January 10, 2025): Component foundations established

### Resources & References
- [WCAG 2.1 Guidelines](https://www.w3.org/TR/WCAG21/)
- [Material Design System](https://material.io/design)
- [Nielsen Norman Group Design Principles](https://www.nngroup.com/articles/ten-usability-heuristics/)

---

This document will evolve with continuous improvements to the OpenCHS design system.
