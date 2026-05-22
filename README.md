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
