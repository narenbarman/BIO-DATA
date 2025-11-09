# Bio-App: Bio Data Management Application

## Project Overview

Bio-App is a React-based web application designed for creating, displaying, and printing bio data forms. It provides multiple format options for presenting personal information in a professional, printable layout optimized for A4 paper. The application supports form submission, data display in various formats, format switching, and print functionality.

### Key Features
- **Multi-Format Display**: Three distinct bio data formats (Format 1, Format 2, Format 3)
- **Form Submission**: Comprehensive form for entering personal, address, and professional information
- **Print Optimization**: A4 paper-optimized layouts with specific margins and fonts
- **Format Switching**: Seamless switching between display formats
- **Reset/Modify Actions**: Ability to reset data or modify existing entries
- **Responsive Design**: Clean, professional styling with color-coded sections

## Project Structure

### Components

#### App.js
The main application component that manages state and routing between different views.

**Key Functionality:**
- Manages `bioData` state (personal information object)
- Handles `submitted` state (form vs. display mode)
- Manages `format` state ('format1', 'format2', 'format3')
- Provides handlers for form submission, reset, modify, and format switching

**State Structure:**
```javascript
const [bioData, setBioData] = useState({
  name: '',
  contactNo: '',
  email: '',
  fathersName: '',
  presentAddress: { vill: '', po: '', ps: '', district: '', state: '', pin: '' },
  permanentAddress: { vill: '', po: '', ps: '', district: '', state: '', pin: '' },
  nationality: '',
  religion: '',
  dob: '',
  caste: '',
  gender: '',
  maritalStatus: '',
  educationalQualification: '',
  otherQualification: '',
  languageKnown: '',
  experience: '',
  experience1: '',
  experience2: '',
  date: '',
  place: ''
});
```

#### Form.jsx
A comprehensive form component for data entry.

