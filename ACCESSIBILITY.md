# Accessibility Standards

## Accessibility Validation Requirements

**MANDATORY**: ALL accessibility checks must pass before any production readiness claims.

### Accessibility Gate Status
- **100% compliance** with WCAG 2.2 Level AA standards is MANDATORY
- Accessibility validation results must be verified and documented
- No production readiness claims without explicit accessibility confirmation

## WCAG 2.2 Level AA Compliance

### 1. Perceivable

#### 1.1 Text Alternatives
- **Images**: All images have appropriate alt text or are marked as decorative
- **Complex Images**: Charts, graphs, and diagrams have detailed descriptions
- **Functional Images**: Images used as buttons/links have descriptive alt text
- **Image Text**: Avoid text in images; when necessary, provide text alternative
- **Audio/Video**: Non-speech audio content has text alternatives

#### 1.2 Time-based Media
- **Captions**: All pre-recorded video content has accurate captions
- **Live Captions**: Live video streams provide real-time captions
- **Audio Descriptions**: Video content includes audio descriptions for visual information
- **Transcripts**: Audio-only content has complete transcripts
- **Sign Language**: Pre-recorded content includes sign language interpretation (Level AAA goal)

#### 1.3 Adaptable
- **Semantic Structure**: Proper HTML heading hierarchy (h1-h6) and landmarks
- **Reading Order**: Content maintains logical reading order when linearized
- **Form Labels**: All form inputs have programmatically associated labels
- **Instructions**: Form instructions are programmatically associated with controls
- **Tables**: Data tables use proper headers, captions, and summary information

#### 1.4 Distinguishable
- **Color Contrast**: Minimum 4.5:1 for normal text, 3:1 for large text (18pt+ or 14pt+ bold)
- **Enhanced Contrast**: Target 7:1 for normal text, 4.5:1 for large text (Level AAA goal)
- **Color Independence**: Information not conveyed by color alone
- **Audio Control**: Auto-playing audio can be paused, stopped, or muted
- **Text Resize**: Text can be resized up to 200% without loss of functionality
- **Images of Text**: Avoid images of text except for logos or essential graphics

### 2. Operable

#### 2.1 Keyboard Accessible
- **Keyboard Navigation**: All functionality available via keyboard
- **Focus Management**: Logical tab order and visible focus indicators
- **Keyboard Shortcuts**: No conflicting keyboard shortcuts
- **Character Key Shortcuts**: Single character shortcuts can be disabled/remapped
- **Focus Order**: Tab order follows logical content sequence

#### 2.2 Enough Time
- **Time Limits**: Users can extend, adjust, or turn off time limits
- **Auto-refresh**: Auto-refreshing content can be paused or controlled
- **Session Timeout**: Users warned before session timeout with option to extend
- **Interruptions**: Users can postpone or suppress non-emergency interruptions
- **Re-authentication**: Data preserved when session expires during form completion

#### 2.3 Seizures and Physical Reactions
- **Flashing Content**: No content flashes more than 3 times per second
- **Animation Control**: Users can disable non-essential animations
- **Motion Sensitivity**: Respect prefers-reduced-motion CSS media query
- **Parallax Scrolling**: Provide option to disable parallax effects
- **Auto-playing Media**: Auto-playing content can be paused or stopped

#### 2.4 Navigable
- **Skip Links**: Skip to main content and other page sections
- **Page Titles**: Descriptive and unique page titles
- **Link Purpose**: Link text clearly describes destination or function
- **Multiple Navigation**: Multiple ways to locate pages (menu, search, sitemap)
- **Headings and Labels**: Descriptive headings and form labels
- **Focus Visible**: Keyboard focus is clearly visible

#### 2.5 Input Modalities
- **Pointer Gestures**: All multipoint/path-based gestures have single-pointer alternative
- **Pointer Cancellation**: Up-event activation or abort/undo functionality
- **Label in Name**: Accessible name contains visible label text
- **Motion Actuation**: Device motion triggers can be disabled
- **Target Size**: Touch targets minimum 24x24 CSS pixels (44x44 recommended)

### 3. Understandable

#### 3.1 Readable
- **Language**: Page language programmatically identified
- **Language Changes**: Language changes within content identified
- **Pronunciation**: Pronunciation provided for ambiguous words (when needed)
- **Abbreviations**: Expanded form or definition provided for abbreviations
- **Reading Level**: Content written at appropriate reading level (9th grade target)

