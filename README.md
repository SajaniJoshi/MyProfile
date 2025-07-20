# Sajani Joshi - Portfolio Website

A modern, responsive portfolio website built with Vue.js 3 and Vuetify, featuring an integrated AI career conversation chatbot.

## 🚀 Features

- **Modern Vue.js 3 Application** - Built with Composition API and Vite
- **Responsive Design** - Mobile-first approach with Vuetify UI framework
- **AI Chat Integration** - Embedded Gradio chatbot for career conversations
- **Professional Navigation** - Clean navigation with work and about/contact sections
- **Social Media Integration** - LinkedIn, Instagram, and Facebook links
- **Docker Support** - Containerized deployment with Nginx
- **Real-time Updates** - Dynamic greeting messages based on time of day

## 🛠️ Tech Stack

- **Frontend**: Vue.js 3, Vuetify 3, Vite
- **UI Framework**: Material Design with Vuetify
- **Icons**: Material Design Icons (MDI)
- **AI Chat**: Gradio integration via iframe
- **Deployment**: Docker, Nginx
- **Linting**: ESLint, Oxlint

## 📦 Installation

### Prerequisites

- Node.js 20+ 
- npm or yarn

### Setup

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd MyProfile
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Start development server**
   ```bash
   npm run dev
   ```

4. **Open your browser**
   Navigate to `http://localhost:5173`

## 🏗️ Build & Deployment

### Development

```bash
# Start development server with hot reload
npm run dev

# Preview production build
npm run preview
```

### Production

```bash
# Build for production
npm run build

# Lint and fix code
npm run lint
```

### Docker Deployment

```bash
# Build Docker image
docker build -t sajani-portfolio .

# Run container
docker run -p 80:80 sajani-portfolio
```

## 📁 Project Structure

```
vueProject/
├── src/
│   ├── components/
│   │   ├── NavBar.vue              # Navigation bar component
│   │   ├── GradioChatInterface.vue # AI chat integration
│   │   └── icons/                  # Icon components
│   ├── assets/                     # Static assets
│   ├── App.vue                     # Main application component
│   └── main.js                     # Application entry point
├── public/                         # Public assets
├── Dockerfile                      # Docker configuration
├── nginx.conf                      # Nginx server configuration
└── package.json                    # Dependencies and scripts
```

## 🎨 Key Components

- **NavBar**: Professional navigation with social media links
- **GradioChatInterface**: Embedded AI chatbot for career guidance
- **App.vue**: Main application with dynamic greeting system

## 🔧 Configuration

### Environment Variables

No environment variables are currently required. The AI chat interface is embedded via iframe from Hugging Face Spaces.

### Customization

- Update personal information in `src/components/NavBar.vue`
- Modify the AI chat URL in `src/components/GradioChatInterface.vue`
- Customize styling in component `<style>` sections

## 📱 Responsive Design

The application is fully responsive and optimized for:
- Desktop (1200px+)
- Tablet (768px - 1199px)
- Mobile (< 768px)

## 🚀 Deployment Options

1. **Static Hosting**: Deploy the `dist` folder to services like Netlify, Vercel, or GitHub Pages
2. **Docker**: Use the provided Dockerfile for containerized deployment
3. **Traditional Server**: Serve the built files with any web server

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Run linting: `npm run lint`
5. Submit a pull request

## 📄 License

This project is private and proprietary.

## 👤 Author

**Sajani Joshi**
- LinkedIn: [Sajani Joshi](https://linkedin.com)
- Instagram: [@sajanijoshi](https://instagram.com)
- Facebook: [Sajani Joshi](https://facebook.com)

---

Built with ❤️ using Vue.js and Vuetify