**Features:**
- Personal information fields (name, contact, email, father's name, DOB)
- Address sections (present and permanent) with checkbox for same address
- Additional information (nationality, religion, caste, gender, marital status)
- Educational qualifications with multiple entries
- Professional experience fields
- Declaration section with date and place
- Image upload functionality

#### BioFormat1.tsx
First bio data display format with structured sections.

**Layout:**
- Personal information in a grid layout
- Address sections with field-based display
- Other information in a 2-column grid
- Academic and professional information in separate sections
- Declaration and signature section

#### BioFormat2.tsx
Second bio data display format with resume-style layout.

**Layout:**
- Tab-based navigation for format switching
- Personal information in a grid with optional image
- Academic information in a table format
- Professional information section
- Declaration section

#### BioFormat3.tsx
Third bio data display format with simple line-by-line layout.

**Layout:**
- Tab-based navigation for format switching
- All information displayed as "LABEL :- VALUE" lines
- Single container design
- Compact, document-style presentation

## Functionality

### Form Submission
1. User fills out the comprehensive form in `Form.jsx`
2. On submission, data is stored in `bioData` state
3. Application switches to display mode showing selected format

### Bio Data Display
- **Format 1**: Sectioned layout with borders and structured fields
- **Format 2**: Resume-style with table for education and grid for personal info
- **Format 3**: Simple line-by-line format inspired by document templates

### Format Switching
- Each format component includes tabs for switching between formats
- Cycling order: Format 1 → Format 2 → Format 3 → Format 1
- Maintains data integrity during switches

### Reset/Modify Actions
- **Reset**: Clears all data and returns to form view
- **Modify**: Returns to form view with existing data pre-populated
- **Print**: Triggers browser print dialog with optimized A4 layout

## Styling Details

### CSS Architecture
- Component-specific CSS files (Bio-Format1.css, Bio-Format2.css, Bio-Format3.css)
- Global styles in App.css and index.css
- Print-specific media queries for A4 optimization

### Key CSS Classes

#### Format 1 (Bio-Format1.css)
- `.bio-display`: Main container (148mm width, centered)
- `.format1-tabs`: Tab navigation for format switching
- `.format1-academic-section`: Academic information container
- `.format1-academic-field`: Individual field styling
- `.action-buttons`: Print/reset/modify buttons

#### Format 2 (Bio-Format2.css)
- `.bio-display`: Main container with tabs
- `.personal-information-section`: Personal info grid
- `.academic-display`: Table layout for education
- `.professional-section`: Experience section
- `.declaration-section`: Signature area

#### Format 3 (Bio-Format3.css)
- `.bio-display`: Compact container
- `.format3-tabs`: Format switching tabs
- `.bio-line`: Flex layout for label-value pairs
- `.label`, `.separator`, `.value`: Individual line components

### Print Styles
All formats include `@media print` rules optimized for A4 paper:

**Common Print Features:**
- Page size: A4
- Margins: 10-15mm (top/bottom), 15-25mm (left/right)
- Font: Times New Roman, serif
- Hide action buttons and tabs
- Compact spacing and smaller fonts

**Format-Specific Print Adjustments:**
- **Format 1**: Reduced margins, smaller fonts (9-10pt), hidden shadows
- **Format 2**: Similar to Format 1 with table optimizations
- **Format 3**: Most compact (9pt font, 1.1 line-height, minimal margins)

## Code Changes and Diffs

### Major Updates Applied

#### State Management (App.js)
- Added `experience1` and `experience2` fields to initial state
- Removed duplicate entries in reset function
- Updated format switching logic for 3 formats

#### CSS Optimizations
- **Margins and Spacing**: Reduced from pixels to millimeters for print accuracy
- **Font Sizes**: Decreased for A4 fit (e.g., headers from 24pt to 20pt)
- **Line Heights**: Tightened from 1.6 to 1.2 for compactness
- **Print Media Queries**: Added specific rules for each format

#### Component Updates
- **BioFormat1.tsx**: Renamed classes to `format1-*` to avoid conflicts
- **BioFormat2.css**: Fixed invalid CSS values (`margin-bottom: NONE` → `margin-bottom: 20px`)
- **BioFormat3.tsx**: Added new component with line-by-line layout

#### Print Optimization
- **Page Margins**: Asymmetric margins (larger left for binding)
- **Content Width**: Limited to 148mm for single-sided printing
- **Font Family**: Switched to Times New Roman for print
- **Element Hiding**: Action buttons and tabs hidden in print view

## Usage Instructions

### For Users

#### Getting Started
1. Clone the repository: `git clone <repo-url>`
2. Install dependencies: `npm install`
3. Start the application: `npm start`
4. Open http://localhost:3000 in your browser

#### Using the Application
1. **Fill the Form**: Complete all required fields in the bio data form
2. **Submit**: Click "Generate Bio Data" to view the formatted output
3. **Switch Formats**: Use tabs in each format to switch between Format 1, 2, and 3
4. **Print**: Click "Print Bio Data" for optimized A4 printing
5. **Modify**: Click "Modify" to edit existing data
6. **Reset**: Click "Create New" to start fresh

#### Print Setup
- Ensure printer settings are set to A4 paper
- Print styles automatically apply when using browser's print function
- Each format is optimized to fit on one A4 page

### For Developers

#### Adding New Formats
1. Create new component file (e.g., `BioFormat4.tsx`)
2. Create corresponding CSS file (`BioFormat4.css`)
3. Import and add to `App.js` conditional rendering
4. Update format switching logic
5. Add print media queries

#### Modifying Existing Styles
- Use unique class prefixes (e.g., `format1-*`, `format2-*`) to avoid conflicts
- Test print styles with browser's print preview
- Use millimeters (mm) for print-accurate measurements

#### State Management
- All bio data is stored in `App.js` state
- Form data flows through props to display components
- Reset/modify actions update state accordingly

## Dependencies

- **React**: ^17.0.2 (UI framework)
- **React DOM**: ^17.0.2 (DOM rendering)
- **React Scripts**: ^4.0.3 (build tools)
- **TypeScript**: For type safety in display components

## Browser Support

- Chrome 80+
- Firefox 75+
- Safari 13+
- Edge 80+

## Troubleshooting

### Common Issues

1. **CSS Not Applying**: Clear browser cache or hard refresh (Ctrl+F5)
2. **Print Layout Issues**: Check browser print preview settings
3. **Format Switching Not Working**: Ensure all components are properly imported in App.js
4. **ESLint Warnings**: Minor accessibility warnings for alt attributes (can be ignored)

### Development Tips

- Use React Developer Tools for component inspection
- Test print functionality with browser's print preview
- Validate A4 dimensions with ruler or measuring tool
- Check console for any runtime errors

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make changes with proper documentation
4. Test print functionality thoroughly
5. Submit a pull request

## License

This project is licensed under the MIT License - see the LICENSE file for details.