#### 3.2 Predictable
- **Consistent Navigation**: Navigation mechanisms consistent across pages
- **Consistent Identification**: Interface components identified consistently
- **Context Changes**: Context changes only on user request
- **Error Prevention**: Legal, financial, data commitments are reversible/confirmable
- **Help**: Context-sensitive help available

#### 3.3 Input Assistance
- **Error Identification**: Form errors clearly identified and described
- **Error Suggestions**: Suggestions provided for fixing input errors
- **Error Prevention**: Important submissions require confirmation or review
- **Accessible Authentication**: Authentication methods don't rely solely on cognitive tests
- **Redundant Entry**: Previously entered information is pre-populated or available

### 4. Robust

#### 4.1 Compatible
- **Valid Code**: HTML validates and uses proper semantics
- **Name, Role, Value**: All UI components expose name, role, state, and value
- **Status Messages**: Important status changes announced to screen readers
- **Custom Controls**: Custom UI components properly implement ARIA
- **Progressive Enhancement**: Core functionality works without JavaScript

## Automated Testing Requirements

### Playwright Accessibility Testing
- **axe-playwright Integration**: All pages tested with axe accessibility engine
- **Automated Scans**: Automated a11y testing in CI/CD pipeline
- **Custom Rules**: Project-specific accessibility rules configured
- **Regression Testing**: Visual regression testing for accessibility features
- **Performance Impact**: Accessibility features don't significantly impact performance

### Testing Tools and Coverage
- **axe-core**: Automated accessibility testing (WCAG 2.2 ruleset)
- **Pa11y**: Command-line accessibility testing
- **Lighthouse**: Accessibility audit scores (target: 95+)
- **Color Contrast**: Automated contrast ratio validation
- **Keyboard Navigation**: Automated keyboard accessibility testing

## Manual Testing Requirements

### Screen Reader Testing
- **NVDA**: Test with NVDA on Windows (free screen reader)
- **JAWS**: Test with JAWS if available (most common enterprise screen reader)
- **VoiceOver**: Test with VoiceOver on macOS/iOS
- **TalkBack**: Test with TalkBack on Android
- **Narrator**: Test with Windows Narrator

### Keyboard Navigation Testing
- **Tab Navigation**: Complete keyboard navigation without mouse
- **Skip Links**: Test skip navigation functionality
- **Focus Management**: Verify focus moves logically through interface
- **Keyboard Shortcuts**: Test all keyboard shortcuts and access keys
- **Modal Dialogs**: Test keyboard navigation in modal dialogs and popups

### Visual Testing
- **High Contrast Mode**: Test in Windows High Contrast mode
- **Browser Zoom**: Test at 200% browser zoom level
- **Custom Colors**: Test with custom browser color schemes
- **Dark Mode**: Test dark mode accessibility and contrast
- **Reduced Motion**: Test with prefers-reduced-motion enabled

## CLI and Script Accessibility Standards

### Command Line Interface (CLI) Accessibility
- **Screen Reader Compatibility**: CLI output works with screen readers
- **Color Independence**: Don't rely solely on color for important information
- **High Contrast**: Support high contrast terminal themes
- **Text Formatting**: Use semantic formatting (bold/italic) rather than just color
- **Progress Indicators**: Provide text-based progress indicators for long operations
- **Error Messages**: Clear, descriptive error messages with suggested solutions
- **Help Text**: Comprehensive help documentation with examples
- **Keyboard Navigation**: Support standard terminal keyboard shortcuts

### Script Output Accessibility
- **Structured Output**: Use consistent formatting for script output
- **Status Messages**: Clear status indicators (SUCCESS, ERROR, WARNING)
- **Progress Feedback**: Text-based progress indicators for long-running scripts
- **Error Handling**: Descriptive error messages with actionable information
- **Documentation**: Accessible documentation with usage examples
- **Logging**: Structured logging that works with assistive technologies

### Terminal and Console Standards
- **ANSI Compatibility**: Use ANSI escape codes appropriately
- **Graceful Degradation**: Work in terminals without color support
- **Font Compatibility**: Work with various terminal fonts and sizes
- **Screen Reader Output**: Ensure output is readable by screen reading software
- **Alternative Formats**: Provide output in multiple formats (JSON, CSV, plain text)

## Accessibility Metrics and Thresholds

### Automated Testing Scores

