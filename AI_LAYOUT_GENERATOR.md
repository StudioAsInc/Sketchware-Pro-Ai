# 🤖 AI Layout Generator - Sketchware-Pro

## 📋 Overview

This new feature integrates Groq AI into Sketchware-Pro's XML editor, allowing users to generate Android XML layouts using natural language descriptions. Instead of manually editing XML, you can simply describe the desired layout, and the AI will automatically generate the code.

## ✨ Features

### 🎯 Intelligent Layout Generation
- **Natural Language Description**: Describe the layout you want to create
- **Automatic Generation**: The AI generates the complete XML code
- **Validation**: Automatic checking for circular dependencies
- **Seamless Integration**: Directly replaces the editor's content

### 🌍 Multi-language Support
- **13 Languages**: Portuguese, English, Spanish, French, German, Italian, Japanese, Korean, Chinese (Simplified and Traditional), Russian, Arabic, and Hindi
- **Configurable**: Choose the AI response language in the settings
- **Intelligent Prompts**: Language-specific instructions

### 🔧 Technical Resources
- **Responsive Layouts**: Generates layouts that follow Android best practices
- **Material Design**: Support for Material Design components
- **Unique IDs**: Automatically generates unique IDs for all elements
- **Accessibility**: Includes accessibility attributes where appropriate

## 🚀 How to Use

### 1. Access the Generator
1. Open the **Direct XML Editor**
2. Click the **🤖 Generate with AI** icon in the toolbar
3. The generation dialog will open

### 2. Describe the Layout
Type a detailed description of the layout you wish to create. Examples:

```
• Login screen with email and password fields
• Product list with images and prices
• Registration form with validation
• Dashboard with statistics cards
• Photo gallery in a grid
```

### 3. Generate and Apply
1. Click **"Generate Layout"**
2. Wait a few seconds while the AI processes
3. The XML code will be automatically inserted into the editor
4. Review and save changes

## ⚙️ Configuration

### Prerequisites
1. **Groq API Key**: Get a free key at [console.groq.com/keys](https://console.groq.com/keys)
2. **Configuration**: Go to Settings → Groq AI Settings
3. **Enable**: Activate the feature and enter your API key

### Language Configuration
1. Go to **Settings → Groq AI Settings**
2. Select the desired language in the "Response Language" spinner
3. The AI will respond in the chosen language

## 📱 User Interface

### Generation Dialog
- **Material Design 3**: Modern and intuitive interface
- **Prompt Field**: Text area for layout description
- **Examples**: Prompt suggestions for easier use
- **Progress**: Visual indicator during generation
- **Buttons**: Generate and Cancel

### Editor Integration
- **Toolbar Icon**: "Generate with AI" button with 🤖 icon
- **Automatic Replacement**: The generated XML replaces the current content
- **Feedback**: Success and error messages
- **Validation**: Check before saving

## 🔧 Technical Architecture

### Main Classes

#### 1. **GroqLayoutGenerator.java**
- **Location**: `app/src/main/java/pro/sketchware/utility/GroqLayoutGenerator.java`
- **Function**: Communicates with the Groq API for layout generation
- **Features**:
  - Building layout-specific prompts
  - HTTP communication with the Groq API
  - Parsing and cleaning XML responses
  - Multi-language support

#### 2. **AiLayoutGeneratorDialog.java**
- **Location**: `app/src/main/java/pro/sketchware/dialogs/AiLayoutGeneratorDialog.java`
- **Function**: User interface for layout generation
- **Features**:
  - Material Design 3 dialog
  - Input validation
  - Integration with GroqLayoutGenerator
  - Error handling and feedback

#### 3. **ViewCodeEditorActivity.java** (Modified)
- **Location**: `app/src/main/java/pro/sketchware/activities/editor/view/ViewCodeEditorActivity.java`
- **Modifications**:
  - Added "Generate with AI" button to the toolbar
  - Integration with AiLayoutGeneratorDialog
  - Automatic replacement of editor content

### Interface Files

#### 1. **Dialog Layout**
- **File**: `app/src/main/res/layout/dialog_ai_layout_generator.xml`
- **Characteristics**:
  - Material Design 3
  - Text field for prompt
  - Prompt examples
  - Progress indicator
  - Action buttons

#### 2. **AI Icon**
- **File**: `app/src/main/res/drawable/ic_mtrl_ai.xml`
- **Design**: Vector icon representing AI

#### 3. **Localization Strings**
- **File**: `app/src/main/res/values/strings.xml`
- **Additions**: 15 new strings for the functionality
- **Categories**: Titles, messages, buttons, errors

## 🎯 Usage Examples

### Example 1: Login Screen
**Prompt**: "Create a login screen with email and password fields, login button, and a link to recover password"

**Result**: XML Layout with:
- Vertical LinearLayout as container
- TextInputLayout for email
- TextInputLayout for password (with passwordToggleEnabled)
- MaterialButton for login
- TextView for recovery link

### Example 2: Product List
**Prompt**: "Create a product list with an image, title, price, and buy button"

**Result**: XML Layout with:
- RecyclerView or ScrollView
- CardView for each product
- ImageView for product image
- TextView for title and price
- Button for purchase

### Example 3: Dashboard
**Prompt**: "Create a dashboard with statistics cards in a 2x2 grid"

**Result**: XML Layout with:
- GridLayout or ConstraintLayout
- CardView for each statistic
- Icons and numbers
- Material Design colors

## 🔒 Security and Privacy

### Data Sent
- **Prompt only**: Only the layout description is sent to the API
- **No personal data**: No personal information is collected
- **No existing code**: The current code is not sent

### Storage
- **Local**: Settings saved locally on the device
- **API Key**: Securely stored in SharedPreferences
- **No cache**: No storage of generated layouts

## 🐛 Error Handling

### Error Scenarios
1. **API not configured**: Dialog to configure
2. **No connection**: Specific error message
3. **Invalid API key**: Error dialog
4. **Timeout**: Timeout message
5. **Empty prompt**: Input validation

### Fallbacks
- **API error**: Maintains the current editor content
- **No configuration**: Redirects to settings
- **Network failure**: Informative message

## 🔮 Future Improvements

### Planned Features
1. **Prompt History**: Save previous prompts
2. **Templates**: Pre-defined prompts for common layouts
3. **Real-time Preview**: Visualize layout before applying
4. **Intelligent Editing**: Modify existing layouts
5. **Context Analysis**: Consider the current layout

### Optimizations
1. **Response Caching**: Avoid repeated requests
2. **Compression**: Reduce bandwidth usage
3. **Offline Mode**: Basic prompts without internet
4. **Personalization**: User-customized prompts

## 📊 Metrics and Analytics

### Collected Data (Optional)
- **Feature usage**: Number of layouts generated
- **Layout types**: Categorization of prompts
- **Success rate**: Layouts generated vs. applied
- **Generation time**: API performance

### Privacy
- **Anonymous**: No personal identification
- **Optional**: User can disable
- **Local**: Data processed locally

## 🤝 Contribution

### How to Contribute
1. **Fork** the repository
2. **Create a branch** for the feature
3. **Implement** functionality
4. **Test** extensively
5. **Submit** pull request

### Code Standards
- Follow project's Java conventions
- Document public methods
- Use localization strings
- Implement error handling
- Test in different languages

## 📄 License

This implementation follows the same license as the Sketchware-Pro project.

---

**Developed with ❤️ for the Sketchware-Pro community**

*Transform your ideas into Android layouts with the power of AI!* 🤖✨