# 🤖 GROQ AI API Integration in Sketchware-Pro

## 📋 Overview

This implementation adds intelligent error explanation functionality to Sketchware-Pro using the Groq API. Users can get detailed explanations and solutions for programming errors through AI.

## 🏗️ Implementation Architecture

### Main Classes

#### 1. **GroqConfig.java**
- **Location**: `app/src/main/java/pro/sketchware/utility/GroqConfig.java`
- **Function**: Manages Groq API settings
- **Features**:
  - Save/retrieve API key
  - Enable/disable functionality
  - Check API availability
  - Environment variable support as fallback
  - AI response language configuration
  - Supports 13 different languages

#### 2. **GroqErrorExplainer.java**
- **Location**: `app/src/main/java/pro/sketchware/utility/GroqErrorExplainer.java`
- **Function**: Communicates with the Groq API
- **Features**:
  - Sends errors for AI analysis
  - Builds custom prompts
  - Processes API responses
  - Handles network errors
  - Supports multiple response languages
  - Language-specific instructions

#### 3. **ErrorHelper.java**
- **Location**: `app/src/main/java/pro/sketchware/utility/ErrorHelper.java`
- **Function**: Interface for error display
- **Features**:
  - Shows error dialogs with AI
  - Material Design integration
  - Confirmation options
  - Fallback for original errors

#### 4. **ManageGroqActivity.java**
- **Location**: `app/src/main/java/pro/sketchware/activities/settings/ManageGroqActivity.java`
- **Function**: API configuration interface
- **Features**:
  - Configures API key
  - Selects AI response language
  - Tests connection
  - Opens documentation
  - Input validation

#### 5. **GroqExampleUsage.java**
- **Location**: `app/src/main/java/pro/sketchware/utility/GroqExampleUsage.java`
- **Function**: Examples of functionality usage
- **Features**:
  - Demonstrations of different scenarios
  - Asynchronous task integration
  - Prompt customization
  - Error handling

### Interface Files

#### 1. **Configuration Layout**
- **File**: `app/src/main/res/layout/manage_library_manage_groq.xml`
- **Characteristics**:
  - Material Design 3
  - Switch to enable/disable
  - Secure field for API key
  - Spinner for language selection
  - Test and documentation buttons
  - Explanatory information

#### 2. **Localization Strings**
- **File**: `app/src/main/res/values/strings.xml`
- **Additions**: 55 new strings for the functionality
- **Languages**: Supports Portuguese and English
- **Categories**: Configuration, error messages, UI, language selection

## 🔧 Setup and Usage

### 1. Initial Configuration

1. **Access Settings**:
   - Main menu → Settings → Groq AI Settings

