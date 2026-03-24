import React, { useState } from 'react';
import { Users, UserCheck, UserClock, UserMinus, DollarSign, Landmark, FileText, Menu, X } from 'lucide-react';

const HRDashboard = () => {
  const [isSidebarOpen, setSidebarOpen] = useState(true);

  const stats = [
    { label: 'Total Employees', value: '452', icon: <Users />, color: 'bg-blue-500' },
    { label: 'Active', value: '410', icon: <UserCheck />, color: 'bg-green-500' },
    { label: 'Probation', value: '32', icon: <UserClock />, color: 'bg-yellow-500' },
    { label: 'Resigned', value: '10', icon: <UserMinus />, color: 'bg-red-500' },
  ];

  const financeStats = [
    { label: 'Payroll (Monthly)', value: '$124,000', icon: <DollarSign />, color: 'bg-indigo-500' },
    { label: 'SSB Contribution', value: '$12,400', icon: <Landmark />, color: 'bg-purple-500' },
    { label: 'Income Tax', value: '$18,600', icon: <FileText />, color: 'bg-orange-500' },
  ];

  return (
    <div className="flex h-screen bg-gray-100 font-sans">
      {/* Sidebar /}
      <aside className={`${isSidebarOpen ? 'w-64' : 'w-20'} bg-slate-900 text-white transition-all duration-300 ease-in-out flex flex-col`}>
        <div className="p-6 text-xl font-bold border-b border-slate-800 flex justify-between items-center">
          {isSidebarOpen && <span>HR Portal</span>}
          <button onClick={() => setSidebarOpen(!isSidebarOpen)} className="hover:text-blue-400">
            {isSidebarOpen ? <X size={20} /> : <Menu size={20} />}
          </button>
        </div>
        <nav className="flex-1 mt-4">
          {['Dashboard', 'Employees', 'Payroll', 'Reports', 'Settings'].map((item) => (
            <a key={item} href="#" className="flex items-center px-6 py-4 hover:bg-slate-800 transition-colors">
              <div className="min-w-[30px]"><Menu size={18} /></div>
              {isSidebarOpen && <span className="ml-4">{item}</span>}
            </a>
          ))}
        </nav>
      </aside>

      {/ Main Content /}
      <main className="flex-1 overflow-y-auto p-8">
        <header className="mb-8">
          <h1 className="text-2xl font-bold text-gray-800">HR Overview</h1>
          <p className="text-gray-500">Welcome back, Admin.</p>
        </header>

        {/ Primary Stats Grid /}
        <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6 mb-8">
          {stats.map((stat, idx) => (
            <div key={idx} className="bg-white p-6 rounded-xl shadow-sm border border-gray-200 flex items-center">
              <div className={`${stat.color} p-4 rounded-lg text-white mr-4`}>
                {stat.icon}
              </div>
              <div>
                <p className="text-sm text-gray-500 font-medium">{stat.label}</p>
                <h3 className="text-2xl font-bold text-gray-800">{stat.value}</h3>
              </div>
            </div>
          ))}
        </div>

        {/ Finance & Compliance Section */}
        <h2 className="text-lg font-semibold text-gray-700 mb-4">Financial & Compliance</h2>
        <div className="grid grid-cols-1 md:grid-cols-3 gap-6">
          {financeStats.map((stat, idx) => (
            <div key={idx} className="bg-white p-6 rounded-xl shadow-sm border border-l-4 border-l-indigo-500 flex justify-between items-center">
              <div>
                <p className="text-sm text-gray-500">{stat.label}</p>
                <h3 className="text-xl font-bold text-gray-800">{stat.value}</h3>
              </div>
              <div className="text-indigo-200">
                {stat.icon}
              </div>
            </div>
          ))}
        </div>
      </main>
    </div>
  );
};

export default HRDashboard;
