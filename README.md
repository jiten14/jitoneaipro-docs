# JitoneAi Pro Documentation

Supercharge your FilamentPHP applications with **JitoneAi Pro**, the ultimate AI-powered premium add-on designed to revolutionize form-based workflows. Whether you're a developer, content creator, or business owner, JitoneAi Pro seamlessly integrates advanced AI functionalities directly into your Filament forms, enabling effortless content generation, SEO optimization, transcription, text-to-audio conversion, and AI-driven image creation—all within your Laravel projects.

With over 25 pre-built AI content templates, dynamic text enhancement tools, and seamless integration for OpenAI-powered AI fields, **JitoneAi Pro** empowers users to create, modify, and optimize content with ease. From generating SEO-friendly meta descriptions to transforming audio files into text or converting text into speech, this powerful add-on enhances productivity and streamlines AI-driven automation.

Built with flexibility in mind, **JitoneAi Pro** allows developers to enhance existing Filament form fields with AI or add dedicated AI-powered fields tailored for specific use cases. Whether you need AI-assisted text input, automated image generation, or advanced audio processing, JitoneAi Pro offers a seamless, plug-and-play experience that takes FilamentPHP applications to the next level.

## Key Features

![AI Content Generator](https://raw.githubusercontent.com/jiten14/jitoneaipro-docs/main/images/Generate-Text.jpg)

### AI-Powered Content Generation

Effortlessly generate high-quality text content using over 25+ AI-powered templates tailored for different use cases, including blog writing, social media posts, product descriptions, email drafts, and more. Customize the tone, style, and length of the generated content to suit your specific needs. Whether you need long-form articles or short, engaging snippets, JitoneAi Pro delivers fast and accurate AI-generated text directly within your FilamentPHP forms.

![AI Image Generator](https://raw.githubusercontent.com/jiten14/jitoneaipro-docs/main/images/Generate-Image.jpg)

### AI Image Generator

Transform text descriptions into stunning visuals with the built-in AI image generator. With 25+ pre-defined templates designed for different use cases, you can generate unique and professional-quality images for blog posts, advertisements, product showcases, and social media content. Simply input a text prompt, select an image size, and let AI create the perfect visual for your project.

![AI Text to Speach](https://raw.githubusercontent.com/jiten14/jitoneaipro-docs/main/images/Transcribe.jpg)

### AI-Powered Audio Transcription

Convert uploaded audio files into accurate, structured text in seconds. JitoneAi Pro’s transcription feature supports various audio formats and uses AI-driven speech recognition to deliver precise transcriptions. This is ideal for podcasters, content creators, and professionals who need to convert interviews, meetings, or lectures into editable text without manual effort.

![AI Text to Speach](https://raw.githubusercontent.com/jiten14/jitoneaipro-docs/main/images/Generate-Audio.jpg)

### Text-to-Audio Conversion

Transform written content into natural-sounding AI-generated speech. Whether you need to create voiceovers for videos, audiobooks, or accessibility features, JitoneAi Pro’s text-to-audio conversion tool provides high-quality AI voices that bring your content to life. Select from different voice styles and languages to match your brand’s tone and audience preferences.

### Advanced Text Modification Tools

Enhance your written content with a powerful set of AI-driven text transformation tools. Modify, refine, expand, shorten, summarize, translate, or correct grammar with a single click. This feature allows users to optimize existing content for readability, SEO, or engagement. Whether you need to rephrase text to improve clarity or simplify complex sentences, JitoneAi Pro ensures your content is polished and professional.

### SEO Meta Description Generator

Automatically generate SEO-friendly meta descriptions for web pages, blog posts, and product listings. By analyzing your content, JitoneAi Pro crafts compelling and keyword-rich descriptions that improve search engine visibility and click-through rates. Save time on manual meta tag writing and let AI generate optimized descriptions that align with best SEO practices.

These features collectively empower developers, marketers, and content creators to seamlessly integrate AI into their FilamentPHP applications, making content creation, optimization, and automation more efficient than ever.

## About the License

JitoneAi Pro offers a **one-time payment** with **lifetime updates** and **priority support**. It can be used on **unlimited domains**, making it the perfect choice for developers, marketers, and creators looking to elevate their digital projects with cutting-edge AI technology.

## How to Use

After successful installation, you can start adding AI functionality to your FilamentPHP forms. Refer to our comprehensive user guide for detailed instructions on leveraging each feature of JitoneAi Pro in your projects.

## Installation

1. After purchase, you will receive the package as a zip file via email or can download it instantly.
2. Once downloaded, create a **Packages** folder in the root directory of your Laravel project.
3. Extract the zip file and paste the **jiten14** folder from the downloaded zip into the **Packages** folder.
4. Update your root **composer.json** file by adding the following repository configuration:
   ```json
   "repositories": [
       {
           "type": "path",
           "url": "packages/jiten14/jitoneai-pro"
       }
   ]
   ```
5. Run the following command in your project's root directory terminal to install the package:
   ```bash
   composer require jiten14/jitoneai-pro:1.0.0
   ```
6. After installation, set up the package by running:
   ```bash
   jitoneai-pro:install
   ```
7. When prompted, provide your **purchased email**, **license key** (sent via email), and **domain name** (or project name if installing locally).

## Usage

### Configuration

The installation command will:
- Publish the configuration file for **JitoneAI Pro** Settings
- Publish the configuration file for **openai-php/laravel** Settings
- Create a symbolic link for storage

We use openai-php/laravel package to connect with OpenAI API. Blank environment variables for the OpenAI API key and organization id are already appended to your .env file, Add your API key here:

```env
OPENAI_API_KEY=sk-...
OPENAI_ORGANIZATION=org-...
```

The **config/jitoneai-pro.php** file allows you to set default values and templates:
- Set default AI models, max tokens, and temperature
- Configure image generation settings
- Add custom content templates with category & placeholder

### Adding AI to Built-in Filament Form Fields

You can add AI generation capabilities to TextInput, Textarea, and RichEditor fields using the **withAI()** method:

```php
use Filament\Forms\Components\TextInput;
use Filament\Forms\Components\Textarea;
use Filament\Forms\Components\RichEditor;

TextInput::make('title')
    ->withAI()

Textarea::make('description')
    ->withAI()

RichEditor::make('content')
    ->withAI()
```

### Using Dedicated AI Fields

#### AITextField

Without Options:
```php
use Jiten14\JitoneAiPro\Forms\Components\AITextField;

AITextField::make('content')->withAI()
```

With Options:
```php
AITextField::make('content')
    ->withAI([
        'model' => 'gpt-4',
        'max_tokens' => 300,
        'temperature' => 0.6,
    ])
```

#### AIFileUpload for Image Generation

Without Options:
```php
use Jiten14\JitoneAiPro\Forms\Components\AIFileUpload;

AIFileUpload::make('image')
    ->imageAI()
```

With Options:
```php
AIFileUpload::make('image')
    ->imageAI([
        'size' => '1024x1024',
    ])
```

### Additional AI-Enabled Fields

#### TextInput with AI Optimization
```php
use Filament\Forms\Components\TextInput;

TextInput::make('title')
    ->withAI([
        'optimize' => true,
    ])
    ->required()
```

#### AIAudio for Audio Processing
```php
use Jiten14\JitoneAiPro\Forms\Components\AIAudio;

AIAudio::make('audio')
    ->label('Audio File')
    ->withAI([
        'reference_field' => 'description',
    ])
    ->columnSpanFull()
```

#### AIMeta for SEO Optimization
```php
use Jiten14\JitoneAiPro\Forms\Components\AIMeta;

AIMeta::make('seo_meta')
    ->label('Meta Description')
    ->withAI([
        'reference_field' => 'description',
    ])
    ->required()
    ->columnSpanFull()
```

## Usage for End-Users

### Generating Content

1. In a form with AI-enabled fields, users will see a "Generate with AI" link right upper to the field.
2. Clicking this link opens a modal where users can:
   - Enter a custom prompt
   - Choose from pre-defined templates (if configured)
   - Use existing content for modification
3. If modifying existing content, users can choose to:
   - Refine: Improve the existing text
   - Expand: Add more details to the existing text
   - Shorten: Summarize the existing text
4. After entering the prompt, selecting a template, or choosing a modification option, click "Generate" to create or modify the content.
5. The generated or modified content will be inserted into the form field.

### Generating Images

1. For fields with AI image generation, users will see a "Generate with AI" link right upper to the upload field.
2. Clicking this link opens a modal where users can:
   - Describe the image they want to generate
   - Choose from pre-defined image prompts (if configured)
   - Select the desired image size (if multiple options are provided)
3. After entering the description, selecting a template, and choosing the size, click "Generate" to create the image.
4. The generated image will be uploaded and associated with the form field.

### Additional Features

1. **Transcribe Function**: End users can transcribe audio to text.
   - Upload audio in the modal
   - Get AI-generated text in the concerned field

2. **Modify Existing Text**: Users can perform various modifications on existing text:
   - Translate
   - Summarize
   - Correct Grammar
   - Optimize

3. **Convert Text to Audio**: Users can convert written text into audio format.
4. **SEO Meta Description**: Users can generate SEO meta descriptions from long-form content.

## Support

[Create Support Ticket](https://support.jiten.one/app)

After activation of your license through above installation steps, your user account will be created automatically & you can login with your email (added during purchase) & password is your license key (You can change password, after 1st login) & create support ticket.

Additionally, if you are facing issues with installation or have presale questions, send an email to support@jiten.one.