2. **Get API Key**:
   - Visit [console.groq.com/keys](https://console.groq.com/keys)
   - Create a free account
   - Generate API key

3. **Configure in App**:
   - Enable "Enable Groq AI" switch
   - Enter API key
   - Select AI response language
   - Test connection

### 2. Functionality Usage

#### Simple Method
```java
// Show error with AI explanation
ErrorHelper.showError(context, errorMessage, "Error", true);
```

#### Method with Confirmation
```java
// Show error with AI option
ErrorHelper.showErrorWithConfirmation(context, errorMessage, "Error", () -> {
    // Callback when user confirms
});
```

#### Direct API Usage
```java
GroqErrorExplainer explainer = new GroqErrorExplainer(context);
explainer.explainError(errorMessage, explanation -> {
    // Process received explanation
});
```

## 🌍 Language Configuration

### Supported Languages
The Groq AI functionality supports 13 different languages for AI responses:

1. **Brazilian Portuguese** (Default) - `pt-BR`
2. **English** - `en`
3. **Spanish** - `es`
4. **French** - `fr`
5. **German** - `de`
6. **Italian** - `it`
7. **Japanese** - `ja`
8. **Korean** - `ko`
9. **Chinese (Simplified)** - `zh-CN`
10. **Chinese (Traditional)** - `zh-TW`
11. **Russian** - `ru`
12. **Arabic** - `ar`
13. **Hindi** - `hi`

### How to Configure Language
1. Access **Settings → Groq AI Settings**
2. In the "Response Language" section, use the spinner to select the desired language
3. The selected language will be used for all AI error explanations
4. The setting is automatically saved

### Default Behavior
- **Default language**: Brazilian Portuguese
- **Persistence**: Selection is maintained between sessions
- **Fallback**: If no configuration, uses Brazilian Portuguese

## 🔒 Security and Privacy

### Secure Storage
- API key stored in private SharedPreferences
- Environment variable support as an alternative
- User input validation

### Secure Communication
- HTTPS requests to Groq API
- Appropriate authorization headers
- Configured timeout to prevent freezes

### Privacy
- Error data sent only to Groq API
- No personal data collection
- User controls when to use the functionality

## 🌐 System Integration

### Integration Points
1. **Compilation System**: Compilation errors can be explained
2. **Runtime Errors**: Errors during app execution
3. **Settings**: Dedicated interface for configuration
4. **Error Logs**: Integration with existing log system

### Settings Menu
- Added "Groq AI Settings" item to the main menu
- Icon: `ic_mtrl_settings_applications`
- Description: "Configure Groq AI for intelligent error explanations"

## 📱 User Interface

### Configuration Screen
- **Design**: Material Design 3
- **Elements**:
  - Groq logo with emoji 🤖
  - Switch to enable/disable
  - Secure text field for API key
  - Spinner for response language selection
  - "Open Documentation" button
  - "Test Connection" button
  - Informative section

### Error Dialogs
- **Types**:
  - Simple dialog (without AI)
  - Dialog with AI explanation
  - Confirmation dialog with AI option
- **Characteristics**:
  - Loading state during analysis
  - "Show Original" button to see original error
  - Messages in Portuguese/English

## 🚀 Advanced Features

### 1. Custom Context
```java
String context = "This error occurred during the compilation of an Android project.";
explainer.explainError(errorMessage, context, callback);
```

### 2. Availability Check
```java
if (ErrorHelper.isGroqAvailable(context)) {
    // Use AI explanation
} else {
    // Show original error
}
```

### 3. Error Handling
- Automatic fallback to original error
- Informative messages when API is unavailable
- Detailed logs for debugging

## 📊 Usage Examples

### Example 1: Compilation Error
```java
try {
    // Code that might fail
} catch (Exception e) {
    ErrorHelper.showError(this, e.getMessage(), "Compilation Error", true);
}
```

### Example 2: Runtime Error
```java
if (ErrorHelper.isGroqAvailable(this)) {
    ErrorHelper.showError(this, errorMessage, "Error", true);
} else {
    ErrorHelper.showError(this, errorMessage, "Error");
}
```

### Example 3: Asynchronous Integration
```java
new Thread(() -> {
    try {
        // Asynchronous task
    } catch (Exception e) {
        runOnUiThread(() -> {
            ErrorHelper.showError(this, e.getMessage(), "Task Error", true);
        });
    }
}).start();
```

### Example 4: Usage with Different Languages
```java
// The AI will respond in the language configured by the user
// If the user configured English, the response will be in English
// If configured Portuguese, the response will be in Portuguese
ErrorHelper.showError(this, errorMessage, "Error", true);
```

## 🔧 Technical Configuration

### Dependencies
- **OkHttp**: For HTTP requests
- **Gson**: For JSON parsing
- **Material Design**: For interface

### Permissions
- `INTERNET`: For API communication
- `ACCESS_NETWORK_STATE`: To check connectivity

### Settings
- **API URL**: `https://api.groq.com/openai/v1/chat/completions`
- **Model**: `llama-3.3-70b-versatile`
- **Timeout**: Configured in OkHttpClient

## 🐛 Error Handling

### Error Scenarios
1. **API not configured**: Informative message
2. **No connection**: Fallback to original error
3. **Invalid API key**: Specific error dialog
4. **Timeout**: Timeout message
5. **Parsing error**: Fallback to original error

### Logs
- Detailed logs for debugging
- Specific tags for each class
- Error information without sensitive data

## 🔮 Future Improvements

### Planned Features
1. **Error history**: Save previous explanations
2. **Prompt customization**: Allow custom prompts
3. **Integration with more APIs**: Support for other AIs
4. **Code analysis**: Suggestions for code improvement
5. **Automatic language detection**: Automatically detect error language

### Optimizations
1. **Explanation caching**: Avoid repeated requests
2. **Data compression**: Reduce bandwidth usage
3. **Offline analysis**: Pre-defined explanations
4. **Economy mode**: Limit API usage

## 📝 API Documentation

### Endpoints Used
- **POST** `/openai/v1/chat/completions`
- **Headers**: `Content-Type: application/json`, `Authorization: Bearer {api_key}`
- **Body**: JSON with model, messages, and parameters

### Response Structure
```json
{
  "choices": [
    {
      "message": {
        "content": "Error explanation..."
      }
    }
  ]
}
```

### Limitations
- **Rate limiting**: Respect API limits
- **Prompt size**: Maximum tokens
- **Timeout**: 30 seconds per request

## 🤝 Contribution

### How to Contribute
1. Fork the repository
2. Create feature branch
3. Implement functionality
4. Test extensively
5. Submit pull request

### Code Standards
- Follow project's Java conventions
- Document public methods
- Use localization strings
- Implement error handling

## 📄 License

This implementation follows the same license as the Sketchware-Pro project.

---

**Developed with ❤️ for the Sketchware-Pro community**