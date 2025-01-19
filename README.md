import React from 'react';
import { LineChart, Line, XAxis, YAxis, Tooltip, ResponsiveContainer } from 'recharts';
import { Github, Linkedin, Mail, Instagram, Code, Server, Cloud } from 'lucide-react';

const mockContributionData = [
  { month: 'Jan', contributions: 65 },
  { month: 'Feb', contributions: 85 },
  { month: 'Mar', contributions: 120 },
  { month: 'Apr', contributions: 90 },
  { month: 'May', contributions: 150 },
  { month: 'Jun', contributions: 180 }
];

export default function GitHubProfile() {
  const skills = {
    frontend: ['React', 'Next.js', 'TypeScript', 'Redux', 'Tailwind'],
    backend: ['Node.js', 'Express', 'NestJS', 'Laravel', 'GraphQL'],
    devops: ['AWS', 'Docker', 'Kubernetes', 'CI/CD']
  };

  return (
    <div className="max-w-4xl mx-auto p-8 space-y-12 bg-gray-50">
      {/* Header Section */}
      <div className="text-center space-y-4 animate-fade-in">
        <h1 className="text-4xl font-bold bg-gradient-to-r from-blue-600 to-purple-600 bg-clip-text text-transparent">
          Vikram Kumar
        </h1>
        <p className="text-xl text-gray-600">Full Stack Developer</p>
        <div className="flex justify-center space-x-4">
          <Github className="w-6 h-6 text-gray-700 hover:text-blue-600 transition-colors" />
          <Linkedin className="w-6 h-6 text-gray-700 hover:text-blue-600 transition-colors" />
          <Mail className="w-6 h-6 text-gray-700 hover:text-blue-600 transition-colors" />
          <Instagram className="w-6 h-6 text-gray-700 hover:text-blue-600 transition-colors" />
        </div>
      </div>

      {/* Skills Section */}
      <div className="space-y-6">
        <h2 className="text-2xl font-semibold text-gray-800 flex items-center">
          <Code className="w-6 h-6 mr-2" /> Technical Skills
        </h2>
        <div className="grid grid-cols-1 md:grid-cols-3 gap-6">
          {Object.entries(skills).map(([category, items]) => (
            <div key={category} className="p-4 bg-white rounded-lg shadow-sm hover:shadow-md transition-shadow">
              <h3 className="text-lg font-medium text-gray-700 mb-3 capitalize">{category}</h3>
              <div className="flex flex-wrap gap-2">
                {items.map(skill => (
                  <span key={skill} className="px-3 py-1 bg-gray-100 text-gray-600 rounded-full text-sm">
                    {skill}
                  </span>
                ))}
              </div>
            </div>
          ))}
        </div>
      </div>

      {/* Contribution Graph */}
      <div className="space-y-6">
        <h2 className="text-2xl font-semibold text-gray-800 flex items-center">
          <Server className="w-6 h-6 mr-2" /> Contributions
        </h2>
        <div className="h-64 bg-white p-4 rounded-lg shadow-sm">
          <ResponsiveContainer width="100%" height="100%">
            <LineChart data={mockContributionData}>
              <XAxis dataKey="month" />
              <YAxis />
              <Tooltip />
              <Line 
                type="monotone" 
                dataKey="contributions" 
                stroke="#4F46E5" 
                strokeWidth={2}
                dot={{ fill: '#4F46E5' }}
              />
            </LineChart>
          </ResponsiveContainer>
        </div>
      </div>

      {/* Projects Section */}
      <div className="space-y-6">
        <h2 className="text-2xl font-semibold text-gray-800 flex items-center">
          <Cloud className="w-6 h-6 mr-2" /> Featured Projects
        </h2>
        <div className="grid grid-cols-1 md:grid-cols-2 gap-6">
          {[1, 2].map((project) => (
            <div key={project} className="group relative overflow-hidden rounded-lg bg-white shadow-sm hover:shadow-md transition-shadow">
              <div className="aspect-video bg-gray-100">
                <img 
                  src={`/api/placeholder/400/225`}
                  alt={`Project ${project}`}
                  className="w-full h-full object-cover"
                />
              </div>
              <div className="p-4">
                <h3 className="text-lg font-medium text-gray-800">Project Title {project}</h3>
                <p className="text-gray-600 text-sm mt-2">
                  A brief description of the project and the technologies used in its development.
                </p>
              </div>
            </div>
          ))}
        </div>
      </div>
    </div>
  );
}