| Tool | Target Score | Tolerance | Red Flag |
|------|-------------|-----------|----------|
| **Lighthouse A11y** | 95+ | 90-94 | < 90 🚨 |
| **axe-core Violations** | 0 | 0 | > 0 🔥 |
| **Pa11y Errors** | 0 | 0 | > 0 ⚠️ |
| **Color Contrast** | 100% compliant | 95%+ | < 95% 📋 |

### Manual Testing Coverage

| Test Type | Target | Tolerance | Red Flag |
|-----------|--------|-----------|----------|
| **Screen Reader Testing** | 100% of UI | 90%+ | < 80% 🚨 |
| **Keyboard Navigation** | 100% functional | 95%+ | < 90% 🔥 |
| **Mobile A11y Testing** | 100% of mobile UI | 90%+ | < 80% ⚠️ |
| **High Contrast Testing** | 100% readable | 95%+ | < 90% 📋 |

### WCAG 2.2 Compliance

| Level | Target | Tolerance | Red Flag |
|-------|--------|-----------|----------|
| **Level A** | 100% compliant | 100% | < 100% 🚨 |
| **Level AA** | 100% compliant | 100% | < 100% 🔥 |
| **Level AAA** | 50% compliant | 30%+ | < 20% 📋 |

## Documentation Requirements

### Accessibility Documentation
- **A11y Statement**: Public accessibility statement with compliance status
- **Testing Results**: Documented results of accessibility testing
- **Known Issues**: List of known accessibility issues and remediation timeline
- **User Guides**: Accessibility features and how to use them
- **Feedback Process**: Process for users to report accessibility issues

### Developer Guidelines
- **Coding Standards**: Accessibility coding guidelines and best practices
- **Design System**: Accessible design system with WCAG-compliant components
- **Testing Procedures**: Step-by-step accessibility testing procedures
- **Remediation Guide**: Common accessibility issues and how to fix them
- **Training Materials**: Accessibility training resources for developers

## Communication Guidelines

### NEVER claim accessibility compliance without:
- Explicit confirmation that ALL automated accessibility tests are passing
- Evidence of manual accessibility testing results
- Verification of WCAG 2.2 Level AA compliance
- Documentation of screen reader and keyboard testing
- Confirmation of accessibility testing coverage

### Instead of saying "accessible" or "WCAG compliant," use specific language:
- "Automated accessibility tests passing but requires [manual testing] before production"
- "WCAG 2.2 Level A compliant but needs [Level AA validation] for production"
- "Screen reader compatible but requires [keyboard navigation testing] validation"
- "Accessibility baseline met but needs [user testing with disabilities] before production"
- "A11y tools passing but requires [accessibility audit] for full compliance"

## Implementation Checklist

### Pre-Production Accessibility Requirements
- [ ] All automated accessibility tests passing with 100% compliance
- [ ] Accessibility validation results documented and verified
- [ ] WCAG 2.2 Level AA compliance confirmed
- [ ] No accessibility findings blocking production deployment

### WCAG 2.2 Level AA Compliance Verification

#### 1. Perceivable
- [ ] **Text Alternatives**: All images have appropriate alt text or marked as decorative
- [ ] **Captions**: Pre-recorded video content has accurate captions
- [ ] **Audio Descriptions**: Video content includes audio descriptions
- [ ] **Color Contrast**: Minimum 4.5:1 for normal text, 3:1 for large text
- [ ] **Text Resize**: Text resizable to 200% without loss of functionality
- [ ] **Semantic Structure**: Proper HTML heading hierarchy (h1-h6) and landmarks
- [ ] **Form Labels**: All form inputs have programmatically associated labels

#### 2. Operable
- [ ] **Keyboard Navigation**: All functionality available via keyboard
- [ ] **Focus Management**: Logical tab order and visible focus indicators
- [ ] **Time Limits**: Users can extend, adjust, or turn off time limits
- [ ] **Seizure Prevention**: No content flashes more than 3 times per second
- [ ] **Skip Links**: Skip to main content and other page sections
- [ ] **Page Titles**: Descriptive and unique page titles
- [ ] **Target Size**: Touch targets minimum 24x24 CSS pixels

#### 3. Understandable
- [ ] **Language**: Page language programmatically identified
- [ ] **Consistent Navigation**: Navigation mechanisms consistent across pages
- [ ] **Error Identification**: Form errors clearly identified and described
- [ ] **Error Suggestions**: Suggestions provided for fixing input errors
- [ ] **Context Changes**: Context changes only on user request

