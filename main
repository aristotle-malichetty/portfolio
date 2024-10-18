import React, { useState, useEffect } from 'react';
import { 
  Database, 
  BarChart2, 
  Server, 
  Mail, 
  Phone, 
  Github,
  Linkedin,
  FileText,
  Code,
  GraduationCap,
  Briefcase,
  ChevronDown
} from 'lucide-react';

const Portfolio = () => {
  const [isVisible, setIsVisible] = useState({});
  const [activeSection, setActiveSection] = useState('hero');
  const [mousePosition, setMousePosition] = useState({ x: 0, y: 0 });
  const [isLoading, setIsLoading] = useState(true);

  // Demo data - replace with your information
  const data = {
    name: "John Data Smith",
    title: "Data Analytics Professional",
    contact: {
      email: "john@example.com",
      phone: "+1 (555) 123-4567",
      github: "github.com/johndatasmith",
      linkedin: "linkedin.com/in/johndatasmith",
      resume: "/path-to-resume.pdf"
    },
    technicalSkills: [
      { category: "Data Analysis", skills: ["Python", "R", "SQL", "Excel", "Power BI"] },
      { category: "Machine Learning", skills: ["Scikit-learn", "TensorFlow", "Statistical Analysis"] },
      { category: "Big Data", skills: ["Hadoop", "Spark", "AWS"] },
      { category: "Visualization", skills: ["Tableau", "Matplotlib", "Seaborn"] }
    ],
    projects: [
      {
        title: "Customer Churn Prediction",
        description: "Developed ML model with 92% accuracy to predict customer churn",
        tools: ["Python", "Scikit-learn", "Tableau"],
        github: "https://github.com/username/churn-prediction"
      },
      {
        title: "Sales Dashboard",
        description: "Created interactive dashboard tracking $10M in sales",
        tools: ["Power BI", "SQL", "Excel"],
        github: "https://github.com/username/sales-dashboard"
      }
    ],
    experience: [
      {
        role: "Data Analyst Intern",
        company: "Tech Corp",
        period: "2023 - Present",
        highlights: [
          "Automated reporting saving 10 hours/week",
          "Built predictive models for inventory"
        ]
      }
    ],
    education: [
      {
        degree: "MS in Business Analytics",
        school: "University Name",
        year: "2024",
        gpa: "3.9/4.0"
      }
    ]
  };

  // Loading animation
  useEffect(() => {
    setTimeout(() => setIsLoading(false), 2000);
  }, []);

  // Mouse movement effect
  useEffect(() => {
    const handleMouseMove = (e) => {
      setMousePosition({ x: e.clientX, y: e.clientY });
    };
    window.addEventListener('mousemove', handleMouseMove);
    return () => window.removeEventListener('mousemove', handleMouseMove);
  }, []);

  // Intersection Observer for sections
  useEffect(() => {
    const observer = new IntersectionObserver(
      (entries) => {
        entries.forEach((entry) => {
          if (entry.isIntersecting) {
            setActiveSection(entry.target.id);
          }
          setIsVisible(prev => ({
            ...prev,
            [entry.target.id]: entry.isIntersecting
          }));
        });
      },
      { threshold: 0.3 }
    );

    document.querySelectorAll('section').forEach((section) => {
      observer.observe(section);
    });

    return () => observer.disconnect();
  }, []);

  if (isLoading) {
    return (
      <div className="h-screen bg-gray-900 flex items-center justify-center">
        <div className="text-4xl text-blue-400 animate-pulse">
          Loading Experience...
        </div>
      </div>
    );
  }

  return (
    <div className="min-h-screen bg-gray-900 text-white overflow-hidden">
      {/* Animated background gradient following mouse */}
      <div 
        className="fixed inset-0 opacity-30 pointer-events-none"
        style={{
          background: `radial-gradient(circle at ${mousePosition.x}px ${mousePosition.y}px, rgba(59,130,246,0.2) 0%, rgba(0,0,0,0) 50%)`
        }}
      />

      {/* Navigation Dots */}
      <div className="fixed right-8 top-1/2 transform -translate-y-1/2 space-y-4 z-50">
        {['hero', 'skills', 'projects', 'experience', 'education'].map((section) => (
          <button
            key={section}
            onClick={() => document.getElementById(section).scrollIntoView({ behavior: 'smooth' })}
            className={`w-3 h-3 rounded-full transition-all duration-300 ${
              activeSection === section ? 'bg-blue-400 scale-150' : 'bg-gray-500 hover:bg-blue-300'
            }`}
          />
        ))}
      </div>

      {/* Hero Section */}
      <section id="hero" className="h-screen flex items-center justify-center relative">
        <div className="text-center z-10 animate-fade-in">
          <h1 className="text-7xl font-bold mb-4 animate-tracking-in-expand">{data.name}</h1>
          <h2 className="text-3xl text-blue-400 mb-8 animate-tracking-in-contract-bottom">{data.title}</h2>
          
          {/* Social Links */}
          <div className="flex justify-center space-x-8 mb-12">
            {[
              { icon: <Mail size={24} />, link: `mailto:${data.contact.email}`, label: "Email" },
              { icon: <Phone size={24} />, link: `tel:${data.contact.phone}`, label: "Phone" },
              { icon: <Github size={24} />, link: `https://${data.contact.github}`, label: "GitHub" },
              { icon: <Linkedin size={24} />, link: `https://${data.contact.linkedin}`, label: "LinkedIn" },
              { icon: <FileText size={24} />, link: data.contact.resume, label: "Resume" }
            ].map((item, index) => (
              <a
                key={index}
                href={item.link}
                className="group relative p-4 bg-gray-800 rounded-lg hover:bg-blue-600 transition-all duration-300 transform hover:scale-110"
                target="_blank"
                rel="noopener noreferrer"
              >
                {item.icon}
                <span className="absolute -bottom-8 left-1/2 transform -translate-x-1/2 opacity-0 group-hover:opacity-100 transition-opacity">
                  {item.label}
                </span>
              </a>
            ))}
          </div>

          {/* Scroll indicator */}
          <div className="absolute bottom-8 left-1/2 transform -translate-x-1/2 animate-bounce">
            <ChevronDown size={32} className="text-blue-400" />
          </div>
        </div>
      </section>

      {/* Technical Skills */}
      <section id="skills" className={`py-20 px-8 relative ${isVisible.skills ? 'animate-slide-up' : 'opacity-0'}`}>
        <h2 className="text-5xl font-bold mb-16 text-center">Technical Skills</h2>
        <div className="max-w-4xl mx-auto grid grid-cols-1 md:grid-cols-2 gap-8">
          {data.technicalSkills.map((category, index) => (
            <div 
              key={index} 
              className="bg-gray-800 p-6 rounded-lg transform transition-all duration-500 hover:scale-105 hover:rotate-1"
              style={{ 
                animationDelay: `${index * 200}ms`,
                transform: isVisible.skills ? 'translateY(0)' : 'translateY(100px)'
              }}
            >
              <h3 className="text-xl font-bold mb-4 text-blue-400">{category.category}</h3>
              <div className="flex flex-wrap gap-2">
                {category.skills.map((skill, skillIndex) => (
                  <span 
                    key={skillIndex} 
                    className="bg-blue-600 px-3 py-1 rounded-full text-sm transform hover:scale-110 transition-transform cursor-default"
                  >
                    {skill}
                  </span>
                ))}
              </div>
            </div>
          ))}
        </div>
      </section>

      {/* Projects */}
      <section id="projects" className={`py-20 px-8 bg-gray-800 relative ${isVisible.projects ? 'animate-slide-up' : 'opacity-0'}`}>
        <h2 className="text-5xl font-bold mb-16 text-center">Featured Projects</h2>
        <div className="max-w-4xl mx-auto grid grid-cols-1 md:grid-cols-2 gap-8">
          {data.projects.map((project, index) => (
            <div 
              key={index} 
              className="group bg-gray-900 p-6 rounded-lg transform transition-all duration-500 hover:scale-105"
            >
              <h3 className="text-xl font-bold mb-2 text-blue-400 group-hover:text-blue-300">{project.title}</h3>
              <p className="mb-4">{project.description}</p>
              <div className="flex flex-wrap gap-2 mb-4">
                {project.tools.map((tool, toolIndex) => (
                  <span key={toolIndex} className="bg-blue-600 px-2 py-1 rounded-full text-xs">
                    {tool}
                  </span>
                ))}
              </div>
              <a 
                href={project.github} 
                className="inline-flex items-center text-blue-400 hover:text-blue-300"
                target="_blank"
                rel="noopener noreferrer"
              >
                <Github className="mr-2" size={16} />
                View Code
              </a>
            </div>
          ))}
        </div>
      </section>

      {/* Experience */}
      <section id="experience" className={`py-20 px-8 relative ${isVisible.experience ? 'animate-slide-up' : 'opacity-0'}`}>
        <h2 className="text-5xl font-bold mb-16 text-center">Experience</h2>
        <div className="max-w-3xl mx-auto space-y-8">
          {data.experience.map((exp, index) => (
            <div 
              key={index} 
              className="bg-gray-800 p-6 rounded-lg transform transition-all duration-500 hover:scale-105 hover:-rotate-1"
            >
              <h3 className="text-xl font-bold text-blue-400">{exp.role}</h3>
              <h4 className="text-lg mb-2">{exp.company} | {exp.period}</h4>
              <ul className="list-disc list-inside space-y-2">
                {exp.highlights.map((highlight, highlightIndex) => (
                  <li 
                    key={highlightIndex} 
                    className="text-gray-300 hover:text-white transition-colors"
                  >
                    {highlight}
                  </li>
                ))}
              </ul>
            </div>
          ))}
        </div>
      </section>

      {/* Education */}
      <section id="education" className={`py-20 px-8 bg-gray-800 relative ${isVisible.education ? 'animate-slide-up' : 'opacity-0'}`}>
        <h2 className="text-5xl font-bold mb-16 text-center">Education</h2>
        <div className="max-w-3xl mx-auto">
          {data.education.map((edu, index) => (
            <div 
              key={index} 
              className="mb-8 bg-gray-900 p-6 rounded-lg transform transition-all duration-500 hover:scale-105 hover:rotate-1"
            >
              <h3 className="text-xl font-bold text-blue-400">{edu.degree}</h3>
              <h4 className="text-lg">{edu.school}</h4>
              <p className="text-gray-300">Graduation: {edu.year} | GPA: {edu.gpa}</p>
            </div>
          ))}
        </div>
      </section>
    </div>
  );
};

export default Portfolio;
