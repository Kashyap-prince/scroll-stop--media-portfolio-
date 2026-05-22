import React, { useState } from 'react';
import { ChevronDown, ExternalLink, Mail, ArrowRight, Check, X } from 'lucide-react';

export default function Portfolio() {
  const [scrollY, setScrollY] = useState(0);
  const [activeCategory, setActiveCategory] = useState('all');
  const [hoveredProject, setHoveredProject] = useState(null);
  const [expandedFAQ, setExpandedFAQ] = useState(null);
  const [formData, setFormData] = useState({ name: '', email: '', service: '', message: '' });
  const [formStatus, setFormStatus] = useState('');

  React.useEffect(() => {
    const handleScroll = () => setScrollY(window.scrollY);
    window.addEventListener('scroll', handleScroll);
    return () => window.removeEventListener('scroll', handleScroll);
  }, []);

  const handleFormChange = (e) => {
    setFormData({ ...formData, [e.target.name]: e.target.value });
  };

  const handleFormSubmit = (e) => {
    e.preventDefault();
    setFormStatus('sending');
    // Create mailto link as fallback
    const mailtoLink = `mailto:fair9727@gmail.com?subject=Project Inquiry from ${formData.name}&body=${encodeURIComponent(`Name: ${formData.name}\nEmail: ${formData.email}\nService: ${formData.service}\n\nMessage:\n${formData.message}`)}`;
    window.location.href = mailtoLink;
    setTimeout(() => setFormStatus('sent'), 500);
  };

  const services = [
    {
      icon: '✨',
      title: 'Prompt Engineering',
      description: 'AI prompts optimized for Claude, ChatGPT, and other models. Get precise, repeatable outputs.',
      price: '₹300',
      color: 'from-blue-500 to-cyan-500'
    },
    {
      icon: '🎬',
      title: 'AI Scripts',
      description: 'Engaging video scripts for YouTube, Instagram Reels, and streaming. Funny, emotional, or educational.',
      price: '₹400-500',
      color: 'from-purple-500 to-pink-500'
    },
    {
      icon: '🎨',
      title: 'Thumbnails',
      description: 'Custom thumbnail designs that stop the scroll. CTR-optimized for maximum clicks.',
      price: '₹150+',
      color: 'from-orange-500 to-red-500'
    },
    {
      icon: '📝',
      title: 'Captions & Copy',
      description: 'Social media captions, ad copy, and hooks that convert. Instagram, YouTube Shorts, and more.',
      price: '₹200+',
      color: 'from-green-500 to-emerald-500'
    },
    {
      icon: '📚',
      title: 'Blog Posts',
      description: 'SEO-optimized, engaging blog content. 1000-3000 words, fully researched.',
      price: '₹250+',
      color: 'from-indigo-500 to-blue-500'
    }
  ];

  const portfolio = [
    { 
      id: 1, 
      title: 'STOP Wasting Time - Study Tips', 
      category: 'ai-scripts', 
      description: '5 proven study techniques that toppers use to crush exams. Educational content with anime-style visuals and engaging narratives.',
      image: '📚',
      highlight: true,
      excerpt: 'Includes The 50-10 Rule, Eliminating Distractions, Power Notes technique, and more. Perfect for education content creators.',
      cta: 'View Case Study'
    },
    { 
      id: 2, 
      title: 'Being Legal = Illegal (GTA Challenge)', 
      category: 'ai-scripts', 
      description: 'Comedy script where following every traffic rule in GTA V gets you arrested. Hilarious narration with perfect comedic timing.',
      image: '🎮',
      highlight: true,
      excerpt: 'Features setup, rules breakdown, first drive chaos, police chases at legal speed, GPS betrayal, and arrest scene. Pure comedy gold.',
      cta: 'View Case Study'
    },
    { 
      id: 3, 
      title: 'Educational Content Series', 
      category: 'ai-scripts', 
      description: 'Full scripts for YouTube videos with strong story structure, hooks, and viewer retention techniques.',
      image: '🎥'
    },
    { 
      id: 4, 
      title: 'Viral Caption Hooks', 
      category: 'captions', 
      description: 'Short-form captions optimized for Instagram Reels and YouTube Shorts. Designed for maximum engagement and shares.',
      image: '💬'
    },
    { 
      id: 5, 
      title: 'Tech & AI Blog Posts', 
      category: 'blog', 
      description: 'SEO-optimized articles on AI, tech, and productivity. Beginner-friendly yet comprehensive.',
      image: '📖'
    },
    { 
      id: 6, 
      title: 'AI Prompt Templates', 
      category: 'prompt-engineering', 
      description: 'Reusable prompt frameworks for marketing, copywriting, and content creation.',
      image: '✨'
    },
  ];

  const pricingPlans = [
    {
      name: 'Single Script',
      price: '₹450',
      description: 'One custom video script',
      features: ['Engaging narrative', 'Optimized for platform', 'Revisions included', 'Delivery in 3-5 days']
    },
    {
      name: '2 Scripts Bundle',
      price: '₹720',
      description: '2 scripts (20% off)',
      features: ['2 custom scripts', 'Any genre/style', 'Priority support', 'Faster delivery', 'SAVE ₹180'],
      featured: true
    },
    {
      name: 'Script + Captions',
      price: '₹650',
      description: '1 script + social captions',
      features: ['Full video script', '5+ caption variations', 'Hashtag strategy', 'Thumbnail brief']
    }
  ];

  const faqs = [
    {
      question: 'How long does it take to receive my script?',
      answer: 'Standard turnaround is 3-5 days for a full script. Rush delivery (1-2 days) available at +₹50. I work efficiently to meet your deadlines.'
    },
    {
      question: 'What platforms do you write for?',
      answer: 'I write for YouTube, Instagram Reels, YouTube Shorts, Twitch, podcasts, and more. Each script is optimized for your platform\'s unique style and audience.'
    },
    {
      question: 'Do you include revisions?',
      answer: 'Yes! Up to 2 rounds of revisions are included in every script. Additional revisions are ₹50 each. I want you to be completely satisfied.'
    },
    {
      question: 'What about copyright and ownership?',
      answer: 'You own 100% of the script once delivered and paid. You can use it commercially, modify it, or share it however you like. No restrictions.'
    },
    {
      question: 'Can you write scripts for any niche?',
      answer: 'I specialize in educational, comedy, and entertainment content. I\'ve written for tech, gaming, productivity, and lifestyle niches. If you have a specific niche, let me discuss it with you.'
    },
    {
      question: 'What if I\'m not happy with the script?',
      answer: 'I offer 1 free revision round. If you\'re still not satisfied, we discuss what\'s missing and adjust. My goal is your complete satisfaction.'
    },
    {
      question: 'Do you offer bulk discounts?',
      answer: 'Yes! 2+ scripts get 20% off. For larger projects (5+ scripts), I offer custom packages. Contact me to discuss your needs.'
    },
    {
      question: 'How do I provide you with my requirements?',
      answer: 'After inquiry, I\'ll send you a brief form asking about your audience, script length, tone, key points, and any specific requirements. The more detail, the better the script!'
    }
  ];

  const filteredPortfolio = activeCategory === 'all' 
    ? portfolio 
    : portfolio.filter(item => item.category === activeCategory);

  return (
    <div className="min-h-screen bg-gradient-to-br from-slate-950 via-slate-900 to-slate-950 text-white overflow-hidden">
      {/* Animated background */}
      <div className="fixed inset-0 overflow-hidden pointer-events-none">
        <div className="absolute top-20 left-10 w-96 h-96 bg-blue-500/10 rounded-full blur-3xl opacity-30 animate-pulse"></div>
        <div className="absolute bottom-40 right-20 w-96 h-96 bg-purple-500/10 rounded-full blur-3xl opacity-30 animate-pulse" style={{animationDelay: '1s'}}></div>
      </div>

      {/* Navigation */}
      <nav className="fixed top-0 w-full z-40 bg-slate-950/80 backdrop-blur-md border-b border-slate-800/50">
        <div className="max-w-6xl mx-auto px-6 py-4 flex justify-between items-center">
          <div className="text-2xl font-bold bg-gradient-to-r from-blue-400 to-purple-400 bg-clip-text text-transparent">
            ScrollStop Media
          </div>
          <div className="hidden md:flex gap-8 text-sm">
            <a href="#services" className="hover:text-blue-400 transition-colors">Services</a>
            <a href="#portfolio" className="hover:text-blue-400 transition-colors">Work</a>
            <a href="#pricing" className="hover:text-blue-400 transition-colors">Pricing</a>
            <a href="#faq" className="hover:text-blue-400 transition-colors">FAQ</a>
            <a href="#contact" className="hover:text-blue-400 transition-colors">Contact</a>
          </div>
        </div>
      </nav>

      {/* Hero Section */}
      <section className="relative pt-32 pb-20 px-6 min-h-screen flex items-center justify-center">
        <div className="max-w-4xl mx-auto text-center space-y-8">
          <div 
            style={{
              transform: `translateY(${scrollY * 0.5}px)`,
              opacity: 1 - scrollY / 800
            }}
          >
            <p className="text-blue-400 font-semibold mb-4">Hello, I'm Love Kashyap</p>
            <div className="text-6xl md:text-7xl font-bold leading-tight">
              <span className="block mb-4">Scripts That</span>
              <span className="bg-gradient-to-r from-blue-400 via-purple-400 to-pink-400 bg-clip-text text-transparent">
                Engage & Convert
              </span>
            </div>
          </div>
          
          <p className="text-xl text-slate-300 max-w-2xl mx-auto leading-relaxed">
            AI-powered video scripts, prompts, captions, thumbnails, and blog posts that captivate audiences and drive results. Perfect for creators, agencies, and entrepreneurs.
          </p>

          <div className="flex flex-col sm:flex-row gap-4 justify-center pt-8">
            <a href="#contact" className="group px-8 py-4 bg-gradient-to-r from-blue-500 to-purple-500 rounded-lg font-semibold hover:shadow-xl hover:shadow-blue-500/50 transition-all hover:scale-105 text-center">
              Get Started <ArrowRight className="inline ml-2 w-4 h-4 group-hover:translate-x-1 transition-transform" />
            </a>
            <a href="#portfolio" className="px-8 py-4 border border-slate-600 rounded-lg font-semibold hover:bg-slate-800/50 transition-all text-center">
              View My Work
            </a>
          </div>

          <div className="pt-8 animate-bounce">
            <ChevronDown className="w-6 h-6 mx-auto text-slate-400" />
          </div>
        </div>
      </section>

      {/* Services Section */}
      <section id="services" className="relative py-20 px-6">
        <div className="max-w-6xl mx-auto">
          <h2 className="text-4xl md:text-5xl font-bold mb-16 text-center">
            What I <span className="bg-gradient-to-r from-blue-400 to-purple-400 bg-clip-text text-transparent">Offer</span>
          </h2>

          <div className="grid md:grid-cols-2 lg:grid-cols-3 gap-6">
            {services.map((service, i) => (
              <div
                key={i}
                className="group relative p-8 bg-slate-800/40 border border-slate-700/50 rounded-xl hover:border-slate-600/80 transition-all hover:bg-slate-800/60 cursor-pointer"
                style={{
                  animation: `fadeInUp 0.6s ease-out ${i * 0.1}s both`
                }}
              >
                <div className={`text-5xl mb-4 group-hover:scale-110 transition-transform`}>
                  {service.icon}
                </div>
                <h3 className="text-xl font-bold mb-3">{service.title}</h3>
                <p className="text-slate-400 group-hover:text-slate-300 transition-colors mb-4">
                  {service.description}
                </p>
                <div className="inline-block px-3 py-1 bg-gradient-to-r from-blue-500/20 to-purple-500/20 border border-blue-500/30 rounded-full">
                  <span className="text-sm font-semibold bg-gradient-to-r from-blue-400 to-purple-400 bg-clip-text text-transparent">
                    {service.price}
                  </span>
                </div>
                <div className={`absolute top-0 right-0 w-20 h-20 bg-gradient-to-r ${service.color} opacity-0 group-hover:opacity-10 rounded-full blur-xl transition-opacity`}></div>
              </div>
            ))}
          </div>
        </div>
      </section>

      {/* Portfolio Section */}
      <section id="portfolio" className="relative py-20 px-6">
        <div className="max-w-6xl mx-auto">
          <h2 className="text-4xl md:text-5xl font-bold mb-8 text-center">
            Featured <span className="bg-gradient-to-r from-blue-400 to-purple-400 bg-clip-text text-transparent">Work</span>
          </h2>

          <div className="flex justify-center gap-3 mb-12 flex-wrap">
            {['all', 'ai-scripts', 'captions', 'blog', 'prompt-engineering'].map(cat => (
              <button
                key={cat}
                onClick={() => setActiveCategory(cat)}
                className={`px-6 py-2 rounded-full font-medium transition-all ${
                  activeCategory === cat
                    ? 'bg-gradient-to-r from-blue-500 to-purple-500 shadow-lg shadow-blue-500/50'
                    : 'bg-slate-800/50 hover:bg-slate-800 border border-slate-700'
                }`}
              >
                {cat === 'all' ? 'All Work' : cat.split('-').map(w => w.charAt(0).toUpperCase() + w.slice(1)).join(' ')}
              </button>
            ))}
          </div>

          <div className="grid md:grid-cols-2 lg:grid-cols-4 gap-4">
            {filteredPortfolio.map((project, i) => (
              <div
                key={project.id}
                onMouseEnter={() => setHoveredProject(project.id)}
                onMouseLeave={() => setHoveredProject(null)}
                className={`group relative overflow-hidden cursor-pointer hover:border-blue-500/50 transition-all rounded-lg ${project.highlight ? 'md:col-span-2 md:row-span-2 h-96' : 'h-64'} bg-slate-800/40 border border-slate-700/50`}
                style={{
                  animation: `fadeInUp 0.6s ease-out ${i * 0.05}s both`
                }}
              >
                <div className="absolute inset-0 flex items-center justify-center text-6xl group-hover:scale-110 transition-transform">
                  {project.image}
                </div>
                
                <div className={`absolute inset-0 bg-gradient-to-t from-slate-950 via-transparent to-transparent transition-all duration-300 ${hoveredProject === project.id ? 'opacity-100' : 'opacity-0'}`}>
                  <div className="absolute bottom-0 left-0 right-0 p-4 space-y-3">
                    <h3 className="font-bold text-lg">{project.title}</h3>
                    <p className="text-sm text-slate-300">{project.description}</p>
                    {project.excerpt && <p className="text-xs text-slate-400 italic">{project.excerpt}</p>}
                    {project.cta && <div className="text-xs font-semibold text-blue-400 group-hover:text-blue-300">{project.cta} →</div>}
                  </div>
                </div>
              </div>
            ))}
          </div>
        </div>
      </section>

      {/* Pricing Section */}
      <section id="pricing" className="relative py-20 px-6">
        <div className="max-w-6xl mx-auto">
          <h2 className="text-4xl md:text-5xl font-bold mb-16 text-center">
            Simple, <span className="bg-gradient-to-r from-blue-400 to-purple-400 bg-clip-text text-transparent">Transparent Pricing</span>
          </h2>

          <div className="grid md:grid-cols-3 gap-8 mb-12">
            {pricingPlans.map((plan, i) => (
              <div
                key={i}
                className={`relative p-8 rounded-xl transition-all ${
                  plan.featured
                    ? 'bg-gradient-to-br from-blue-600/20 to-purple-600/20 border border-blue-500/50 md:scale-105'
                    : 'bg-slate-800/40 border border-slate-700/50'
                }`}
                style={{
                  animation: `fadeInUp 0.6s ease-out ${i * 0.1}s both`
                }}
              >
                {plan.featured && (
                  <div className="absolute -top-4 left-1/2 transform -translate-x-1/2 bg-gradient-to-r from-blue-500 to-purple-500 px-4 py-1 rounded-full text-sm font-bold">
                    Most Popular
                  </div>
                )}
                <h3 className="text-2xl font-bold mb-2">{plan.name}</h3>
                <p className="text-slate-400 mb-4">{plan.description}</p>
                <div className="text-4xl font-bold mb-6">{plan.price}</div>
                <ul className="space-y-3 mb-8">
                  {plan.features.map((feature, j) => (
                    <li key={j} className="flex items-center gap-2 text-slate-300">
                      <Check className="w-5 h-5 text-green-400" />
                      {feature}
                    </li>
                  ))}
                </ul>
                <a href="#contact" className="w-full py-2 px-4 bg-gradient-to-r from-blue-500 to-purple-500 rounded-lg font-semibold hover:shadow-lg transition-all text-center">
                  Get Started
                </a>
              </div>
            ))}
          </div>

          <div className="bg-slate-800/40 border border-slate-700/50 rounded-xl p-8 text-center">
            <p className="text-slate-300 mb-2">Custom projects? Multiple scripts? Special packages?</p>
            <p className="text-lg font-semibold">Let's discuss! <a href="#contact" className="text-blue-400 hover:text-blue-300">Get in touch</a></p>
          </div>
        </div>
      </section>

      {/* FAQ Section */}
      <section id="faq" className="relative py-20 px-6">
        <div className="max-w-3xl mx-auto">
          <h2 className="text-4xl md:text-5xl font-bold mb-16 text-center">
            <span className="bg-gradient-to-r from-blue-400 to-purple-400 bg-clip-text text-transparent">Frequently Asked</span> Questions
          </h2>

          <div className="space-y-4">
            {faqs.map((faq, i) => (
              <div
                key={i}
                className="bg-slate-800/40 border border-slate-700/50 rounded-lg overflow-hidden hover:border-slate-600/80 transition-all"
                style={{
                  animation: `fadeInUp 0.6s ease-out ${i * 0.05}s both`
                }}
              >
                <button
                  onClick={() => setExpandedFAQ(expandedFAQ === i ? null : i)}
                  className="w-full p-6 flex justify-between items-center hover:bg-slate-800/60 transition-colors"
                >
                  <h3 className="text-lg font-semibold text-left">{faq.question}</h3>
                  <ChevronDown className={`w-5 h-5 transition-transform ${expandedFAQ === i ? 'rotate-180' : ''}`} />
                </button>
                {expandedFAQ === i && (
                  <div className="px-6 pb-6 border-t border-slate-700/50 text-slate-300">
                    {faq.answer}
                  </div>
                )}
              </div>
            ))}
          </div>
        </div>
      </section>

      {/* Contact Section */}
      <section id="contact" className="relative py-20 px-6">
        <div className="max-w-2xl mx-auto">
          <h2 className="text-4xl md:text-5xl font-bold mb-8 text-center">
            Ready to <span className="bg-gradient-to-r from-blue-400 to-purple-400 bg-clip-text text-transparent">Get Started?</span>
          </h2>
          <p className="text-lg text-slate-300 text-center mb-12">
            Let's create content that captivates your audience. Fill out the form below and I'll get back to you within 24 hours.
          </p>

          <form onSubmit={handleFormSubmit} className="bg-slate-800/40 border border-slate-700/50 rounded-xl p-8 space-y-6">
            <div># scroll-stop--media-portfolio-