#### 4. Robust
- [ ] **Valid Code**: HTML validates and uses proper semantics
- [ ] **Name, Role, Value**: All UI components expose name, role, state, and value
- [ ] **Status Messages**: Important status changes announced to screen readers
- [ ] **Progressive Enhancement**: Core functionality works without JavaScript

### Automated Testing Validation
- [ ] **axe-playwright**: All pages tested with zero violations
- [ ] **Lighthouse Accessibility**: Score of 95+ achieved
- [ ] **Pa11y**: Command-line testing completed with zero errors
- [ ] **Color Contrast**: 100% compliance with contrast requirements
- [ ] **Custom Rules**: Project-specific accessibility rules passing
- [ ] **CI/CD Integration**: Automated a11y testing in pipeline

### Manual Testing Completion

#### Screen Reader Testing
- [ ] **NVDA**: Tested with NVDA on Windows
- [ ] **JAWS**: Tested with JAWS (if available)
- [ ] **VoiceOver**: Tested with VoiceOver on macOS/iOS
- [ ] **TalkBack**: Tested with TalkBack on Android
- [ ] **Narrator**: Tested with Windows Narrator

#### Keyboard Navigation Testing
- [ ] **Tab Navigation**: Complete keyboard navigation without mouse
- [ ] **Skip Links**: Skip navigation functionality tested
- [ ] **Focus Management**: Focus moves logically through interface
- [ ] **Keyboard Shortcuts**: All shortcuts and access keys tested
- [ ] **Modal Dialogs**: Keyboard navigation in modals and popups tested

#### Visual and Environmental Testing
- [ ] **High Contrast Mode**: Tested in Windows High Contrast mode
- [ ] **Browser Zoom**: Tested at 200% browser zoom level
- [ ] **Custom Colors**: Tested with custom browser color schemes
- [ ] **Dark Mode**: Dark mode accessibility and contrast verified
- [ ] **Reduced Motion**: Tested with prefers-reduced-motion enabled

### CLI and Script Accessibility (if applicable)
- [ ] **Screen Reader Compatibility**: CLI output works with screen readers
- [ ] **Color Independence**: Important information not conveyed by color alone
- [ ] **High Contrast Support**: Supports high contrast terminal themes
- [ ] **Text Formatting**: Semantic formatting used (bold/italic vs. color only)
- [ ] **Progress Indicators**: Text-based progress indicators implemented
- [ ] **Error Messages**: Clear, descriptive error messages with solutions
- [ ] **Help Documentation**: Comprehensive, accessible help text

### Coverage and Metrics Validation
- [ ] **Lighthouse A11y Score**: 95+ achieved
- [ ] **Screen Reader Testing**: 100% of UI tested
- [ ] **Keyboard Navigation**: 100% functional coverage
- [ ] **Mobile A11y Testing**: 100% of mobile UI tested
- [ ] **High Contrast Testing**: 100% readable in high contrast mode
- [ ] All accessibility metrics meet defined thresholds
- [ ] No red flag accessibility indicators present

### Documentation and Compliance
- [ ] **Accessibility Statement**: Public accessibility statement published
- [ ] **Testing Results**: Documented results of all accessibility testing
- [ ] **Known Issues**: List of known issues with remediation timeline
- [ ] **User Guides**: Documentation of accessibility features
- [ ] **Developer Guidelines**: Accessibility coding standards documented
- [ ] **Feedback Process**: Process for reporting accessibility issues established

### Communication and Sign-off
- [ ] Accessibility results documented with evidence
- [ ] Accessibility limitations or caveats clearly stated
- [ ] Specific language used (no premature accessibility compliance claims)
- [ ] Accessibility gaps identified and remediation plan documented
- [ ] Accessibility review sign-off obtained from accessibility team/expert
- [ ] User testing with people with disabilities completed (when possible)

## Key Accessibility Principles

- Accessibility is designed in from the start, not retrofitted
- All accessibility features must be tested with actual assistive technologies
- Automated testing catches ~30% of issues; manual testing is essential
- Users with disabilities should be involved in testing when possible
- Accessibility benefits everyone, not just users with disabilities
- Legal compliance is the minimum standard, not the goal
- Accessibility is an ongoing process, not a one-time checklist
- Performance and accessibility must be balanced, not traded off
- Inclusive design creates better experiences for all users
- Accessibility documentation helps users discover and use features