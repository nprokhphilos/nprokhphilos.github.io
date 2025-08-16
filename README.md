# nprokhphilos.github.io

import React from "react";
import { Link, useLocation } from "react-router-dom";
import { BookOpen, User, FileText, MessageCircle, Home, Atom } from "lucide-react";

const navigationItems = [
  { title: "Home", url: "/", icon: Home },
  { title: "About", url: "/about", icon: User },
  { title: "Research", url: "/research", icon: BookOpen },
  { title: "Essays", url: "/essays", icon: FileText },
  { title: "Contact", url: "/contact", icon: MessageCircle },
];

export default function Layout({ children, currentPageName }) {
  const location = useLocation();

  return (
    <div className="min-h-screen bg-gradient-to-br from-amber-50 via-orange-100 to-yellow-200/80 relative overflow-x-hidden">
      {/* Enhanced desert mirage background effects */}
      <div className="fixed inset-0 pointer-events-none opacity-80">
        <div className="absolute top-0 -left-1/4 w-1/2 h-1/2 bg-gradient-radial from-orange-300/30 via-amber-200/20 to-transparent rounded-full blur-3xl animate-[pulse_10s_cubic-bezier(0.4,0,0.6,1)_infinite]"></div>
        <div className="absolute top-1/3 -right-1/4 w-1/2 h-1/2 bg-gradient-radial from-yellow-300/20 via-orange-200/10 to-transparent rounded-full blur-3xl animate-[pulse_12s_cubic-bezier(0.4,0,0.6,1)_infinite_1s]"></div>
        <div className="absolute bottom-0 left-1/3 w-1/2 h-1/2 bg-gradient-radial from-amber-300/20 via-orange-200/10 to-transparent rounded-full blur-3xl animate-[pulse_15s_cubic-bezier(0.4,0,0.6,1)_infinite_2s]"></div>
      </div>
      
      {/* Shimmer overlay for mirage effect */}
      <div 
        className="fixed inset-0 pointer-events-none" 
        style={{
          background: 'linear-gradient(45deg, rgba(255,255,255,0) 45%, rgba(255,255,255,0.05) 50%, rgba(255,255,255,0) 55%)',
          backgroundSize: '400% 400%',
          animation: 'shimmer 15s ease infinite',
        }}
      ></div>

      {/* Navigation */}
      <nav className="relative z-50 bg-gradient-to-r from-amber-900/90 via-orange-900/90 to-yellow-900/90 backdrop-blur-lg border-b border-orange-800/40 shadow-xl">
        <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
          <div className="flex items-center justify-between h-20">
            {/* Logo/Brand */}
            <Link 
              to="/" 
              className="flex items-center gap-3 text-amber-100 font-bold text-2xl tracking-wider hover:text-orange-200 transition-colors duration-300 group"
            >
              <Atom className="w-8 h-8 text-orange-400 group-hover:rotate-90 transition-transform duration-500" />
              Nikita Prokhorov
            </Link>

            {/* Desktop Navigation */}
            <div className="hidden md:flex items-center space-x-1">
              {navigationItems.map((item) => (
                <Link
                  key={item.title}
                  to={item.url}
                  className={`relative flex items-center gap-2 px-4 py-2 rounded-lg transition-all duration-300 group ${
                    location.pathname === item.url
                      ? "text-amber-100"
                      : "text-orange-200 hover:text-amber-100"
                  }`}
                >
                  <span className={`absolute inset-0 rounded-lg transition-all duration-300 ${location.pathname === item.url ? 'bg-gradient-to-r from-orange-700/80 to-amber-700/80 shadow-lg' : 'group-hover:bg-orange-800/30'}`}></span>
                  <item.icon className="w-4 h-4 z-10" />
                  <span className="font-medium z-10">{item.title}</span>
                </Link>
              ))}
            </div>

            {/* Mobile Navigation Button */}
            <div className="md:hidden">
              <button className="text-orange-200 hover:text-amber-100 p-2">
                <svg className="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path strokeLinecap="round" strokeLinejoin="round" strokeWidth={2} d="M4 6h16M4 12h16M4 18h16" />
                </svg>
              </button>
            </div>
          </div>

          {/* Mobile Navigation Menu */}
          <div className="md:hidden pb-4">
            <div className="flex flex-col space-y-2">
              {navigationItems.map((item) => (
                <Link
                  key={item.title}
                  to={item.url}
                  className={`flex items-center gap-3 px-4 py-3 rounded-lg transition-all duration-300 ${
                    location.pathname === item.url
                      ? "bg-gradient-to-r from-orange-700/80 to-amber-700/80 text-amber-100"
                      : "text-orange-200 hover:text-amber-100 hover:bg-orange-800/30"
                  }`}
                >
                  <item.icon className="w-5 h-5" />
                  <span className="font-medium">{item.title}</span>
                </Link>
              ))}
            </div>
          </div>
        </div>
      </nav>

      {/* Main Content */}
      <main className="relative z-10">
        {children}
      </main>

      {/* Footer */}
      <footer className="relative z-10 bg-gradient-to-r from-amber-900/95 via-orange-900/95 to-yellow-900/95 backdrop-blur-sm border-t border-orange-800/30 mt-12">
        <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-8">
          <div className="text-center">
            <p className="text-orange-200 mb-4 italic">
              "The mystery of life isn't a problem to solve, but a reality to experience."
            </p>
            <p className="text-amber-300/80 text-sm">
              © {new Date().getFullYear()} Nikita Prokhorov. Website built on Arrakis.
            </p>
          </div>
        </div>
      </footer>

      <style>{`
        @keyframes shimmer {
          0% { background-position: 100% 100%; }
          100% { background-position: 0% 0%; }
        }
        .bg-gradient-radial {
          background: radial-gradient(circle, var(--tw-gradient-from), var(--tw-gradient-to));
        }
      `}</style>
    </div>
  );
}
