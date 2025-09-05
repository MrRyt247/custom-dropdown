# Custom Dropdown Component

A modern, accessible dropdown component built with Svelte 5 and TypeScript. This component provides an intuitive selection interface with smooth animations and click-outside functionality.

## URLs
- [Live URL](https://vercel.com/mrryt247s-projects/svelte-custom-dropdown/CRuNaU6PHBQa7n7YgWXB6PAhpipg)
- [Project URL](https://github.com/MrRyt247/custom-dropdown)


## Features

- 🎯 Click-outside to close functionality
- ⚡ Smooth rotation animations for the chevron icon
- ✅ Visual indication of selected items
- 🎨 Custom styling with Comic Relief font
- 📱 Responsive design
- ♿ Accessible button elements
- 🔧 TypeScript support with proper type safety

## Technology Stack

- **Framework**: Svelte 5 (with new runes)
- **Language**: TypeScript
- **Styling**: CSS with nested selectors
- **Icons**: svelte-hero-icons
- **Font**: Comic Relief (@fontsource/comic-relief)

## Component Structure

```
src/
├── components/
│   └── CustomDropdown.svelte
├── data/
│   └── data.ts
└── types/
    └── dropdown.ts
```

## Getting Started

### Prerequisites

- Node.js (Latest LTS version recommended)
- npm or pnpm
- Svelte 5 project setup

### Installation

1. Install required dependencies:
```bash
npm install svelte-hero-icons @fontsource/comic-relief
```

2. Import the component in your Svelte file:
```svelte
<script lang="ts">
  import CustomDropdown from './components/CustomDropdown.svelte';
</script>

<CustomDropdown />
```

### Data Structure

The dropdown expects data in the following format:

```typescript
// data/data.ts
export const data = [
  {
    select: "Option 1", // Default selected value
    options: ["Option 1", "Option 2", "Option 3", "Option 4"]
  }
];
```

## Component API

### Props
Currently, the component uses imported data, but can be easily extended to accept props:

```typescript
interface DropdownProps {
  data: Array<{
    select: string;
    options: string[];
  }>;
  placeholder?: string;
  disabled?: boolean;
}
```

### State Management

The component uses Svelte 5's new runes for state management:

- `selected`: Currently selected option (reactive)
- `isOpened`: Dropdown open/close state (reactive)
- `dropdownRef`: DOM reference for click-outside detection

#### Smooth Animations
- Chevron icon rotates 180 degrees when opened
- Transition duration: 300ms with ease timing
- Display toggle for dropdown list (flex/none)

#### Visual Feedback
- Selected items show a checkmark (✓)
- Hover effects on buttons
- Border and background styling

## Styling Architecture

### CSS Structure
- Global reset with box-sizing
- Component-scoped styles
- Nested selectors for clean organization
- Responsive width (18em)

### Key Style Classes
- `.select`: Main container with relative positioning
- `.select-container`: Primary button with flex layout
- `ul`: Dropdown list with absolute positioning
- `button`: Individual option buttons with consistent spacing

## Customization

### Theming
```css
:root {
  --dropdown-border: solid 3px black;
  --dropdown-bg: transparent;
  --dropdown-radius: 10px;
  --selected-bg: black;
  --selected-color: white;
}
```

### Font Customization
Replace Comic Relief with your preferred font:
```typescript
import '@fontsource/your-font';
```

### Icon Customization
Replace ChevronDown with any icon from svelte-hero-icons:
```typescript
import { ChevronUp, CaretDown } from 'svelte-hero-icons';
```

## Accessibility Features

- Semantic button elements
- Proper ARIA attributes (can be extended)
- Keyboard navigation support (can be enhanced)
- Focus management
- Screen reader compatible structure

## Browser Support

- Modern browsers supporting ES2020+
- CSS Grid and Flexbox support required
- JavaScript enabled environments

## Contributing

Contributions are welcome! To contribute:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/dropdown-enhancement`)
3. Make your changes with proper TypeScript types
4. Test the component thoroughly
5. Submit a pull request with clear documentation

### Development Guidelines

- Follow TypeScript best practices
- Maintain component reactivity patterns
- Ensure accessibility standards
- Add proper error handling
- Write clear, self-documenting code
- Test across different browsers

## License

This component is available under the MIT License. Feel free to use, modify, and distribute as needed.

---

**Note**: This component is built with Svelte 5 and uses the new runes syntax. Ensure your project is compatible with Svelte 5 before implementation.