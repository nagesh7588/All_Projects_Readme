# Motivational Quotes Web Application

A beautiful, responsive web application that displays inspirational quotes in both Hindi and English. Built with modern web technologies and optimized for Azure App Service deployment.

## 🌟 Features

- **Bilingual Support**: Display quotes in both Hindi and English
- **Beautiful UI/UX**: Modern gradient design with smooth animations
- **Interactive Elements**: 
  - Language switching with smooth transitions
  - Quote refresh functionality
  - Copy to clipboard feature
  - Share functionality (with native Web Share API support)
- **Responsive Design**: Works perfectly on all devices (mobile, tablet, desktop)
- **Accessibility**: Full keyboard navigation and screen reader support
- **PWA Ready**: Service Worker for offline functionality
- **Azure Optimized**: Ready for deployment on Azure App Service

## 🎨 Design Features

- Gradient backgrounds with floating animations
- Smooth CSS transitions and hover effects
- Font Awesome icons for enhanced UI
- Google Fonts (Poppins & Noto Sans Devanagari for Hindi)
- Dark mode support
- High contrast mode support
- Reduced motion support for accessibility

## 🚀 Technology Stack

- **Frontend**: HTML5, CSS3, Vanilla JavaScript
- **Backend**: Python with Flask (for Azure deployment)
- **Server**: Gunicorn WSGI server
- **Fonts**: Google Fonts (Poppins, Noto Sans Devanagari)
- **Icons**: Font Awesome 6
- **Deployment**: Azure App Service compatible

## 📱 Interaction Features

### Keyboard Shortcuts
- `Space` or `R`: Get new quote
- `H`: Switch to Hindi
- `E`: Switch to English
- `C`: Copy current quote
- `S`: Share current quote

### Touch Gestures
- **Swipe Right**: Switch to Hindi
- **Swipe Left**: Switch to English
- **Swipe Up**: Get new quote

## 🌐 Deployment on Azure App Service

### Prerequisites
- Azure account
- Azure CLI or Azure Portal access

### Steps to Deploy

1. **Prepare the application**
   ```bash
   pip install -r requirements.txt
   ```

2. **Deploy to Azure App Service**
   - Create a new Web App in Azure Portal
   - Choose Python 3.11 runtime
   - Deploy using Git, GitHub Actions, or ZIP deployment
   - The app will automatically start using Gunicorn

3. **Environment Configuration**
   - The app uses `os.environ.get('PORT')` for Azure's dynamic port assignment
   - No additional environment variables needed

### Azure App Service Configuration
- **Runtime**: Python 3.11
- **Startup Command**: `gunicorn app:app`
- **Platform**: Linux (recommended for Python)
- **Pricing Tier**: Free (F1) tier supported

## 📂 Project Structure

```
azr_tstng_app/
├── index.html          # Main HTML file
├── styles.css          # All CSS styles and animations
├── script.js           # JavaScript functionality
├── app.py             # Flask server for Azure
├── requirements.txt    # Python dependencies
├── runtime.txt        # Python version specification
├── Procfile           # Deployment configuration
├── azure-config.yml   # Azure deployment settings
├── sw.js              # Service Worker for PWA
└── README.md          # This file
```

## 🎯 Features in Detail

### Quote Management
- 20+ carefully curated motivational quotes
- Random quote selection ensuring no immediate repeats
- Automatic quote refresh on page visibility change
- Local storage for better user experience

### UI/UX Enhancements
- Loading animations and state management
- Toast notifications for user feedback
- Smooth language switching
- Responsive breakpoints for all screen sizes
- Print-friendly styles

### Performance Optimizations
- CSS Grid and Flexbox for efficient layouts
- CSS custom properties for consistent theming
- Optimized animations with `transform` and `opacity`
- Service Worker caching for offline support

## 🎨 Customization

### Adding New Quotes
Edit the `quotes` array in `script.js`:

```javascript
const quotes = [
    {
        hindi: "Your Hindi quote here",
        english: "Your English quote here",
        author: "Author Name"
    },
    // Add more quotes...
];
```

### Styling Customization
Modify CSS custom properties in `styles.css`:

```css
:root {
    --primary-gradient: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    --secondary-gradient: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
    /* Customize other variables... */
}
```

## 🔧 Local Development

1. **Install Python dependencies**
   ```bash
   pip install -r requirements.txt
   ```

2. **Start the development server**
   ```bash
   python app.py
   ```

3. **Open your browser**
   Navigate to `http://localhost:5000`

4. **Make changes**
   The server serves static files, so refresh the browser to see changes.

## 🌟 Browser Support

- Chrome 90+
- Firefox 88+
- Safari 14+
- Edge 90+
- Mobile browsers (iOS Safari, Chrome Mobile)

## 📝 License

MIT License - feel free to use this project for your own purposes.

## 🤝 Contributing

Feel free to fork this project and submit pull requests for improvements!

## 📞 Support

If you encounter any issues with deployment or functionality, please check:
1. Python version compatibility (3.11 recommended)
2. Azure App Service logs
3. Browser console for any JavaScript errors

---

Made with ❤️ for spreading daily motivation and inspiration!
