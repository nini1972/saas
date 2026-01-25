# IdeaGen Pro - AI-Powered Business Idea Generator

A sophisticated SaaS application that generates creative AI-powered business ideas using OpenAI's GPT models. Built with Next.js, Clerk authentication, and real-time streaming responses.

## 🚀 Features

- **AI-Powered Ideas**: Generate unique business ideas using OpenAI GPT models
- **Real-Time Streaming**: Watch ideas generate in real-time with streaming responses
- **User Authentication**: Secure authentication and subscription management with Clerk
- **Save & Download**: Automatically save generated ideas as markdown files
- **Subscription Management**: Built-in payment processing and subscription tiers
- **Responsive Design**: Beautiful, mobile-friendly interface with dark mode support
- **Professional Output**: Properly formatted markdown with headings and bullet points

## 🛠️ Tech Stack

- **Frontend**: Next.js 15, React, TypeScript, Tailwind CSS
- **Authentication**: Clerk (with subscription management)
- **AI**: OpenAI GPT API with streaming responses
- **Deployment**: Vercel
- **Styling**: Tailwind CSS with custom markdown rendering

## 📋 Prerequisites

- Node.js 18+ and npm
- OpenAI API key
- Clerk account with authentication setup
- Vercel account for deployment

## ⚙️ Environment Variables

Create a `.env.local` file in the root directory:

```bash
# Clerk Configuration
NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=pk_test_your_key_here
CLERK_SECRET_KEY=sk_test_your_key_here
CLERK_JWKS_URL=https://your-app.clerk.accounts.dev/.well-known/jwks.json
CLERK_WEBHOOK_SECRET=whsec_your_webhook_secret_here

# OpenAI Configuration
OPENAI_API_KEY=sk-your_openai_key_here
```

## 🚀 Getting Started

1. **Clone and install dependencies:**
```bash
git clone <repository-url>
cd saas
npm install
```

2. **Set up environment variables** (see above)

3. **Run development server:**
```bash
npm run dev
```

4. **Open [http://localhost:3000](http://localhost:3000)**

## 📦 Deployment

### Deploy to Vercel

1. **Deploy the application:**
```bash
vercel --prod
```

2. **Add environment variables** in Vercel dashboard:
   - Go to your project settings
   - Navigate to Environment Variables
   - Add all the variables from `.env.local`

3. **Note your deployment URL** (e.g., `https://your-app.vercel.app`)

## 🔗 CRITICAL: Webhook Setup

**⚠️ IMPORTANT: After each deployment, update your Clerk webhook URL!**

### In Clerk Dashboard:
1. Go to **Webhooks** section
2. Update the endpoint URL to your **NEW Vercel deployment URL**:
   ```
   https://your-new-deployment-url.vercel.app/api/webhooks/clerk
   ```
3. Ensure these events are selected:
   - `subscription.created`
   - `subscription.updated` 
   - `subscription.deleted`
4. Copy the webhook secret and update `CLERK_WEBHOOK_SECRET` in Vercel

### Why This Matters:
- Vercel creates a new URL for each deployment
- The webhook URL must match your current deployment
- Without this, subscription management won't work properly

## 🏗️ Project Structure

```
├── pages/
│   ├── index.tsx          # Landing page
│   ├── product.tsx        # Main app (idea generator)
│   ├── _app.tsx          # App wrapper with Clerk provider
│   ├── _document.tsx     # Document head configuration
│   └── api/
│       ├── index.ts      # OpenAI streaming API endpoint
│       └── webhooks/
│           └── clerk.ts  # Clerk webhook handler
├── styles/
│   └── globals.css       # Global styles and markdown rendering
├── .env.local            # Environment variables (not in git)
├── .env.example          # Environment template
└── SUBSCRIPTION_SETUP.md # Detailed subscription setup guide
```

## 💡 How It Works

1. **User Authentication**: Users sign in through Clerk
2. **Subscription Check**: App checks if user has premium access
3. **AI Generation**: OpenAI generates business ideas with streaming
4. **Real-Time Display**: Ideas appear in real-time with proper formatting
5. **Save Feature**: Users can download ideas as markdown files
6. **New Ideas**: Generate unlimited new ideas with one click

## 🔐 Security Features

- **JWT Authentication**: All API calls require valid Clerk JWT tokens
- **Subscription Verification**: Premium features protected by subscription status
- **Webhook Verification**: Clerk webhooks verified with secret signatures
- **Environment Security**: All sensitive keys stored as environment variables

## 🎯 Current Status

- ✅ **Fully Functional**: App works end-to-end
- ✅ **Real AI Integration**: Uses actual OpenAI API
- ✅ **Save Feature**: Download generated ideas
- ✅ **Authentication**: Secure user management
- ✅ **Deployed**: Live on Vercel
- 🔄 **Subscription Enforcement**: Currently allows all authenticated users (easily configurable)

## 📝 Usage

1. **Visit the deployed app**
2. **Sign in** with Clerk authentication
3. **Click "Access Premium Features"**
4. **Watch your AI business idea generate** in real-time
5. **Save the idea** using the download button
6. **Generate new ideas** as needed

## 🔧 Customization

- **AI Prompts**: Modify the prompt in `pages/api/index.ts`
- **Styling**: Update Tailwind classes throughout components
- **Subscription Logic**: Adjust checks in `pages/product.tsx`
- **AI Model**: Change OpenAI model in API configuration

## 📚 Additional Documentation

- `SUBSCRIPTION_SETUP.md` - Complete subscription system setup
- `.env.example` - Environment variable template
- Clerk documentation for advanced authentication features
- OpenAI documentation for API customization

## 🆘 Troubleshooting

### Common Issues:

1. **Webhook Not Working**: Update Clerk webhook URL after each deployment
2. **API Errors**: Check OpenAI API key and quotas
3. **Auth Issues**: Verify Clerk environment variables
4. **Deployment Fails**: Check build errors and environment variables

### Support:
- Check browser console for error details
- Verify all environment variables are set
- Ensure Clerk webhook URL matches current deployment
- Review OpenAI API usage and limits

---

**Built with ❤️ using Next.js, Clerk, and OpenAI**

****Future Enhancements (Optional):****
If you want to add more advanced features later, we could:

User History: Store ideas in a database with user accounts
Export Options: PDF, DOCX, or plain text formats
Idea Management: View, edit, and organize saved ideas
Sharing Features: Share ideas via email or social media

to connect Docker to ECR use the following command:
$TOKEN = aws ecr get-login-password --region eu-west-3
>> docker login --username AWS --password $TOKEN 809278131757.dkr.ecr.eu-west-3.amazonaws.com