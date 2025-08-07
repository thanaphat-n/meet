<!DOCTYPE html>
<html lang="th">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>แบบฟอร์มขอใช้ห้องประชุม กลุ่มบริษัท TAISIN</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" rel="stylesheet">
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Sarabun:wght@300;400;500;600;700&display=swap');
    body { font-family: 'Sarabun', sans-serif; }
    .calendar-day:hover { transform: translateY(-2px); }
    .booking-item { animation: slideIn 0.3s ease-out; }
    @keyframes slideIn {
      from { opacity: 0; transform: translateY(10px); }
      to { opacity: 1; transform: translateY(0); }
    }
    .modal-backdrop { backdrop-filter: blur(4px); }
    .room-card:hover { transform: translateY(-4px); box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1); }
    .time-slot { transition: all 0.2s ease; }
    .time-slot:hover { background-color: #dbeafe; }
    .time-slot.selected { background-color: #3b82f6; color: white; }
    .fade-in { animation: fadeIn 0.5s ease-in; }
    @keyframes fadeIn {
      from { opacity: 0; }
      to { opacity: 1; }
    }
    @keyframes shake {
      0%, 100% { transform: translateX(0); }
      10%, 30%, 50%, 70%, 90% { transform: translateX(-5px); }
      20%, 40%, 60%, 80% { transform: translateX(5px); }
    }
    @keyframes slideIn {
      from { opacity: 0; transform: translateY(20px); }
      to { opacity: 1; transform: translateY(0); }
    }
    .animate-slideIn {
      animation: slideIn 0.5s ease-out forwards;
    }
    @keyframes newBookingGlow {
      0% { box-shadow: 0 0 0 0 rgba(34, 197, 94, 0.7); }
      70% { box-shadow: 0 0 0 10px rgba(34, 197, 94, 0); }
      100% { box-shadow: 0 0 0 0 rgba(34, 197, 94, 0); }
    }
    .new-booking-glow {
      animation: newBookingGlow 2s ease-out;
    }
    @keyframes fadeIn {
      from { opacity: 0; }
      to { opacity: 1; }
    }
    @keyframes fadeOut {
      from { opacity: 1; }
      to { opacity: 0; }
    }
    .animate-fadeIn {
      animation: fadeIn 0.3s ease-in;
    }
    .animate-fadeOut {
      animation: fadeOut 0.3s ease-out;
    }
    @keyframes alertPulse {
      0%, 100% { transform: scale(1); }
      50% { transform: scale(1.05); }
    }
    .animate-alertPulse {
      animation: alertPulse 1s ease-in-out infinite;
    }
    @keyframes conflictShake {
      0%, 100% { transform: translateX(0); }
      10%, 30%, 50%, 70%, 90% { transform: translateX(-8px); }
      20%, 40%, 60%, 80% { transform: translateX(8px); }
    }
    .animate-conflictShake {
      animation: conflictShake 0.8s ease-in-out;
    }
    
    /* Success Modal Animations */
    @keyframes successBounce {
      0% { 
        opacity: 0; 
        transform: scale(0.3) translateY(-100px) rotate(-10deg); 
      }
      50% { 
        opacity: 1; 
        transform: scale(1.05) translateY(10px) rotate(2deg); 
      }
      70% { 
        transform: scale(0.95) translateY(-5px) rotate(-1deg); 
      }
      100% { 
        opacity: 1; 
        transform: scale(1) translateY(0) rotate(0deg); 
      }
    }
    .animate-successBounce {
      animation: successBounce 0.8s cubic-bezier(0.68, -0.55, 0.265, 1.55);
    }
    
    @keyframes successIcon {
      0% { 
        transform: scale(0) rotate(-180deg); 
        opacity: 0; 
      }
      50% { 
        transform: scale(1.2) rotate(10deg); 
        opacity: 1; 
      }
      100% { 
        transform: scale(1) rotate(0deg); 
        opacity: 1; 
      }
    }
    .animate-successIcon {
      animation: successIcon 0.6s ease-out 0.3s both;
    }
    
    @keyframes checkmark {
      0% { 
        transform: scale(0) rotate(45deg); 
        opacity: 0; 
      }
      50% { 
        transform: scale(1.3) rotate(45deg); 
        opacity: 1; 
      }
      100% { 
        transform: scale(1) rotate(0deg); 
        opacity: 1; 
      }
    }
    .animate-checkmark {
      animation: checkmark 0.5s ease-out 0.5s both;
    }
    
    @keyframes sparkle1 {
      0%, 100% { 
        transform: scale(0) rotate(0deg); 
        opacity: 0; 
      }
      50% { 
        transform: scale(1.5) rotate(180deg); 
        opacity: 1; 
      }
    }
    .animate-sparkle1 {
      animation: sparkle1 1.5s ease-in-out 0.8s infinite;
    }
    
    @keyframes sparkle2 {
      0%, 100% { 
        transform: scale(0) rotate(0deg); 
        opacity: 0; 
      }
      50% { 
        transform: scale(1.2) rotate(-180deg); 
        opacity: 1; 
      }
    }
    .animate-sparkle2 {
      animation: sparkle2 1.8s ease-in-out 1.2s infinite;
    }
    
    @keyframes sparkle3 {
      0%, 100% { 
        transform: scale(0) rotate(0deg); 
        opacity: 0; 
      }
      50% { 
        transform: scale(1) rotate(360deg); 
        opacity: 1; 
      }
    }
    .animate-sparkle3 {
      animation: sparkle3 2s ease-in-out 1s infinite;
    }
    
    @keyframes titleSlide {
      0% { 
        transform: translateY(-30px); 
        opacity: 0; 
      }
      100% { 
        transform: translateY(0); 
        opacity: 1; 
      }
    }
    .animate-titleSlide {
      animation: titleSlide 0.6s ease-out 0.4s both;
    }
    
    @keyframes progressBar {
      0% { width: 0; }
      100% { width: 200px; }
    }
    .animate-progressBar {
      animation: progressBar 1.5s ease-out 0.6s both;
    }
    
    @keyframes fadeInUp {
      0% { 
        transform: translateY(20px); 
        opacity: 0; 
      }
      100% { 
        transform: translateY(0); 
        opacity: 1; 
      }
    }
    .animate-fadeInUp {
      animation: fadeInUp 0.6s ease-out both;
    }
    
    @keyframes slideUp {
      0% { 
        transform: translateY(30px); 
        opacity: 0; 
      }
      100% { 
        transform: translateY(0); 
        opacity: 1; 
      }
    }
    .animate-slideUp {
      animation: slideUp 0.6s ease-out both;
    }
    
    @keyframes heartbeat {
      0%, 100% { transform: scale(1); }
      25% { transform: scale(1.1); }
      50% { transform: scale(1.2); }
      75% { transform: scale(1.1); }
    }
    .animate-heartbeat {
      animation: heartbeat 1.5s ease-in-out infinite;
      color: #e91e63;
    }
    
    @keyframes float {
      0%, 100% { 
        transform: translateY(0px) rotate(0deg); 
        opacity: 0.6; 
      }
      50% { 
        transform: translateY(-10px) rotate(5deg); 
        opacity: 1; 
      }
    }
    .animate-float {
      animation: float 3s ease-in-out infinite;
    }
    
    /* Sad face animations */
    @keyframes sadBounce {
      0%, 100% { 
        transform: translateY(0px) scale(1); 
      }
      50% { 
        transform: translateY(-5px) scale(1.02); 
      }
    }
    .animate-sadBounce {
      animation: sadBounce 2s ease-in-out infinite;
    }
    
    @keyframes tearDrop {
      0% { 
        transform: translateY(0px) scale(1); 
        opacity: 1; 
      }
      50% { 
        transform: translateY(10px) scale(0.8); 
        opacity: 0.7; 
      }
      100% { 
        transform: translateY(20px) scale(0.5); 
        opacity: 0; 
      }
    }
    .animate-tearDrop {
      animation: tearDrop 2s ease-in-out infinite;
    }
    
    @keyframes sadFloat {
      0%, 100% { 
        transform: translateY(0px) translateX(0px) rotate(0deg); 
        opacity: 0.4; 
      }
      25% { 
        transform: translateY(-8px) translateX(3px) rotate(2deg); 
        opacity: 0.8; 
      }
      50% { 
        transform: translateY(-5px) translateX(-2px) rotate(-1deg); 
        opacity: 1; 
      }
      75% { 
        transform: translateY(-12px) translateX(4px) rotate(3deg); 
        opacity: 0.6; 
      }
    }
    .animate-sadFloat {
      animation: sadFloat 4s ease-in-out infinite;
    }
    
    @keyframes gradientShift {
      0% { background-position: 0% 50%; }
      50% { background-position: 100% 50%; }
      100% { background-position: 0% 50%; }
    }
    .animate-gradientShift {
      background-size: 200% 200%;
      animation: gradientShift 4s ease infinite;
    }
    
    /* Confetti Styles */
    .confetti-piece {
      position: absolute;
      width: 10px;
      height: 10px;
      background: #f39c12;
      animation: confetti-fall 3s linear infinite;
    }
    
    @keyframes confetti-fall {
      0% {
        transform: translateY(-100vh) rotate(0deg);
        opacity: 1;
      }
      100% {
        transform: translateY(100vh) rotate(720deg);
        opacity: 0;
      }
    }
    
    /* Particle Styles */
    .particle {
      position: absolute;
      width: 4px;
      height: 4px;
      background: radial-gradient(circle, #fff, transparent);
      border-radius: 50%;
      animation: particle-float 4s ease-in-out infinite;
    }
    
    .particle-1 { top: 10%; left: 10%; animation-delay: 0s; }
    .particle-2 { top: 20%; right: 15%; animation-delay: 0.5s; }
    .particle-3 { bottom: 30%; left: 20%; animation-delay: 1s; }
    .particle-4 { bottom: 20%; right: 10%; animation-delay: 1.5s; }
    .particle-5 { top: 50%; left: 5%; animation-delay: 2s; }
    .particle-6 { top: 60%; right: 5%; animation-delay: 2.5s; }
    
    @keyframes particle-float {
      0%, 100% { 
        transform: translateY(0px) translateX(0px); 
        opacity: 0.3; 
      }
      25% { 
        transform: translateY(-20px) translateX(10px); 
        opacity: 0.8; 
      }
      50% { 
        transform: translateY(-10px) translateX(-5px); 
        opacity: 1; 
      }
      75% { 
        transform: translateY(-30px) translateX(15px); 
        opacity: 0.6; 
      }
    }
    
    /* Celebration Rays */
    .ray {
      position: absolute;
      top: 50%;
      left: 50%;
      width: 4px;
      height: 200px;
      background: linear-gradient(to bottom, transparent, #ffd700, transparent);
      transform-origin: center bottom;
      animation: rayRotate 4s linear infinite;
      opacity: 0.6;
    }
    
    .ray-1 { transform: rotate(0deg) translateY(-100px); animation-delay: 0s; }
    .ray-2 { transform: rotate(45deg) translateY(-100px); animation-delay: 0.5s; }
    .ray-3 { transform: rotate(90deg) translateY(-100px); animation-delay: 1s; }
    .ray-4 { transform: rotate(135deg) translateY(-100px); animation-delay: 1.5s; }
    .ray-5 { transform: rotate(180deg) translateY(-100px); animation-delay: 2s; }
    .ray-6 { transform: rotate(225deg) translateY(-100px); animation-delay: 2.5s; }
    .ray-7 { transform: rotate(270deg) translateY(-100px); animation-delay: 3s; }
    .ray-8 { transform: rotate(315deg) translateY(-100px); animation-delay: 3.5s; }
    
    @keyframes rayRotate {
      0% { 
        transform: rotate(var(--rotation, 0deg)) translateY(-100px) scale(0);
        opacity: 0;
      }
      10% { 
        transform: rotate(var(--rotation, 0deg)) translateY(-100px) scale(1);
        opacity: 0.8;
      }
      90% { 
        transform: rotate(var(--rotation, 0deg)) translateY(-100px) scale(1);
        opacity: 0.8;
      }
      100% { 
        transform: rotate(var(--rotation, 0deg)) translateY(-100px) scale(0);
        opacity: 0;
      }
    }
    
    /* Fireworks Styles */
    .firework {
      position: absolute;
      width: 6px;
      height: 6px;
      border-radius: 50%;
      animation: fireworkExplode 2s ease-out forwards;
    }
    
    @keyframes fireworkExplode {
      0% {
        transform: scale(0);
        opacity: 1;
      }
      50% {
        transform: scale(1);
        opacity: 1;
      }
      100% {
        transform: scale(2);
        opacity: 0;
      }
    }
    
    /* Enhanced Confetti */
    .confetti-piece {
      position: absolute;
      width: 12px;
      height: 12px;
      animation: confetti-fall 4s linear infinite;
    }
    
    @keyframes confetti-fall {
      0% {
        transform: translateY(-100vh) rotate(0deg) scale(1);
        opacity: 1;
      }
      50% {
        opacity: 1;
        transform: translateY(50vh) rotate(360deg) scale(1.2);
      }
      100% {
        transform: translateY(100vh) rotate(720deg) scale(0.8);
        opacity: 0;
      }
    }
  </style>
</head>
<body class="bg-gradient-to-br from-purple-100 via-pink-50 to-blue-100 min-h-screen">

<!-- Header -->
<header class="bg-gradient-to-r from-indigo-600 via-purple-600 to-pink-600 shadow-lg border-b border-purple-300">
  <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
    <div class="flex justify-between items-center py-4">
      <div class="flex items-center">
        <i class="fas fa-calendar-alt text-2xl text-white mr-3"></i>
        <div>
          <h1 class="text-xl sm:text-2xl font-bold text-white">ระบบการจองห้องประชุม TAISIN GROUP</h1>
        </div>
      </div>
      <div class="flex items-center space-x-4">
        <!-- Main Navigation Menu -->
        <nav class="hidden md:flex items-center space-x-4">
          <button onclick="showWelcomeSection()" class="text-white hover:text-yellow-300 transition-colors px-3 py-2 rounded-lg hover:bg-white hover:bg-opacity-10">
            <i class="fas fa-home mr-1"></i>หน้าหลัก
          </button>
          <button onclick="showBookingForm()" class="text-white hover:text-yellow-300 transition-colors px-3 py-2 rounded-lg hover:bg-white hover:bg-opacity-10">
            <i class="fas fa-plus mr-1"></i>จองห้อง
          </button>
          <button onclick="showTodayBookingsSection()" class="text-white hover:text-yellow-300 transition-colors px-3 py-2 rounded-lg hover:bg-white hover:bg-opacity-10">
            <i class="fas fa-calendar-day mr-1"></i>การจองวันนี้
          </button>
        </nav>

        <!-- Mobile Menu Button -->
        <button id="mobileMenuBtn" class="md:hidden text-white hover:text-yellow-300 transition-colors" onclick="toggleMobileMenu()">
          <i class="fas fa-bars text-xl"></i>
        </button>

        <!-- Admin Section -->
        <div class="border-l border-white border-opacity-30 pl-4">
          <button id="adminBtn" class="text-white hover:text-yellow-300 transition-colors" onclick="showAdminModal()">
            <i class="fas fa-user-shield mr-1"></i>ผู้ดูแลระบบ
          </button>
          <div id="adminStatus" class="hidden text-yellow-300 font-medium">
            <i class="fas fa-check-circle mr-1"></i>Admin
            <button onclick="showAdminMenu()" class="ml-2 bg-red-500 text-white px-3 py-1 rounded hover:bg-red-600 transition-colors">
              <i class="fas fa-cogs mr-1"></i>เมนูจัดการ
            </button>
            <button id="logoutBtn" class="ml-2 text-red-300 hover:text-red-200" onclick="adminLogout()">
              <i class="fas fa-sign-out-alt"></i>
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</header>

<!-- Mobile Menu -->
<div id="mobileMenu" class="hidden md:hidden bg-gradient-to-r from-indigo-600 via-purple-600 to-pink-600 border-t border-purple-300">
  <div class="max-w-7xl mx-auto px-4 py-4">
    <nav class="flex flex-col space-y-2">
      <button onclick="showWelcomeSection(); toggleMobileMenu();" class="text-white hover:text-yellow-300 transition-colors px-3 py-2 rounded-lg hover:bg-white hover:bg-opacity-10 text-left">
        <i class="fas fa-home mr-2"></i>หน้าหลัก
      </button>
      <button onclick="showBookingForm(); toggleMobileMenu();" class="text-white hover:text-yellow-300 transition-colors px-3 py-2 rounded-lg hover:bg-white hover:bg-opacity-10 text-left">
        <i class="fas fa-plus mr-2"></i>จองห้องประชุม
      </button>
      <button onclick="showTodayBookingsSection(); toggleMobileMenu();" class="text-white hover:text-yellow-300 transition-colors px-3 py-2 rounded-lg hover:bg-white hover:bg-opacity-10 text-left">
        <i class="fas fa-calendar-day mr-2"></i>การจองวันนี้
      </button>
      <div class="border-t border-white border-opacity-30 pt-2 mt-2">
        <button onclick="showAdminModal(); toggleMobileMenu();" class="text-white hover:text-yellow-300 transition-colors px-3 py-2 rounded-lg hover:bg-white hover:bg-opacity-10 text-left w-full">
          <i class="fas fa-user-shield mr-2"></i>ผู้ดูแลระบบ
        </button>
      </div>
    </nav>
  </div>
</div>

<!-- Main Content -->
<div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-8">
  <div class="grid grid-cols-1 lg:grid-cols-3 gap-8">
    <div class="lg:col-span-2">
      <div class="bg-gradient-to-br from-white to-blue-50 rounded-2xl shadow-xl border border-blue-200 p-6">
        <h2 class="text-xl font-bold bg-gradient-to-r from-purple-600 to-pink-600 bg-clip-text text-transparent mb-6">ระบบการจองห้องประชุม TAISIN GROUP</h2>
        
        <!-- Welcome Section -->
        <div id="welcomeSection" class="py-8">
          <!-- Header -->
          <div class="text-center mb-8">
            <i class="fas fa-calendar-check text-6xl bg-gradient-to-r from-purple-500 to-pink-500 bg-clip-text text-transparent mb-4"></i>
            <h3 class="text-2xl font-bold text-gray-800 mb-4">ยินดีต้อนรับสู่ระบบการจองห้องประชุม<br>TAISIN GROUP</h3>
            <p class="text-gray-600 mb-6">จองห้องประชุมได้อย่างง่ายดายและรวดเร็ว</p>
          </div>

          <!-- How to Book Section -->
          <div class="bg-gradient-to-r from-blue-50 to-indigo-50 rounded-2xl p-6 mb-8 border border-blue-200">
            <div class="text-center mb-6">
              <h4 class="text-xl font-bold text-blue-800 mb-2">
                <i class="fas fa-question-circle mr-2"></i>วิธีการจองห้องประชุม
              </h4>
              <p class="text-blue-700 text-sm">ทำตามขั้นตอนง่ายๆ เพียง 4 ขั้นตอน</p>
            </div>

            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-4">
              <!-- Step 1 -->
              <div class="bg-white rounded-xl p-4 border-2 border-blue-200 hover:border-blue-400 transition-all duration-300 hover:shadow-lg group">
                <div class="text-center">
                  <div class="w-12 h-12 bg-gradient-to-r from-blue-500 to-blue-600 text-white rounded-full flex items-center justify-center mx-auto mb-3 group-hover:scale-110 transition-transform duration-300">
                    <i class="fas fa-door-open text-lg"></i>
                  </div>
                  <div class="text-blue-600 font-bold text-sm mb-2">ขั้นตอนที่ 1</div>
                  <h5 class="font-bold text-gray-800 mb-2">เลือกห้องประชุม</h5>
                  <p class="text-xs text-gray-600 leading-relaxed">เลือกห้องประชุมที่ต้องการใช้งาน จากห้องที่มีให้เลือก 5 ห้อง</p>
                  <div class="mt-3 flex flex-wrap gap-1 justify-center">
                    <span class="bg-red-100 text-red-700 text-xs px-2 py-1 rounded-full">1A</span>
                    <span class="bg-orange-100 text-orange-700 text-xs px-2 py-1 rounded-full">1B</span>
                    <span class="bg-blue-100 text-blue-700 text-xs px-2 py-1 rounded-full">500</span>
                    <span class="bg-green-100 text-green-700 text-xs px-2 py-1 rounded-full">501</span>
                    <span class="bg-purple-100 text-purple-700 text-xs px-2 py-1 rounded-full">502</span>
                  </div>
                </div>
              </div>

              <!-- Step 2 -->
              <div class="bg-white rounded-xl p-4 border-2 border-green-200 hover:border-green-400 transition-all duration-300 hover:shadow-lg group">
                <div class="text-center">
                  <div class="w-12 h-12 bg-gradient-to-r from-green-500 to-green-600 text-white rounded-full flex items-center justify-center mx-auto mb-3 group-hover:scale-110 transition-transform duration-300">
                    <i class="fas fa-clock text-lg"></i>
                  </div>
                  <div class="text-green-600 font-bold text-sm mb-2">ขั้นตอนที่ 2</div>
                  <h5 class="font-bold text-gray-800 mb-2">เลือกวันที่และเวลา</h5>
                  <p class="text-xs text-gray-600 leading-relaxed">กำหนดวันที่และช่วงเวลาที่ต้องการใช้ห้องประชุม</p>
                  <div class="mt-3 space-y-1">
                    <div class="flex items-center justify-center text-xs text-gray-600">
                      <i class="fas fa-sun text-yellow-500 mr-1"></i>
                      <span>เช้า 09:00-12:00</span>
                    </div>
                    <div class="flex items-center justify-center text-xs text-gray-600">
                      <i class="fas fa-sun text-orange-500 mr-1"></i>
                      <span>บ่าย 13:00-16:00</span>
                    </div>
                    <div class="flex items-center justify-center text-xs text-gray-600">
                      <i class="fas fa-clock text-blue-500 mr-1"></i>
                      <span>เต็มวัน หรือกำหนดเอง</span>
                    </div>
                  </div>
                </div>
              </div>

              <!-- Step 3 -->
              <div class="bg-white rounded-xl p-4 border-2 border-purple-200 hover:border-purple-400 transition-all duration-300 hover:shadow-lg group">
                <div class="text-center">
                  <div class="w-12 h-12 bg-gradient-to-r from-purple-500 to-purple-600 text-white rounded-full flex items-center justify-center mx-auto mb-3 group-hover:scale-110 transition-transform duration-300">
                    <i class="fas fa-user text-lg"></i>
                  </div>
                  <div class="text-purple-600 font-bold text-sm mb-2">ขั้นตอนที่ 3</div>
                  <h5 class="font-bold text-gray-800 mb-2">กรอกข้อมูลผู้จอง</h5>
                  <p class="text-xs text-gray-600 leading-relaxed">กรอกข้อมูลส่วนตัว รายละเอียดการประชุม และอุปกรณ์ที่ต้องการ</p>
                  <div class="mt-3 space-y-1">
                    <div class="flex items-center justify-center text-xs text-gray-600">
                      <i class="fas fa-user text-blue-500 mr-1"></i>
                      <span>ชื่อ-นามสกุล</span>
                    </div>
                    <div class="flex items-center justify-center text-xs text-gray-600">
                      <i class="fas fa-building text-green-500 mr-1"></i>
                      <span>แผนก</span>
                    </div>
                    <div class="flex items-center justify-center text-xs text-gray-600">
                      <i class="fas fa-clipboard-list text-purple-500 mr-1"></i>
                      <span>หัวข้อการประชุม</span>
                    </div>
                  </div>
                </div>
              </div>

              <!-- Step 4 -->
              <div class="bg-white rounded-xl p-4 border-2 border-orange-200 hover:border-orange-400 transition-all duration-300 hover:shadow-lg group">
                <div class="text-center">
                  <div class="w-12 h-12 bg-gradient-to-r from-orange-500 to-orange-600 text-white rounded-full flex items-center justify-center mx-auto mb-3 group-hover:scale-110 transition-transform duration-300">
                    <i class="fas fa-check text-lg"></i>
                  </div>
                  <div class="text-orange-600 font-bold text-sm mb-2">ขั้นตอนที่ 4</div>
                  <h5 class="font-bold text-gray-800 mb-2">ตรวจสอบและยืนยัน</h5>
                  <p class="text-xs text-gray-600 leading-relaxed">ตรวจสอบข้อมูลการจองให้ถูกต้อง แล้วกดยืนยันการจอง</p>
                  <div class="mt-3">
                    <div class="bg-green-100 text-green-800 text-xs px-3 py-1 rounded-full inline-flex items-center">
                      <i class="fas fa-check-circle mr-1"></i>
                      <span>เสร็จสิ้น!</span>
                    </div>
                  </div>
                </div>
              </div>
            </div>

            <!-- Additional Info -->
            <div class="mt-6 bg-white rounded-xl p-4 border border-blue-200">
              <div class="grid grid-cols-1 md:grid-cols-3 gap-4 text-center">
                <div class="flex items-center justify-center">
                  <i class="fas fa-clock text-blue-600 mr-2"></i>
                  <span class="text-sm text-gray-700">ใช้เวลาเพียง <strong>2-3 นาที</strong></span>
                </div>
                <div class="flex items-center justify-center">
                  <i class="fas fa-shield-check text-green-600 mr-2"></i>
                  <span class="text-sm text-gray-700">ระบบตรวจสอบ<strong>ความซ้ำซ้อน</strong></span>
                </div>
                <div class="flex items-center justify-center">
                  <i class="fas fa-bell text-purple-600 mr-2"></i>
                  <span class="text-sm text-gray-700">แจ้งเตือน<strong>ทันที</strong>หากมีปัญหา</span>
                </div>
              </div>
            </div>
          </div>

          <!-- Action Buttons -->
          <div class="text-center">
            <div class="flex flex-col sm:flex-row gap-4 justify-center">
              <button id="startBookingBtn" onclick="startBookingProcess()" class="bg-gradient-to-r from-purple-600 to-pink-600 text-white px-8 py-4 rounded-xl hover:from-purple-700 hover:to-pink-700 transition-all duration-300 text-lg font-semibold shadow-lg transform hover:scale-105 focus:outline-none focus:ring-4 focus:ring-purple-300">
                <i class="fas fa-plus mr-2"></i>เริ่มจองห้องประชุม
                <div class="text-xs opacity-90 mt-1">ทำตามขั้นตอนข้างต้น</div>
              </button>
              <button onclick="showTodayBookingsSection()" class="bg-gradient-to-r from-blue-600 to-indigo-600 text-white px-8 py-4 rounded-xl hover:from-blue-700 hover:to-indigo-700 transition-all duration-300 text-lg font-semibold shadow-lg transform hover:scale-105 focus:outline-none focus:ring-4 focus:ring-blue-300">
                <i class="fas fa-calendar-day mr-2"></i>ดูการจองวันนี้
                <div class="text-xs opacity-90 mt-1">ตรวจสอบการจองที่มีอยู่</div>
              </button>
            </div>

            <!-- Quick Tips -->
            <div class="mt-6 bg-gradient-to-r from-yellow-50 to-orange-50 rounded-xl p-4 border border-yellow-200">
              <h5 class="font-bold text-yellow-800 mb-3">
                <i class="fas fa-lightbulb mr-2"></i>เคล็ดลับการใช้งาน
              </h5>
              <div class="grid grid-cols-1 md:grid-cols-2 gap-3 text-sm">
                <div class="flex items-start">
                  <i class="fas fa-check-circle text-green-600 mr-2 mt-0.5"></i>
                  <span class="text-gray-700">ตรวจสอบความว่างของห้องก่อนจอง</span>
                </div>
                <div class="flex items-start">
                  <i class="fas fa-check-circle text-green-600 mr-2 mt-0.5"></i>
                  <span class="text-gray-700">เตรียมข้อมูลการประชุมให้พร้อม</span>
                </div>
                <div class="flex items-start">
                  <i class="fas fa-check-circle text-green-600 mr-2 mt-0.5"></i>
                  <span class="text-gray-700">ระบุอุปกรณ์ที่ต้องการล่วงหน้า</span>
                </div>
                <div class="flex items-start">
                  <i class="fas fa-check-circle text-green-600 mr-2 mt-0.5"></i>
                  <span class="text-gray-700">ยืนยันข้อมูลก่อนกดส่ง</span>
                </div>
              </div>
            </div>
          </div>
        </div>

        <!-- Booking Form -->
        <div id="bookingForm" class="hidden fade-in">
          <!-- Progress Steps -->
          <div class="mb-8">
            <div class="flex items-center justify-between mb-4">
              <h3 class="text-xl font-bold bg-gradient-to-r from-blue-600 to-purple-600 bg-clip-text text-transparent">
                <i class="fas fa-clipboard-list mr-2"></i>ขั้นตอนการจองห้องประชุม
              </h3>
              <div class="text-sm text-gray-600">
                ขั้นตอนที่ <span id="currentStep">1</span> จาก 4
              </div>
            </div>
            
            <div class="flex items-center justify-between">
              <div class="flex items-center step-indicator active" data-step="1">
                <div class="w-10 h-10 rounded-full bg-blue-500 text-white flex items-center justify-center font-bold mr-3 transition-all duration-300">
                  <i class="fas fa-door-open"></i>
                </div>
                <div class="hidden sm:block">
                  <div class="font-semibold text-blue-600">เลือกห้อง</div>
                  <div class="text-xs text-gray-500">เลือกห้องประชุม</div>
                </div>
              </div>
              
              <div class="flex-1 h-1 bg-gray-200 mx-4 rounded-full">
                <div class="h-full bg-blue-500 rounded-full transition-all duration-500" style="width: 25%" id="progressBar"></div>
              </div>
              
              <div class="flex items-center step-indicator" data-step="2">
                <div class="w-10 h-10 rounded-full bg-gray-300 text-gray-600 flex items-center justify-center font-bold mr-3 transition-all duration-300">
                  <i class="fas fa-clock"></i>
                </div>
                <div class="hidden sm:block">
                  <div class="font-semibold text-gray-400">เลือกเวลา</div>
                  <div class="text-xs text-gray-400">กำหนดวันและเวลา</div>
                </div>
              </div>
              
              <div class="flex-1 h-1 bg-gray-200 mx-4 rounded-full">
                <div class="h-full bg-gray-300 rounded-full transition-all duration-500" style="width: 0%"></div>
              </div>
              
              <div class="flex items-center step-indicator" data-step="3">
                <div class="w-10 h-10 rounded-full bg-gray-300 text-gray-600 flex items-center justify-center font-bold mr-3 transition-all duration-300">
                  <i class="fas fa-user"></i>
                </div>
                <div class="hidden sm:block">
                  <div class="font-semibold text-gray-400">กรอกข้อมูล</div>
                  <div class="text-xs text-gray-400">ข้อมูลผู้จอง</div>
                </div>
              </div>
              
              <div class="flex-1 h-1 bg-gray-200 mx-4 rounded-full">
                <div class="h-full bg-gray-300 rounded-full transition-all duration-500" style="width: 0%"></div>
              </div>
              
              <div class="flex items-center step-indicator" data-step="4">
                <div class="w-10 h-10 rounded-full bg-gray-300 text-gray-600 flex items-center justify-center font-bold mr-3 transition-all duration-300">
                  <i class="fas fa-check"></i>
                </div>
                <div class="hidden sm:block">
                  <div class="font-semibold text-gray-400">ยืนยัน</div>
                  <div class="text-xs text-gray-400">ตรวจสอบและยืนยัน</div>
                </div>
              </div>
            </div>
          </div>

          <!-- Step 1: Room Selection -->
          <div id="step1" class="booking-step">
            <div class="bg-gradient-to-r from-blue-50 to-indigo-50 p-6 rounded-xl border border-blue-200 mb-6">
              <h4 class="text-lg font-semibold text-blue-800 mb-4">
                <i class="fas fa-door-open mr-2"></i>ขั้นตอนที่ 1: เลือกห้องประชุม
              </h4>
              <p class="text-blue-700 text-sm mb-4">กรุณาเลือกห้องประชุมที่ต้องการใช้งาน</p>
              <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4">
                <div class="room-card bg-gradient-to-r from-red-50 to-red-100 p-4 rounded-lg border-2 border-transparent hover:border-red-300 cursor-pointer transition-all duration-300" data-room="ห้อง 1A">
                  <div class="flex items-center justify-between">
                    <div>
                      <h4 class="font-semibold text-gray-800">ห้อง 1A</h4>
                    </div>
                    <i class="fas fa-door-open text-2xl text-red-600"></i>
                  </div>
                </div>
                <div class="room-card bg-gradient-to-r from-orange-50 to-orange-100 p-4 rounded-lg border-2 border-transparent hover:border-orange-300 cursor-pointer transition-all duration-300" data-room="ห้อง 1B">
                  <div class="flex items-center justify-between">
                    <div>
                      <h4 class="font-semibold text-gray-800">ห้อง 1B</h4>
                    </div>
                    <i class="fas fa-chalkboard-teacher text-2xl text-orange-600"></i>
                  </div>
                </div>
                <div class="room-card bg-gradient-to-r from-blue-50 to-blue-100 p-4 rounded-lg border-2 border-transparent hover:border-blue-300 cursor-pointer transition-all duration-300" data-room="ห้อง 500">
                  <div class="flex items-center justify-between">
                    <div>
                      <h4 class="font-semibold text-gray-800">ห้อง 500</h4>
                    </div>
                    <i class="fas fa-users text-2xl text-blue-600"></i>
                  </div>
                </div>
                <div class="room-card bg-gradient-to-r from-green-50 to-green-100 p-4 rounded-lg border-2 border-transparent hover:border-green-300 cursor-pointer transition-all duration-300" data-room="ห้อง 501">
                  <div class="flex items-center justify-between">
                    <div>
                      <h4 class="font-semibold text-gray-800">ห้อง 501</h4>
                    </div>
                    <i class="fas fa-user-friends text-2xl text-green-600"></i>
                  </div>
                </div>
                <div class="room-card bg-gradient-to-r from-purple-50 to-purple-100 p-4 rounded-lg border-2 border-transparent hover:border-purple-300 cursor-pointer transition-all duration-300" data-room="ห้อง 502">
                  <div class="flex items-center justify-between">
                    <div>
                      <h4 class="font-semibold text-gray-800">ห้อง 502</h4>
                    </div>
                    <i class="fas fa-crown text-2xl text-purple-600"></i>
                  </div>
                </div>
              </div>
            </div>
            
            <div class="flex justify-between mt-6">
              <button type="button" onclick="cancelBooking()" class="bg-gray-500 text-white px-6 py-3 rounded-lg hover:bg-gray-600 transition-colors font-semibold">
                <i class="fas fa-times mr-2"></i>ยกเลิก
              </button>
              <button type="button" id="nextToStep2" class="bg-blue-500 text-white px-6 py-3 rounded-lg hover:bg-blue-600 transition-colors font-semibold disabled:opacity-50 disabled:cursor-not-allowed" disabled>
                <i class="fas fa-arrow-right mr-2"></i>ถัดไป: เลือกเวลา
              </button>
            </div>
          </div>

          <!-- Step 2: Date & Time Selection -->
          <div id="step2" class="booking-step hidden">
            <div class="bg-gradient-to-r from-green-50 to-emerald-50 p-6 rounded-xl border border-green-200 mb-6">
              <h4 class="text-lg font-semibold text-green-800 mb-4">
                <i class="fas fa-clock mr-2"></i>ขั้นตอนที่ 2: เลือกวันที่และเวลา
              </h4>
              <p class="text-green-700 text-sm mb-4">กำหนดวันที่และช่วงเวลาที่ต้องการใช้ห้องประชุม</p>
              
              <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                <div>
                  <label class="block text-sm font-medium text-gray-700 mb-2">
                    <i class="fas fa-calendar mr-1 text-blue-600"></i>วันที่ *
                  </label>
                  <input type="date" id="bookingDateForm" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-blue-500 transition-colors" required>
                </div>

                <div>
                  <label class="block text-sm font-medium text-gray-700 mb-2">
                    <i class="fas fa-clock mr-1 text-green-600"></i>ช่วงเวลา *
                  </label>
                  <div class="grid grid-cols-2 gap-3">
                    <button type="button" class="time-slot-btn px-4 py-3 border-2 border-gray-300 rounded-lg hover:bg-blue-50 hover:border-blue-300 transition-all duration-200 text-center text-sm font-medium focus:outline-none focus:ring-2 focus:ring-blue-500" data-time="09:00-12:00">
                      <i class="fas fa-sun mr-1 text-yellow-500"></i>
                      <div class="font-semibold">09:00-12:00</div>
                      <div class="text-xs text-gray-500">ช่วงเช้า</div>
                    </button>
                    <button type="button" class="time-slot-btn px-4 py-3 border-2 border-gray-300 rounded-lg hover:bg-blue-50 hover:border-blue-300 transition-all duration-200 text-center text-sm font-medium focus:outline-none focus:ring-2 focus:ring-blue-500" data-time="13:00-16:00">
                      <i class="fas fa-sun mr-1 text-orange-500"></i>
                      <div class="font-semibold">13:00-16:00</div>
                      <div class="text-xs text-gray-500">ช่วงบ่าย</div>
                    </button>
                    <button type="button" class="time-slot-btn px-4 py-3 border-2 border-gray-300 rounded-lg hover:bg-blue-50 hover:border-blue-300 transition-all duration-200 text-center text-sm font-medium focus:outline-none focus:ring-2 focus:ring-blue-500" data-time="09:00-16:00">
                      <i class="fas fa-clock mr-1 text-blue-500"></i>
                      <div class="font-semibold">09:00-16:00</div>
                      <div class="text-xs text-gray-500">เต็มวัน</div>
                    </button>
                    <button type="button" class="time-slot-btn px-4 py-3 border-2 border-gray-300 rounded-lg hover:bg-blue-50 hover:border-blue-300 transition-all duration-200 text-center text-sm font-medium focus:outline-none focus:ring-2 focus:ring-blue-500" data-time="custom">
                      <i class="fas fa-edit mr-1 text-purple-500"></i>
                      <div class="font-semibold">กำหนดเอง</div>
                      <div class="text-xs text-gray-500">เลือกเวลา</div>
                    </button>
                  </div>
                </div>
              </div>

              <!-- Custom Time Section -->
              <div id="customTimeForm" class="hidden mt-4 p-4 bg-white rounded-lg border border-blue-200">
                <h5 class="text-sm font-semibold text-gray-700 mb-3">
                  <i class="fas fa-clock mr-2 text-purple-600"></i>กำหนดเวลาเอง
                </h5>
                <div class="grid grid-cols-2 gap-4">
                  <div>
                    <label class="block text-xs font-medium text-gray-600 mb-1">เวลาเริ่ม</label>
                    <input type="time" id="startTimeForm" class="w-full px-3 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-blue-500" min="08:00" max="18:00">
                  </div>
                  <div>
                    <label class="block text-xs font-medium text-gray-600 mb-1">เวลาสิ้นสุด</label>
                    <input type="time" id="endTimeForm" class="w-full px-3 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-blue-500" min="08:00" max="18:00">
                  </div>
                </div>
              </div>
            </div>
            
            <div class="flex justify-between mt-6">
              <button type="button" id="backToStep1" class="bg-gray-500 text-white px-6 py-3 rounded-lg hover:bg-gray-600 transition-colors font-semibold">
                <i class="fas fa-arrow-left mr-2"></i>ย้อนกลับ
              </button>
              <button type="button" id="nextToStep3" class="bg-green-500 text-white px-6 py-3 rounded-lg hover:bg-green-600 transition-colors font-semibold disabled:opacity-50 disabled:cursor-not-allowed" disabled>
                <i class="fas fa-arrow-right mr-2"></i>ถัดไป: กรอกข้อมูล
              </button>
            </div>
          </div>

          <!-- Step 3: Information Form -->
          <div id="step3" class="booking-step hidden">
            <div class="bg-gradient-to-r from-purple-50 to-pink-50 p-6 rounded-xl border border-purple-200 mb-6">
              <h4 class="text-lg font-semibold text-purple-800 mb-4">
                <i class="fas fa-user mr-2"></i>ขั้นตอนที่ 3: กรอกข้อมูลผู้จอง
              </h4>
              <p class="text-purple-700 text-sm mb-4">กรุณากรอกข้อมูลของผู้จองและรายละเอียดการประชุม</p>

              <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                <div>
                  <label class="block text-sm font-medium text-gray-700 mb-2">
                    <i class="fas fa-user mr-1 text-blue-600"></i>ชื่อผู้จอง *
                  </label>
                  <input type="text" id="bookerNameForm" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-blue-500 transition-colors" placeholder="กรอกชื่อ-นามสกุล" required>
                </div>
                
                <div>
                  <label class="block text-sm font-medium text-gray-700 mb-2">
                    <i class="fas fa-building mr-1 text-green-600"></i>แผนก *
                  </label>
                  <select id="departmentForm" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-blue-500 transition-colors" required>
                    <option value="">เลือกแผนก</option>
                    <option value="บริหาร">บริหาร</option>
                    <option value="บัญชีการเงิน">บัญชีการเงิน</option>
                    <option value="ทรัพยากรบุคคล">ทรัพยากรบุคคล</option>
                    <option value="ขาย">ขาย</option>
                    <option value="การตลาด">การตลาด</option>
                    <option value="โมเดิร์นเทรด">โมเดิร์นเทรด</option>
                    <option value="Consumer">Consumer</option>
                    <option value="Supply Chain">Supply Chain</option>
                    <option value="Ecom.">Ecom.</option>
                    <option value="Commu.">Commu.</option>
                    <option value="เลขานุการ">เลขานุการ</option>
                    <option value="IT">IT</option>
                  </select>
                </div>
              </div>

              <div>
                <label class="block text-sm font-medium text-gray-700 mb-2">
                  <i class="fas fa-clipboard-list mr-1 text-purple-600"></i>หัวข้อการประชุม *
                </label>
                <input type="text" id="meetingTopicForm" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-blue-500 transition-colors" placeholder="กรอกหัวข้อการประชุม" required>
              </div>

              <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                <div>
                  <label class="block text-sm font-medium text-gray-700 mb-2">
                    <i class="fas fa-users mr-1 text-orange-600"></i>จำนวนผู้เข้าร่วม *
                  </label>
                  <input type="number" id="attendeesForm" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-blue-500 transition-colors" placeholder="จำนวนคน (1-50)" min="1" max="50" required>
                </div>

                <div>
                  <label class="block text-sm font-medium text-gray-700 mb-2">
                    <i class="fas fa-phone mr-1 text-teal-600"></i>เบอร์โทรติดต่อ
                  </label>
                  <input type="tel" id="phoneForm" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-blue-500 transition-colors" placeholder="เบอร์โทรศัพท์ (ไม่บังคับ)">
                </div>
              </div>

              <!-- Equipment Selection -->
              <div class="bg-gradient-to-r from-green-50 to-emerald-50 p-6 rounded-xl border border-green-200 mt-6">
                <h5 class="text-lg font-semibold text-green-800 mb-4">
                  <i class="fas fa-tools mr-2"></i>อุปกรณ์ที่ต้องการ (ไม่บังคับ)
                </h5>
                <div class="grid grid-cols-2 md:grid-cols-3 gap-4">
                  <label class="flex items-center p-3 bg-white rounded-lg border border-green-200 hover:bg-green-50 cursor-pointer transition-colors">
                    <input type="checkbox" class="equipment-checkbox-form mr-3 text-green-600" value="โปรเจคเตอร์">
                    <div class="flex items-center">
                      <i class="fas fa-video text-green-600 mr-2"></i>
                      <span class="text-sm font-medium">โปรเจคเตอร์</span>
                    </div>
                  </label>
                  <label class="flex items-center p-3 bg-white rounded-lg border border-green-200 hover:bg-green-50 cursor-pointer transition-colors">
                    <input type="checkbox" class="equipment-checkbox-form mr-3 text-green-600" value="ไมโครโฟน">
                    <div class="flex items-center">
                      <i class="fas fa-microphone text-green-600 mr-2"></i>
                      <span class="text-sm font-medium">ไมโครโฟน</span>
                    </div>
                  </label>
                  <label class="flex items-center p-3 bg-white rounded-lg border border-green-200 hover:bg-green-50 cursor-pointer transition-colors">
                    <input type="checkbox" class="equipment-checkbox-form mr-3 text-green-600" value="กระดานไวท์บอร์ด">
                    <div class="flex items-center">
                      <i class="fas fa-chalkboard text-green-600 mr-2"></i>
                      <span class="text-sm font-medium">กระดานไวท์บอร์ด</span>
                    </div>
                  </label>
                  <label class="flex items-center p-3 bg-white rounded-lg border border-green-200 hover:bg-green-50 cursor-pointer transition-colors">
                    <input type="checkbox" class="equipment-checkbox-form mr-3 text-green-600" value="คอมพิวเตอร์">
                    <div class="flex items-center">
                      <i class="fas fa-laptop text-green-600 mr-2"></i>
                      <span class="text-sm font-medium">คอมพิวเตอร์</span>
                    </div>
                  </label>
                  <label class="flex items-center p-3 bg-white rounded-lg border border-green-200 hover:bg-green-50 cursor-pointer transition-colors">
                    <input type="checkbox" class="equipment-checkbox-form mr-3 text-green-600" value="เครื่องเสียง">
                    <div class="flex items-center">
                      <i class="fas fa-volume-up text-green-600 mr-2"></i>
                      <span class="text-sm font-medium">เครื่องเสียง</span>
                    </div>
                  </label>
                  <label class="flex items-center p-3 bg-white rounded-lg border border-green-200 hover:bg-green-50 cursor-pointer transition-colors">
                    <input type="checkbox" class="equipment-checkbox-form mr-3 text-green-600" value="กาแฟ/น้ำดื่ม">
                    <div class="flex items-center">
                      <i class="fas fa-coffee text-green-600 mr-2"></i>
                      <span class="text-sm font-medium">กาแฟ/น้ำดื่ม</span>
                    </div>
                  </label>
                </div>
              </div>
            </div>
            
            <div class="flex justify-between mt-6">
              <button type="button" id="backToStep2" class="bg-gray-500 text-white px-6 py-3 rounded-lg hover:bg-gray-600 transition-colors font-semibold">
                <i class="fas fa-arrow-left mr-2"></i>ย้อนกลับ
              </button>
              <button type="button" id="nextToStep4" class="bg-purple-500 text-white px-6 py-3 rounded-lg hover:bg-purple-600 transition-colors font-semibold">
                <i class="fas fa-arrow-right mr-2"></i>ถัดไป: ตรวจสอบข้อมูล
              </button>
            </div>
          </div>

          <!-- Step 4: Confirmation -->
          <div id="step4" class="booking-step hidden">
            <div class="bg-gradient-to-r from-orange-50 to-red-50 p-6 rounded-xl border border-orange-200 mb-6">
              <h4 class="text-lg font-semibold text-orange-800 mb-4">
                <i class="fas fa-check mr-2"></i>ขั้นตอนที่ 4: ตรวจสอบและยืนยันการจอง
              </h4>
              <p class="text-orange-700 text-sm mb-4">กรุณาตรวจสอบข้อมูลการจองให้ถูกต้องก่อนยืนยัน</p>
              
              <!-- Booking Summary -->
              <div id="bookingSummary" class="bg-white p-6 rounded-lg border border-orange-200 shadow-sm">
                <h5 class="text-lg font-bold text-gray-800 mb-4">
                  <i class="fas fa-clipboard-check mr-2 text-orange-600"></i>สรุปการจอง
                </h5>
                
                <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                  <div class="space-y-3">
                    <div class="flex items-center">
                      <i class="fas fa-door-open text-blue-600 mr-3 w-5"></i>
                      <span class="font-semibold text-gray-700">ห้องประชุม:</span>
                      <span class="ml-2 font-bold text-blue-800" id="summaryRoom">-</span>
                    </div>
                    <div class="flex items-center">
                      <i class="fas fa-calendar text-green-600 mr-3 w-5"></i>
                      <span class="font-semibold text-gray-700">วันที่:</span>
                      <span class="ml-2 text-gray-800" id="summaryDate">-</span>
                    </div>
                    <div class="flex items-center">
                      <i class="fas fa-clock text-orange-600 mr-3 w-5"></i>
                      <span class="font-semibold text-gray-700">เวลา:</span>
                      <span class="ml-2 font-bold text-orange-800" id="summaryTime">-</span>
                    </div>
                    <div class="flex items-center">
                      <i class="fas fa-clipboard-list text-purple-600 mr-3 w-5"></i>
                      <span class="font-semibold text-gray-700">หัวข้อ:</span>
                      <span class="ml-2 text-gray-800" id="summaryTopic">-</span>
                    </div>
                  </div>
                  
                  <div class="space-y-3">
                    <div class="flex items-center">
                      <i class="fas fa-user text-indigo-600 mr-3 w-5"></i>
                      <span class="font-semibold text-gray-700">ผู้จอง:</span>
                      <span class="ml-2 text-gray-800" id="summaryBooker">-</span>
                    </div>
                    <div class="flex items-center">
                      <i class="fas fa-building text-teal-600 mr-3 w-5"></i>
                      <span class="font-semibold text-gray-700">แผนก:</span>
                      <span class="ml-2 text-gray-800" id="summaryDepartment">-</span>
                    </div>
                    <div class="flex items-center">
                      <i class="fas fa-users text-pink-600 mr-3 w-5"></i>
                      <span class="font-semibold text-gray-700">จำนวนคน:</span>
                      <span class="ml-2 font-bold text-pink-800" id="summaryAttendees">-</span>
                    </div>
                    <div class="flex items-center" id="summaryPhoneRow" style="display: none;">
                      <i class="fas fa-phone text-cyan-600 mr-3 w-5"></i>
                      <span class="font-semibold text-gray-700">โทรศัพท์:</span>
                      <span class="ml-2 text-gray-800" id="summaryPhone">-</span>
                    </div>
                  </div>
                </div>
                
                <div id="summaryEquipmentSection" class="mt-6" style="display: none;">
                  <div class="flex items-start">
                    <i class="fas fa-tools text-gray-600 mr-3 w-5 mt-0.5"></i>
                    <div>
                      <span class="font-semibold text-gray-700">อุปกรณ์ที่ต้องการ:</span>
                      <div class="flex flex-wrap gap-2 mt-2" id="summaryEquipment">
                        <!-- Equipment items will be added here -->
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
            
            <!-- Form for submission -->
            <form id="submitForm">
              <div class="flex justify-between mt-6">
                <button type="button" id="backToStep3" class="bg-gray-500 text-white px-6 py-3 rounded-lg hover:bg-gray-600 transition-colors font-semibold">
                  <i class="fas fa-arrow-left mr-2"></i>ย้อนกลับ
                </button>
                <button type="submit" id="submitBookingForm" class="bg-gradient-to-r from-green-500 to-emerald-600 text-white px-8 py-4 rounded-lg hover:from-green-600 hover:to-emerald-700 transition-all duration-300 font-bold shadow-lg transform hover:scale-105 text-lg">
                  <i class="fas fa-check-circle mr-2"></i>ยืนยันการจอง
                </button>
              </div>
            </form>
          </div>
        </div>

        <!-- Today's Bookings Section -->
        <div id="todayBookingsSection" class="hidden fade-in">
          <div class="flex justify-between items-center mb-6">
            <h3 class="text-xl font-bold bg-gradient-to-r from-blue-600 to-indigo-600 bg-clip-text text-transparent">
              <i class="fas fa-calendar-day mr-2"></i>การจองวันนี้
            </h3>
            <div class="flex space-x-2">
              <button onclick="refreshTodayBookings()" class="bg-green-500 text-white px-4 py-2 rounded-lg hover:bg-green-600 transition-colors">
                <i class="fas fa-sync-alt mr-1"></i>รีเฟรช
              </button>
              <button onclick="hideTodayBookingsSection()" class="bg-gray-500 text-white px-4 py-2 rounded-lg hover:bg-gray-600 transition-colors">
                <i class="fas fa-times mr-1"></i>ปิด
              </button>
            </div>
          </div>
          
          <!-- Today's Bookings List -->
          <div id="todayBookingsList" class="space-y-4">
            <!-- Bookings will be dynamically loaded here -->
          </div>

          <!-- Empty State -->
          <div id="emptyTodayBookings" class="hidden text-center py-12">
            <div class="text-gray-400 text-6xl mb-4">
              <i class="fas fa-calendar-times"></i>
            </div>
            <h4 class="text-xl font-semibold text-gray-600 mb-2">ไม่มีการจองวันนี้</h4>
            <p class="text-gray-500 mb-6">ยังไม่มีการจองห้องประชุมในวันนี้</p>
            <button onclick="showBookingForm()" class="bg-blue-600 text-white px-6 py-3 rounded-lg hover:bg-blue-700 transition-colors">
              <i class="fas fa-plus mr-2"></i>จองห้องประชุมใหม่
            </button>
          </div>
        </div>
      </div>
    </div>

    <!-- Sidebar -->
    <div class="lg:col-span-1">
      <!-- Calendar Section -->
      <div class="bg-gradient-to-br from-white to-purple-50 rounded-2xl shadow-xl border border-purple-200 p-6 mb-6">
        <div class="flex justify-between items-center mb-4">
          <h2 class="text-xl font-bold bg-gradient-to-r from-purple-600 to-pink-600 bg-clip-text text-transparent">ปฏิทินการจอง</h2>
          <div class="flex items-center space-x-2">
            <button id="prevMonth" class="p-2 text-purple-600 hover:text-white hover:bg-gradient-to-r hover:from-purple-500 hover:to-pink-500 rounded-lg transition-all duration-300">
              <i class="fas fa-chevron-left"></i>
            </button>
            <button id="nextMonth" class="p-2 text-purple-600 hover:text-white hover:bg-gradient-to-r hover:from-purple-500 hover:to-pink-500 rounded-lg transition-all duration-300">
              <i class="fas fa-chevron-right"></i>
            </button>
          </div>
        </div>
        
        <div class="text-center mb-4">
          <h3 id="currentMonth" class="text-lg font-semibold text-gray-800"></h3>
        </div>
        
        <div class="grid grid-cols-7 gap-1 mb-2">
          <div class="text-center text-xs font-medium text-gray-500 py-2">อา</div>
          <div class="text-center text-xs font-medium text-gray-500 py-2">จ</div>
          <div class="text-center text-xs font-medium text-gray-500 py-2">อ</div>
          <div class="text-center text-xs font-medium text-gray-500 py-2">พ</div>
          <div class="text-center text-xs font-medium text-gray-500 py-2">พฤ</div>
          <div class="text-center text-xs font-medium text-gray-500 py-2">ศ</div>
          <div class="text-center text-xs font-medium text-gray-500 py-2">ส</div>
        </div>
        
        <div id="calendarGrid" class="grid grid-cols-7 gap-1">
          <!-- Calendar days will be generated here -->
        </div>
      </div>

      <div class="bg-gradient-to-br from-white to-purple-50 rounded-2xl shadow-xl border border-purple-200 p-6 mb-6">
        <h2 class="text-xl font-bold bg-gradient-to-r from-green-600 to-emerald-600 bg-clip-text text-transparent mb-6">การจองวันนี้</h2>
        <div id="todayBookings" class="space-y-4">
          <!-- Today's bookings will be dynamically generated here -->
        </div>
      </div>

      <!-- Quick Stats -->
      <div class="bg-gradient-to-br from-white to-orange-50 rounded-2xl shadow-xl border border-orange-200 p-6">
        <div class="flex justify-between items-center mb-4">
          <h3 class="text-lg font-semibold bg-gradient-to-r from-orange-600 to-red-600 bg-clip-text text-transparent">สถิติการใช้งาน</h3>
          <div id="statsAdminControls" class="admin-controls hidden">
            <button id="editStatsBtn" class="text-xs bg-blue-500 text-white px-2 py-1 rounded hover:bg-blue-600 mr-1" onclick="editStats()">
              <i class="fas fa-edit"></i> แก้ไข
            </button>
            <button id="resetStatsBtn" class="text-xs bg-red-500 text-white px-2 py-1 rounded hover:bg-red-600 mr-1" onclick="resetStats()">
              <i class="fas fa-trash"></i> รีเซ็ต
            </button>
            <button id="resetAllBtn" class="text-xs bg-orange-500 text-white px-2 py-1 rounded hover:bg-orange-600" onclick="resetAllData()">
              <i class="fas fa-exclamation-triangle"></i> รีเซ็ตทั้งหมด
            </button>
          </div>
        </div>
        <div id="statsContent" class="space-y-3">
          <div class="flex justify-between items-center">
            <span class="text-gray-600">การจองวันนี้</span>
            <span class="font-semibold text-blue-600" id="todayCount">2</span>
          </div>
          <div class="flex justify-between items-center">
            <span class="text-gray-600">การจองสัปดาห์นี้</span>
            <span class="font-semibold text-green-600" id="weekCount">8</span>
          </div>
          <div class="flex justify-between items-center">
            <span class="text-gray-600">ห้องที่ใช้มากที่สุด</span>
            <span class="font-semibold text-purple-600" id="popularRoom">ห้อง 500</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>

<!-- Footer -->
<footer class="bg-gradient-to-r from-gray-800 via-gray-900 to-black text-white mt-16">
  <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-12">
    <div class="grid grid-cols-1 md:grid-cols-4 gap-8">
      <!-- Company Info -->
      <div class="col-span-1 md:col-span-2">
        <div class="flex items-center mb-6">
          <div class="bg-gradient-to-r from-purple-600 to-pink-600 p-3 rounded-full mr-4">
            <i class="fas fa-building text-2xl text-white"></i>
          </div>
          <div>
            <h3 class="text-2xl font-bold bg-gradient-to-r from-purple-400 to-pink-400 bg-clip-text text-transparent">
              TAISIN GROUP
            </h3>
            <p class="text-gray-300 text-sm">ระบบการจองห้องประชุมออนไลน์</p>
          </div>
        </div>
        <p class="text-gray-300 mb-4 leading-relaxed">
          ระบบการจองห้องประชุมที่ทันสมัย ใช้งานง่าย และมีประสิทธิภาพ 
          สำหรับพนักงานทุกคนในกลุ่มบริษัท TAISIN เพื่อการประชุมที่ราบรื่น
        </p>
        <div class="flex space-x-4">
          <a href="#" class="bg-blue-600 hover:bg-blue-700 p-3 rounded-full transition-colors">
            <i class="fab fa-facebook-f text-white"></i>
          </a>
          <a href="#" class="bg-green-600 hover:bg-green-700 p-3 rounded-full transition-colors">
            <i class="fab fa-line text-white"></i>
          </a>
          <a href="#" class="bg-red-600 hover:bg-red-700 p-3 rounded-full transition-colors">
            <i class="fas fa-envelope text-white"></i>
          </a>
          <a href="#" class="bg-gray-600 hover:bg-gray-700 p-3 rounded-full transition-colors">
            <i class="fas fa-phone text-white"></i>
          </a>
        </div>
      </div>

      <!-- Quick Links -->
      <div>
        <h4 class="text-lg font-semibold mb-4 text-purple-400">
          <i class="fas fa-link mr-2"></i>เมนูหลัก
        </h4>
        <ul class="space-y-3">
          <li>
            <button onclick="showWelcomeSection()" class="text-gray-300 hover:text-purple-400 transition-colors flex items-center">
              <i class="fas fa-home mr-2 w-4"></i>หน้าหลัก
            </button>
          </li>
          <li>
            <button onclick="showBookingForm()" class="text-gray-300 hover:text-purple-400 transition-colors flex items-center">
              <i class="fas fa-plus mr-2 w-4"></i>จองห้องประชุม
            </button>
          </li>
          <li>
            <button onclick="showTodayBookingsSection()" class="text-gray-300 hover:text-purple-400 transition-colors flex items-center">
              <i class="fas fa-calendar-day mr-2 w-4"></i>การจองวันนี้
            </button>
          </li>
          <li>
            <button onclick="showAdminModal()" class="text-gray-300 hover:text-purple-400 transition-colors flex items-center">
              <i class="fas fa-user-shield mr-2 w-4"></i>ผู้ดูแลระบบ
            </button>
          </li>
        </ul>
      </div>

      <!-- Contact Info -->
      <div>
        <h4 class="text-lg font-semibold mb-4 text-purple-400">
          <i class="fas fa-address-book mr-2"></i>ติดต่อเรา
        </h4>
        <ul class="space-y-3 text-gray-300">
          <li class="flex items-start">
            <i class="fas fa-map-marker-alt mr-3 w-4 mt-1 text-purple-400"></i>
            <div>
              <div class="font-medium">สำนักงานใหญ่</div>
              <div class="text-sm">1521 Sukhumvit Rd, Kwaeng Phrakhanong-North, Watthana, Bangkok 10110</div>
            </div>
          </li>
          <li class="flex items-center">
            <i class="fas fa-phone mr-3 w-4 text-purple-400"></i>
            <div>
              <div class="font-medium">02-714-0777</div>
              <div class="text-sm text-gray-400">จันทร์-ศุกร์ 08:30-17:30</div>
            </div>
          </li>
          <li class="flex items-center">
            <i class="fas fa-envelope mr-3 w-4 text-purple-400"></i>
            <div>
              <div class="font-medium">booking@taisin.co.th</div>
              <div class="text-sm text-gray-400">สำหรับการจองห้องประชุม</div>
            </div>
          </li>
          <li class="flex items-center">
            <i class="fas fa-globe mr-3 w-4 text-purple-400"></i>
            <div>
              <div class="font-medium">www.taisin.co.th</div>
              <div class="text-sm text-gray-400">เว็บไซต์หลัก</div>
            </div>
          </li>
        </ul>
      </div>
    </div>

    <!-- Bottom Bar -->
    <div class="border-t border-gray-700 mt-8 pt-8">
      <div class="flex flex-col md:flex-row justify-between items-center">
        <div class="text-gray-400 text-sm mb-4 md:mb-0">
          <p>&copy; 2024 TAISIN GROUP. สงวนลิขสิทธิ์ทุกประการ</p>
          <p class="mt-1">ระบบการจองห้องประชุม เวอร์ชัน 2.1.0</p>
        </div>
        <div class="flex items-center space-x-6 text-sm text-gray-400">
          <div class="flex items-center">
            <i class="fas fa-shield-alt mr-2 text-green-400"></i>
            <span>ระบบปลอดภัย SSL</span>
          </div>
          <div class="flex items-center">
            <i class="fas fa-clock mr-2 text-blue-400"></i>
            <span>อัพเดทล่าสุด: <span id="lastUpdate">วันนี้</span></span>
          </div>
          <div class="flex items-center">
            <i class="fas fa-users mr-2 text-purple-400"></i>
            <span>ผู้ใช้งาน: <span id="totalUsers">150+</span> คน</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</footer>

<!-- Admin Menu Modal -->
<div id="adminMenuModal" class="fixed inset-0 bg-black bg-opacity-50 modal-backdrop hidden flex items-center justify-center z-50">
  <div class="bg-white rounded-2xl p-8 max-w-4xl mx-4 w-full max-h-screen overflow-y-auto">
    <div class="flex justify-between items-center mb-6">
      <div class="flex items-center">
        <div class="bg-gradient-to-r from-red-500 to-orange-600 p-3 rounded-full mr-4">
          <i class="fas fa-user-shield text-2xl text-white"></i>
        </div>
        <div>
          <h3 class="text-2xl font-bold text-gray-800">เมนูผู้ดูแลระบบ</h3>
          <p class="text-sm text-gray-600">จัดการข้อมูลการจองห้องประชุม</p>
        </div>
      </div>
      <button id="closeAdminMenu" class="text-gray-500 hover:text-gray-700 text-2xl">
        <i class="fas fa-times"></i>
      </button>
    </div>

    <!-- Admin Action Buttons -->
    <div class="grid grid-cols-1 md:grid-cols-2 gap-6 mb-8 max-w-2xl mx-auto">
      <button id="addNewBookingBtn" class="bg-gradient-to-r from-green-500 to-emerald-600 text-white p-8 rounded-xl hover:from-green-600 hover:to-emerald-700 transition-all duration-300 shadow-lg transform hover:scale-105">
        <div class="text-center">
          <i class="fas fa-plus-circle text-4xl mb-4"></i>
          <h4 class="text-xl font-bold mb-3">เพิ่มการจองใหม่</h4>
          <p class="text-sm opacity-90">สร้างการจองใหม่โดยผู้ดูแลระบบ</p>
        </div>
      </button>

      <button id="manageBookingsBtn" class="bg-gradient-to-r from-blue-500 to-indigo-600 text-white p-8 rounded-xl hover:from-blue-600 hover:to-indigo-700 transition-all duration-300 shadow-lg transform hover:scale-105">
        <div class="text-center">
          <i class="fas fa-list-alt text-4xl mb-4"></i>
          <h4 class="text-xl font-bold mb-3">จัดการการจอง</h4>
          <p class="text-sm opacity-90">ดู แก้ไข ลบการจองทั้งหมด</p>
        </div>
      </button>
    </div>

    <!-- Quick Stats for Admin -->
    <div class="bg-gradient-to-r from-gray-50 to-blue-50 p-6 rounded-xl border border-gray-200 mb-6">
      <h4 class="text-lg font-bold text-gray-800 mb-4">
        <i class="fas fa-chart-bar mr-2 text-blue-600"></i>สถิติระบบ
      </h4>
      <div class="grid grid-cols-2 md:grid-cols-4 gap-4">
        <div class="text-center">
          <div class="text-2xl font-bold text-blue-600" id="adminTotalBookings">0</div>
          <div class="text-sm text-gray-600">การจองทั้งหมด</div>
        </div>
        <div class="text-center">
          <div class="text-2xl font-bold text-green-600" id="adminTodayBookings">0</div>
          <div class="text-sm text-gray-600">การจองวันนี้</div>
        </div>
        <div class="text-center">
          <div class="text-2xl font-bold text-orange-600" id="adminThisWeekBookings">0</div>
          <div class="text-sm text-gray-600">การจองสัปดาห์นี้</div>
        </div>
        <div class="text-center">
          <div class="text-2xl font-bold text-purple-600" id="adminActiveRooms">5</div>
          <div class="text-sm text-gray-600">ห้องทั้งหมด</div>
        </div>
      </div>
    </div>

    <div class="flex justify-end">
      <button id="closeAdminMenuBtn" class="bg-gray-600 text-white px-6 py-3 rounded-lg hover:bg-gray-700 transition-colors">
        <i class="fas fa-times mr-2"></i>ปิด
      </button>
    </div>
  </div>
</div>

<!-- Admin Add Booking Modal -->
<div id="adminAddBookingModal" class="fixed inset-0 bg-black bg-opacity-50 modal-backdrop hidden flex items-center justify-center z-50">
  <div class="bg-white rounded-2xl p-8 max-w-4xl mx-4 w-full max-h-screen overflow-y-auto">
    <div class="flex justify-between items-center mb-6">
      <h3 class="text-2xl font-bold text-gray-800">
        <i class="fas fa-plus-circle mr-2 text-green-600"></i>เพิ่มการจองใหม่ (Admin)
      </h3>
      <button id="closeAdminAddBooking" class="text-gray-500 hover:text-gray-700 text-2xl">
        <i class="fas fa-times"></i>
      </button>
    </div>

    <form id="adminAddBookingForm" class="space-y-6">
      <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
        <div>
          <label class="block text-sm font-medium text-gray-700 mb-2">
            <i class="fas fa-door-open mr-1 text-blue-600"></i>ห้องประชุม *
          </label>
          <select id="adminRoom" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-blue-500" required>
            <option value="">เลือกห้อง</option>
            <option value="ห้อง 1A">ห้อง 1A</option>
            <option value="ห้อง 1B">ห้อง 1B</option>
            <option value="ห้อง 500">ห้อง 500</option>
            <option value="ห้อง 501">ห้อง 501</option>
            <option value="ห้อง 502">ห้อง 502</option>
          </select>
        </div>

        <div>
          <label class="block text-sm font-medium text-gray-700 mb-2">
            <i class="fas fa-calendar mr-1 text-green-600"></i>วันที่ *
          </label>
          <input type="date" id="adminDate" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-blue-500" required>
        </div>
      </div>

      <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
        <div>
          <label class="block text-sm font-medium text-gray-700 mb-2">
            <i class="fas fa-clock mr-1 text-orange-600"></i>เวลาเริ่ม *
          </label>
          <input type="time" id="adminStartTime" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-blue-500" required>
        </div>

        <div>
          <label class="block text-sm font-medium text-gray-700 mb-2">
            <i class="fas fa-clock mr-1 text-red-600"></i>เวลาสิ้นสุด *
          </label>
          <input type="time" id="adminEndTime" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-blue-500" required>
        </div>
      </div>

      <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
        <div>
          <label class="block text-sm font-medium text-gray-700 mb-2">
            <i class="fas fa-user mr-1 text-purple-600"></i>ชื่อผู้จอง *
          </label>
          <input type="text" id="adminBooker" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-blue-500" placeholder="กรอกชื่อ-นามสกุล" required>
        </div>

        <div>
          <label class="block text-sm font-medium text-gray-700 mb-2">
            <i class="fas fa-building mr-1 text-teal-600"></i>แผนก *
          </label>
          <select id="adminDepartment" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-blue-500" required>
            <option value="">เลือกแผนก</option>
            <option value="บริหาร">บริหาร</option>
            <option value="บัญชีการเงิน">บัญชีการเงิน</option>
            <option value="ทรัพยากรบุคคล">ทรัพยากรบุคคล</option>
            <option value="ขาย">ขาย</option>
            <option value="การตลาด">การตลาด</option>
            <option value="โมเดิร์นเทรด">โมเดิร์นเทรด</option>
            <option value="Consumer">Consumer</option>
            <option value="Supply Chain">Supply Chain</option>
            <option value="Ecom.">Ecom.</option>
            <option value="Commu.">Commu.</option>
            <option value="เลขานุการ">เลขานุการ</option>
            <option value="IT">IT</option>
          </select>
        </div>
      </div>

      <div>
        <label class="block text-sm font-medium text-gray-700 mb-2">
          <i class="fas fa-clipboard-list mr-1 text-indigo-600"></i>หัวข้อการประชุม *
        </label>
        <input type="text" id="adminTopic" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-blue-500" placeholder="กรอกหัวข้อการประชุม" required>
      </div>

      <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
        <div>
          <label class="block text-sm font-medium text-gray-700 mb-2">
            <i class="fas fa-users mr-1 text-pink-600"></i>จำนวนผู้เข้าร่วม *
          </label>
          <input type="number" id="adminAttendees" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-blue-500" placeholder="จำนวนคน" min="1" max="50" required>
        </div>

        <div>
          <label class="block text-sm font-medium text-gray-700 mb-2">
            <i class="fas fa-phone mr-1 text-cyan-600"></i>เบอร์โทรติดต่อ
          </label>
          <input type="tel" id="adminPhone" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-blue-500" placeholder="เบอร์โทรศัพท์">
        </div>
      </div>

      <div>
        <label class="block text-sm font-medium text-gray-700 mb-2">
          <i class="fas fa-tools mr-1 text-gray-600"></i>อุปกรณ์ที่ต้องการ
        </label>
        <div class="grid grid-cols-2 md:grid-cols-3 gap-3">
          <label class="flex items-center p-3 bg-gray-50 rounded-lg border hover:bg-gray-100 cursor-pointer">
            <input type="checkbox" class="admin-equipment-checkbox mr-3" value="โปรเจคเตอร์">
            <span class="text-sm">โปรเจคเตอร์</span>
          </label>
          <label class="flex items-center p-3 bg-gray-50 rounded-lg border hover:bg-gray-100 cursor-pointer">
            <input type="checkbox" class="admin-equipment-checkbox mr-3" value="ไมโครโฟน">
            <span class="text-sm">ไมโครโฟน</span>
          </label>
          <label class="flex items-center p-3 bg-gray-50 rounded-lg border hover:bg-gray-100 cursor-pointer">
            <input type="checkbox" class="admin-equipment-checkbox mr-3" value="กระดานไวท์บอร์ด">
            <span class="text-sm">กระดานไวท์บอร์ด</span>
          </label>
          <label class="flex items-center p-3 bg-gray-50 rounded-lg border hover:bg-gray-100 cursor-pointer">
            <input type="checkbox" class="admin-equipment-checkbox mr-3" value="คอมพิวเตอร์">
            <span class="text-sm">คอมพิวเตอร์</span>
          </label>
          <label class="flex items-center p-3 bg-gray-50 rounded-lg border hover:bg-gray-100 cursor-pointer">
            <input type="checkbox" class="admin-equipment-checkbox mr-3" value="เครื่องเสียง">
            <span class="text-sm">เครื่องเสียง</span>
          </label>
          <label class="flex items-center p-3 bg-gray-50 rounded-lg border hover:bg-gray-100 cursor-pointer">
            <input type="checkbox" class="admin-equipment-checkbox mr-3" value="กาแฟ/น้ำดื่ม">
            <span class="text-sm">กาแฟ/น้ำดื่ม</span>
          </label>
        </div>
      </div>

      <div class="flex space-x-4 pt-4">
        <button type="submit" class="flex-1 bg-gradient-to-r from-green-500 to-emerald-600 text-white py-4 rounded-lg hover:from-green-600 hover:to-emerald-700 transition-all duration-300 font-semibold shadow-lg">
          <i class="fas fa-plus mr-2"></i>เพิ่มการจอง
        </button>
        <button type="button" id="cancelAdminAddBooking" class="px-8 bg-gray-300 text-gray-700 py-4 rounded-lg hover:bg-gray-400 transition-colors font-semibold">
          <i class="fas fa-times mr-2"></i>ยกเลิก
        </button>
      </div>
    </form>
  </div>
</div>

<!-- Admin Manage Bookings Modal -->
<div id="adminManageBookingsModal" class="fixed inset-0 bg-black bg-opacity-50 modal-backdrop hidden flex items-center justify-center z-50">
  <div class="bg-white rounded-2xl p-8 max-w-6xl mx-4 w-full max-h-screen overflow-y-auto">
    <div class="flex justify-between items-center mb-6">
      <h3 class="text-2xl font-bold text-gray-800">
        <i class="fas fa-list-alt mr-2 text-blue-600"></i>จัดการการจองทั้งหมด
      </h3>
      <button id="closeAdminManageBookings" class="text-gray-500 hover:text-gray-700 text-2xl">
        <i class="fas fa-times"></i>
      </button>
    </div>

    <!-- Filter and Search -->
    <div class="bg-gray-50 p-4 rounded-lg mb-6">
      <div class="grid grid-cols-1 md:grid-cols-4 gap-4">
        <div>
          <label class="block text-sm font-medium text-gray-700 mb-1">ค้นหา</label>
          <input type="text" id="adminSearchBookings" class="w-full px-3 py-2 border border-gray-300 rounded text-sm" placeholder="ค้นหาชื่อ, หัวข้อ, ห้อง...">
        </div>
        <div>
          <label class="block text-sm font-medium text-gray-700 mb-1">กรองตามห้อง</label>
          <select id="adminFilterRoom" class="w-full px-3 py-2 border border-gray-300 rounded text-sm">
            <option value="">ทุกห้อง</option>
            <option value="ห้อง 1A">ห้อง 1A</option>
            <option value="ห้อง 1B">ห้อง 1B</option>
            <option value="ห้อง 500">ห้อง 500</option>
            <option value="ห้อง 501">ห้อง 501</option>
            <option value="ห้อง 502">ห้อง 502</option>
          </select>
        </div>
        <div>
          <label class="block text-sm font-medium text-gray-700 mb-1">กรองตามวันที่</label>
          <select id="adminFilterDate" class="w-full px-3 py-2 border border-gray-300 rounded text-sm">
            <option value="">ทุกวัน</option>
            <option value="today">วันนี้</option>
            <option value="tomorrow">พรุ่งนี้</option>
            <option value="thisweek">สัปดาห์นี้</option>
            <option value="nextweek">สัปดาห์หน้า</option>
          </select>
        </div>
        <div>
          <label class="block text-sm font-medium text-gray-700 mb-1">เรียงตาม</label>
          <select id="adminSortBy" class="w-full px-3 py-2 border border-gray-300 rounded text-sm">
            <option value="date">วันที่</option>
            <option value="time">เวลา</option>
            <option value="room">ห้อง</option>
            <option value="booker">ผู้จอง</option>
            <option value="created">วันที่สร้าง</option>
          </select>
        </div>
      </div>
      
      <div class="flex justify-between items-center mt-4">
        <div class="flex items-center space-x-4">
          <button id="adminSelectAllBookings" class="text-sm bg-blue-500 text-white px-3 py-2 rounded hover:bg-blue-600">
            <i class="fas fa-check-square mr-1"></i>เลือกทั้งหมด
          </button>
          <button id="adminDeleteSelectedBookings" class="text-sm bg-red-500 text-white px-3 py-2 rounded hover:bg-red-600">
            <i class="fas fa-trash mr-1"></i>ลบที่เลือก
          </button>
        </div>
        <div class="text-sm text-gray-600">
          รายการทั้งหมด: <span id="adminTotalBookingsCount">0</span> รายการ
        </div>
      </div>
    </div>

    <!-- Bookings List -->
    <div id="adminBookingsList" class="space-y-4 max-h-96 overflow-y-auto">
      <!-- Bookings will be loaded here -->
    </div>

    <div class="flex justify-end mt-6">
      <button id="closeAdminManageBookingsBtn" class="bg-gray-600 text-white px-6 py-3 rounded-lg hover:bg-gray-700 transition-colors">
        <i class="fas fa-times mr-2"></i>ปิด
      </button>
    </div>
  </div>
</div>

<!-- Admin Login Modal -->
<div id="adminModal" class="fixed inset-0 bg-black bg-opacity-50 modal-backdrop hidden flex items-center justify-center z-50">
  <div class="bg-white rounded-2xl p-8 max-w-md mx-4">
    <div class="text-center mb-6">
      <div class="bg-gradient-to-r from-red-500 to-orange-600 p-4 rounded-full w-20 h-20 mx-auto mb-4 flex items-center justify-center shadow-lg">
        <i class="fas fa-user-shield text-3xl text-white"></i>
      </div>
      <h3 class="text-2xl font-bold text-gray-800 mb-2">เข้าสู่ระบบผู้ดูแล</h3>
      <p class="text-sm text-gray-600">กรุณาใส่รหัสผ่านเพื่อเข้าสู่โหมดผู้ดูแลระบบ</p>
    </div>
    
    <!-- Admin Features Info -->
    <div class="bg-gradient-to-r from-blue-50 to-purple-50 p-4 rounded-xl border border-blue-200 mb-6">
      <div class="text-sm text-blue-800 font-medium mb-3 text-center">
        <i class="fas fa-crown mr-2 text-yellow-500"></i>สิทธิ์ผู้ดูแลระบบ
      </div>
      <div class="grid grid-cols-2 gap-3 text-xs">
        <div class="flex items-center text-green-700">
          <i class="fas fa-plus-circle mr-2 text-green-600"></i>เพิ่มการจอง
        </div>
        <div class="flex items-center text-blue-700">
          <i class="fas fa-edit mr-2 text-blue-600"></i>แก้ไขข้อมูล
        </div>
        <div class="flex items-center text-red-700">
          <i class="fas fa-trash mr-2 text-red-600"></i>ลบการจอง
        </div>
        <div class="flex items-center text-purple-700">
          <i class="fas fa-chart-bar mr-2 text-purple-600"></i>ดูสถิติ
        </div>
      </div>
    </div>
    
    <!-- Password Input Form -->
    <form id="adminLoginForm" class="space-y-4">
      <div>
        <label class="block text-sm font-medium text-gray-700 mb-2">
          <i class="fas fa-lock mr-1 text-red-600"></i>รหัสผ่านผู้ดูแลระบบ *
        </label>
        <div class="relative">
          <input type="password" id="adminPassword" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-red-500 focus:border-red-500 transition-colors pr-12" placeholder="กรอกรหัสผ่าน" required>
          <button type="button" id="togglePassword" class="absolute right-3 top-1/2 transform -translate-y-1/2 text-gray-500 hover:text-gray-700 transition-colors">
            <i class="fas fa-eye" id="passwordIcon"></i>
          </button>
        </div>
        <div id="passwordError" class="hidden mt-2 text-sm text-red-600">
          <i class="fas fa-exclamation-triangle mr-1"></i>รหัสผ่านไม่ถูกต้อง กรุณาลองใหม่อีกครั้ง
        </div>
        <div class="mt-2 text-xs text-gray-500">
          <i class="fas fa-info-circle mr-1"></i>หากลืมรหัสผ่าน กรุณาติดต่อผู้ดูแลระบบ
        </div>
      </div>
      
      <!-- Login Button -->
      <div class="flex justify-center pt-2">
        <button type="submit" class="w-full bg-gradient-to-r from-red-500 to-orange-600 text-white px-8 py-4 rounded-xl hover:from-red-600 hover:to-orange-700 transition-all duration-300 font-bold shadow-lg transform hover:scale-105 text-lg">
          <i class="fas fa-sign-in-alt mr-3"></i>เข้าสู่ระบบ
        </button>
      </div>
    </form>
    
    <!-- Close Button -->
    <div class="flex justify-center mt-4">
      <button id="cancelAdmin" class="text-gray-500 hover:text-gray-700 transition-colors text-sm" onclick="closeAdminModal()">
        <i class="fas fa-times mr-1"></i>ปิด
      </button>
    </div>
  </div>
</div>

<!-- Success Modal -->
<div id="successModal" class="fixed inset-0 bg-black bg-opacity-70 modal-backdrop hidden flex items-center justify-center z-50">
  <!-- Fireworks Background -->
  <div class="fireworks-container absolute inset-0 pointer-events-none overflow-hidden">
    <!-- Fireworks will be generated by JavaScript -->
  </div>
  
  <!-- Confetti Background -->
  <div class="confetti-container absolute inset-0 pointer-events-none overflow-hidden">
    <!-- Confetti pieces will be generated by JavaScript -->
  </div>
  
  <!-- Floating Particles -->
  <div class="particles-container absolute inset-0 pointer-events-none">
    <div class="particle particle-1"></div>
    <div class="particle particle-2"></div>
    <div class="particle particle-3"></div>
    <div class="particle particle-4"></div>
    <div class="particle particle-5"></div>
    <div class="particle particle-6"></div>
  </div>
  
  <!-- Celebration Rays -->
  <div class="celebration-rays absolute inset-0 pointer-events-none">
    <div class="ray ray-1"></div>
    <div class="ray ray-2"></div>
    <div class="ray ray-3"></div>
    <div class="ray ray-4"></div>
    <div class="ray ray-5"></div>
    <div class="ray ray-6"></div>
    <div class="ray ray-7"></div>
    <div class="ray ray-8"></div>
  </div>
  
  <div class="bg-white rounded-3xl p-8 max-w-2xl mx-4 text-center relative overflow-hidden shadow-2xl transform animate-successBounce border-4 border-gradient-to-r from-green-400 via-blue-400 to-purple-400">
    <!-- Animated Background Gradient -->
    <div class="absolute inset-0 bg-gradient-to-br from-green-100 via-blue-50 to-purple-100 opacity-40 animate-gradientShift"></div>
    
    <!-- Celebration Banner -->
    <div class="absolute -top-4 -left-4 -right-4 h-8 bg-gradient-to-r from-green-400 via-blue-400 to-purple-400 transform -rotate-2 opacity-80"></div>
    <div class="absolute -top-2 -left-4 -right-4 h-8 bg-gradient-to-r from-purple-400 via-pink-400 to-yellow-400 transform rotate-1 opacity-60"></div>
    
    <!-- Success Icon with Multiple Animations -->
    <div class="relative z-10 mb-8">
      <!-- Outer Ring Animation -->
      <div class="relative inline-block">
        <div class="absolute inset-0 rounded-full bg-green-500 opacity-20 animate-ping scale-200"></div>
        <div class="absolute inset-0 rounded-full bg-green-400 opacity-30 animate-pulse scale-150"></div>
        <div class="absolute inset-0 rounded-full bg-blue-400 opacity-20 animate-ping scale-175" style="animation-delay: 0.5s;"></div>
        
        <!-- Main Success Icon -->
        <div class="relative bg-gradient-to-br from-green-400 via-emerald-500 to-green-600 text-white rounded-full w-24 h-24 flex items-center justify-center shadow-2xl animate-successIcon border-4 border-white">
          <i class="fas fa-check text-4xl animate-checkmark"></i>
        </div>
        
        <!-- Enhanced Sparkle Effects -->
        <div class="absolute -top-4 -right-4 text-yellow-400 animate-sparkle1">
          <i class="fas fa-star text-2xl"></i>
        </div>
        <div class="absolute -bottom-2 -left-2 text-yellow-300 animate-sparkle2">
          <i class="fas fa-star text-lg"></i>
        </div>
        <div class="absolute top-2 -left-6 text-yellow-500 animate-sparkle3">
          <i class="fas fa-star text-sm"></i>
        </div>
        <div class="absolute -top-2 left-6 text-pink-400 animate-sparkle1" style="animation-delay: 0.3s;">
          <i class="fas fa-heart text-lg"></i>
        </div>
        <div class="absolute bottom-4 -right-2 text-blue-400 animate-sparkle2" style="animation-delay: 0.6s;">
          <i class="fas fa-gem text-sm"></i>
        </div>
        
        <!-- Rotating Success Ring -->
        <div class="absolute inset-0 rounded-full border-4 border-dashed border-green-300 animate-spin" style="animation-duration: 3s;"></div>
      </div>
    </div>
    
    <!-- Success Message with Enhanced Typography -->
    <div class="relative z-10 mb-6">
      <h3 class="text-4xl font-black bg-gradient-to-r from-green-600 via-blue-600 to-purple-600 bg-clip-text text-transparent mb-4 animate-titleSlide">
        🎉 จองสำเร็จ! 🎉
      </h3>
      <div class="flex items-center justify-center mb-4">
        <div class="h-2 bg-gradient-to-r from-green-400 via-blue-400 to-purple-400 rounded-full animate-progressBar shadow-lg" style="width: 0; animation-fill-mode: forwards;"></div>
      </div>
      <p class="text-gray-700 text-lg font-medium animate-fadeInUp" style="animation-delay: 0.5s; opacity: 0; animation-fill-mode: forwards;">
        🎊 การจองห้องประชุมของคุณได้รับการยืนยันแล้ว 🎊
      </p>
      <p class="text-gray-600 text-sm mt-2 animate-fadeInUp" style="animation-delay: 0.7s; opacity: 0; animation-fill-mode: forwards;">
        ระบบได้บันทึกข้อมูลการจองเรียบร้อยแล้ว
      </p>
      
      <!-- Enhanced Success Stats -->
      <div class="flex justify-center space-x-8 mt-6 animate-fadeInUp" style="animation-delay: 0.8s; opacity: 0; animation-fill-mode: forwards;">
        <div class="text-center bg-green-50 p-4 rounded-xl border-2 border-green-200 shadow-md">
          <div class="text-2xl font-bold text-green-600 animate-countUp" data-target="100">0</div>
          <div class="text-sm text-gray-600 font-medium">% สำเร็จ</div>
          <i class="fas fa-check-circle text-green-500 text-lg mt-1"></i>
        </div>
        <div class="text-center bg-blue-50 p-4 rounded-xl border-2 border-blue-200 shadow-md">
          <div class="text-2xl font-bold text-blue-600 animate-countUp" data-target="2" data-suffix=" นาที">0</div>
          <div class="text-sm text-gray-600 font-medium">ใช้เวลา</div>
          <i class="fas fa-clock text-blue-500 text-lg mt-1"></i>
        </div>
        <div class="text-center bg-purple-50 p-4 rounded-xl border-2 border-purple-200 shadow-md">
          <div class="text-2xl font-bold text-purple-600">
            <i class="fas fa-heart animate-heartbeat"></i>
          </div>
          <div class="text-sm text-gray-600 font-medium">ขอบคุณ</div>
          <div class="text-xs text-purple-500 mt-1">TAISIN GROUP</div>
        </div>
      </div>
    </div>
    
    <!-- Booking Details with Enhanced Design -->
    <div id="bookingDetails" class="relative z-10 bg-gradient-to-br from-white to-gray-50 p-6 rounded-2xl mb-6 text-left shadow-lg border-2 border-gray-100 animate-slideUp" style="animation-delay: 1s; opacity: 0; animation-fill-mode: forwards;">
      <!-- Details will be inserted here with enhanced styling -->
    </div>
    
    <!-- Action Buttons with Enhanced Design -->
    <div class="relative z-10 flex flex-wrap gap-3 justify-center animate-fadeInUp" style="animation-delay: 1.2s; opacity: 0; animation-fill-mode: forwards;">
      <button id="shareBookingLine" class="bg-gradient-to-r from-green-500 to-green-600 text-white px-4 py-3 rounded-xl hover:from-green-600 hover:to-green-700 transition-all duration-300 flex items-center justify-center shadow-lg text-sm font-semibold transform hover:scale-105 hover:shadow-xl">
        <i class="fab fa-line mr-2 text-lg"></i>
        <span>แชร์ LINE</span>
      </button>
      
      <button id="shareBookingEmail" class="bg-gradient-to-r from-blue-500 to-blue-600 text-white px-4 py-3 rounded-xl hover:from-blue-600 hover:to-blue-700 transition-all duration-300 flex items-center justify-center shadow-lg text-sm font-semibold transform hover:scale-105 hover:shadow-xl">
        <i class="fas fa-envelope mr-2 text-lg"></i>
        <span>ส่ง Email</span>
      </button>
      
      <button id="printBooking" class="bg-gradient-to-r from-purple-500 to-purple-600 text-white px-4 py-3 rounded-xl hover:from-purple-600 hover:to-purple-700 transition-all duration-300 flex items-center justify-center shadow-lg text-sm font-semibold transform hover:scale-105 hover:shadow-xl">
        <i class="fas fa-print mr-2 text-lg"></i>
        <span>พิมพ์</span>
      </button>
      
      <button id="closeModal" class="bg-gradient-to-r from-gray-600 to-gray-700 text-white px-8 py-4 rounded-2xl hover:from-gray-700 hover:to-gray-800 transition-all duration-300 flex items-center justify-center shadow-xl text-lg font-bold transform hover:scale-105 hover:shadow-2xl border-2 border-gray-500">
        <i class="fas fa-times mr-3 text-xl"></i>
        <span>ปิด</span>
      </button>
    </div>
    
    <!-- Enhanced Decorative Elements -->
    <div class="absolute top-4 left-4 text-yellow-400 animate-float">
      <i class="fas fa-star text-lg opacity-80"></i>
    </div>
    <div class="absolute top-6 right-6 text-pink-400 animate-float" style="animation-delay: 0.5s;">
      <i class="fas fa-heart text-lg opacity-80"></i>
    </div>
    <div class="absolute bottom-6 left-6 text-blue-400 animate-float" style="animation-delay: 1s;">
      <i class="fas fa-gem text-sm opacity-80"></i>
    </div>
    <div class="absolute bottom-4 right-4 text-green-400 animate-float" style="animation-delay: 1.5s;">
      <i class="fas fa-trophy text-lg opacity-80"></i>
    </div>
    <div class="absolute top-1/2 left-2 text-purple-400 animate-float" style="animation-delay: 2s;">
      <i class="fas fa-magic text-sm opacity-60"></i>
    </div>
    <div class="absolute top-1/2 right-2 text-orange-400 animate-float" style="animation-delay: 2.5s;">
      <i class="fas fa-crown text-sm opacity-60"></i>
    </div>
    
    <!-- Success Badge -->
    <div class="absolute -top-3 left-1/2 transform -translate-x-1/2 bg-gradient-to-r from-green-500 to-emerald-600 text-white px-6 py-2 rounded-full text-sm font-bold shadow-lg animate-bounce">
      <i class="fas fa-medal mr-2"></i>SUCCESS
    </div>
  </div>
</div>

<script>
// Global variables
let selectedRoom = '';
let selectedTime = '';
let isAdmin = false;
let currentCalendarDate = new Date();
let currentBookingData = null;
let currentBookingStep = 1;

// Initialize
document.addEventListener('DOMContentLoaded', function() {
  // Set today's date as default
  const today = new Date().toISOString().split('T')[0];
  document.getElementById('bookingDateForm').value = today;
  
  // Initialize sample data if not exists
  initializeSampleData();
  
  // Event listeners
  setupEventListeners();
  
  // Initialize displays
  updateTodayBookings();
  generateCalendar();
  updateStatsDisplay();
  updateFooterInfo();
  
  // Setup stats button listeners if admin is already logged in
  if (isAdmin) {
    setTimeout(() => {
      setupStatsButtonListeners();
    }, 200);
  }
  
  // Close mobile menu when clicking outside
  document.addEventListener('click', function(event) {
    const mobileMenu = document.getElementById('mobileMenu');
    const mobileMenuBtn = document.getElementById('mobileMenuBtn');
    
    if (!mobileMenu.classList.contains('hidden') && 
        !mobileMenu.contains(event.target) && 
        !mobileMenuBtn.contains(event.target)) {
      toggleMobileMenu();
    }
  });
  
  // Add date/time change listeners for real-time availability check
  const dateInput = document.getElementById('bookingDateForm');
  if (dateInput) {
    dateInput.addEventListener('change', checkRoomAvailability);
  }
});

function initializeSampleData() {
  // Add sample bookings if none exist
  const existingBookings = JSON.parse(localStorage.getItem('bookings') || '[]');
  if (existingBookings.length === 0) {
    const today = new Date().toISOString().split('T')[0];
    const tomorrow = new Date();
    tomorrow.setDate(tomorrow.getDate() + 1);
    const tomorrowStr = tomorrow.toISOString().split('T')[0];
    
    const sampleBookings = [
      {
        id: Date.now() + 1,
        room: 'ห้อง 500',
        date: today,
        time: '09:00-12:00',
        booker: 'คุณสมชาย ใจดี',
        department: 'บริหาร',
        topic: 'ประชุมบอร์ดรายเดือน',
        attendees: 10,
        equipment: ['โปรเจคเตอร์', 'ไมโครโฟน', 'กาแฟ/น้ำดื่ม']
      },
      {
        id: Date.now() + 2,
        room: 'ห้อง 501',
        date: today,
        time: '13:00-16:00',
        booker: 'คุณสมหญิง รักงาน',
        department: 'IT',
        topic: 'ประชุมทีม IT รายสัปดาห์',
        attendees: 8,
        equipment: ['คอมพิวเตอร์', 'กระดานไวท์บอร์ด']
      }
    ];
    localStorage.setItem('bookings', JSON.stringify(sampleBookings));
  }
  
  // Initialize stats if not exists
  const existingStats = localStorage.getItem('stats');
  if (!existingStats) {
    const defaultStats = {
      todayCount: 2,
      weekCount: 8,
      popularRoom: 'ห้อง 500'
    };
    localStorage.setItem('stats', JSON.stringify(defaultStats));
  }
}

function setupEventListeners() {
  // Room selection
  document.querySelectorAll('.room-card').forEach(card => {
    card.addEventListener('click', function() {
      selectRoom(this);
    });
  });
  
  // Time slot selection
  document.querySelectorAll('.time-slot-btn').forEach(slot => {
    slot.addEventListener('click', function() {
      selectTimeSlot(this);
    });
  });
  
  // Form submission
  document.getElementById('submitForm').addEventListener('submit', submitBooking);
  
  // Step navigation buttons
  setupStepNavigation();
  
  // Real-time form validation
  setupFormValidation();
  
  // Modal controls
  document.getElementById('closeModal').addEventListener('click', closeSuccessModal);
  
  // Admin controls - handled by onclick attributes in HTML
  

  
  // Calendar navigation
  document.getElementById('prevMonth').addEventListener('click', function() {
    currentCalendarDate.setMonth(currentCalendarDate.getMonth() - 1);
    generateCalendar();
  });
  
  document.getElementById('nextMonth').addEventListener('click', function() {
    currentCalendarDate.setMonth(currentCalendarDate.getMonth() + 1);
    generateCalendar();
  });
  
  // Setup admin button listeners
  setupAdminButtonListeners();
  
  // Setup stats button listeners
  setupStatsButtonListeners();
  
  // Admin login form
  const adminLoginForm = document.getElementById('adminLoginForm');
  if (adminLoginForm) {
    adminLoginForm.addEventListener('submit', adminLogin);
  }
  
  // Toggle password visibility
  const togglePassword = document.getElementById('togglePassword');
  if (togglePassword) {
    togglePassword.addEventListener('click', function() {
      const passwordInput = document.getElementById('adminPassword');
      const passwordIcon = document.getElementById('passwordIcon');
      
      if (passwordInput.type === 'password') {
        passwordInput.type = 'text';
        passwordIcon.classList.remove('fa-eye');
        passwordIcon.classList.add('fa-eye-slash');
      } else {
        passwordInput.type = 'password';
        passwordIcon.classList.remove('fa-eye-slash');
        passwordIcon.classList.add('fa-eye');
      }
    });
  }
}

function startBookingProcess() {
  const startBtn = document.getElementById('startBookingBtn');
  
  // Add loading state
  startBtn.innerHTML = '<i class="fas fa-spinner fa-spin mr-2"></i>กำลังเตรียมฟอร์ม...';
  startBtn.disabled = true;
  startBtn.classList.add('opacity-75', 'cursor-not-allowed');
  
  // Simulate loading and show form
  setTimeout(() => {
    showBookingForm();
    
    // Reset button
    startBtn.innerHTML = '<i class="fas fa-plus mr-2"></i>เริ่มจองห้องประชุม';
    startBtn.disabled = false;
    startBtn.classList.remove('opacity-75', 'cursor-not-allowed');
    
    // Show success notification
    showNotification('🎯 เปิดฟอร์มจองห้องประชุมแล้ว กรุณาเลือกห้องและกรอกข้อมูล', 'success', 4000);
    
    // Auto-focus on first room card
    const firstRoom = document.querySelector('.room-card');
    if (firstRoom) {
      firstRoom.scrollIntoView({ behavior: 'smooth', block: 'center' });
      firstRoom.classList.add('animate-pulse');
      setTimeout(() => {
        firstRoom.classList.remove('animate-pulse');
      }, 2000);
    }
  }, 800);
}

function showBookingForm() {
  document.getElementById('welcomeSection').classList.add('hidden');
  document.getElementById('bookingForm').classList.remove('hidden');
  document.getElementById('todayBookingsSection').classList.add('hidden');
  
  // Reset to step 1
  currentBookingStep = 1;
  showStep(1);
  
  // Update active navigation state
  updateActiveNavigation('booking');
  
  // Check room availability in real-time
  checkRoomAvailability();
}

// Step management functions
function setupStepNavigation() {
  // Step 1 navigation
  const nextToStep2 = document.getElementById('nextToStep2');
  if (nextToStep2) {
    nextToStep2.addEventListener('click', () => goToStep(2));
  }
  
  // Step 2 navigation
  const backToStep1 = document.getElementById('backToStep1');
  const nextToStep3 = document.getElementById('nextToStep3');
  if (backToStep1) {
    backToStep1.addEventListener('click', () => goToStep(1));
  }
  if (nextToStep3) {
    nextToStep3.addEventListener('click', () => goToStep(3));
  }
  
  // Step 3 navigation
  const backToStep2 = document.getElementById('backToStep2');
  const nextToStep4 = document.getElementById('nextToStep4');
  if (backToStep2) {
    backToStep2.addEventListener('click', () => goToStep(2));
  }
  if (nextToStep4) {
    nextToStep4.addEventListener('click', () => goToStep(4));
  }
  
  // Step 4 navigation
  const backToStep3 = document.getElementById('backToStep3');
  if (backToStep3) {
    backToStep3.addEventListener('click', () => goToStep(3));
  }
}

function showStep(stepNumber) {
  // Hide all steps
  document.querySelectorAll('.booking-step').forEach(step => {
    step.classList.add('hidden');
  });
  
  // Show current step
  const currentStepElement = document.getElementById(`step${stepNumber}`);
  if (currentStepElement) {
    currentStepElement.classList.remove('hidden');
  }
  
  // Update step indicators
  updateStepIndicators(stepNumber);
  
  // Update progress bar
  updateProgressBar(stepNumber);
  
  // Update current step display
  const currentStepDisplay = document.getElementById('currentStep');
  if (currentStepDisplay) {
    currentStepDisplay.textContent = stepNumber;
  }
  
  currentBookingStep = stepNumber;
}

function updateStepIndicators(activeStep) {
  document.querySelectorAll('.step-indicator').forEach((indicator, index) => {
    const stepNum = index + 1;
    const circle = indicator.querySelector('div');
    const textElements = indicator.querySelectorAll('div:not(:first-child) div');
    
    if (stepNum <= activeStep) {
      // Active or completed step
      circle.classList.remove('bg-gray-300', 'text-gray-600');
      circle.classList.add('bg-blue-500', 'text-white');
      
      textElements.forEach(text => {
        text.classList.remove('text-gray-400');
        text.classList.add('text-blue-600');
      });
      
      if (stepNum === activeStep) {
        indicator.classList.add('active');
      }
    } else {
      // Inactive step
      circle.classList.remove('bg-blue-500', 'text-white');
      circle.classList.add('bg-gray-300', 'text-gray-600');
      
      textElements.forEach(text => {
        text.classList.remove('text-blue-600');
        text.classList.add('text-gray-400');
      });
      
      indicator.classList.remove('active');
    }
  });
}

function updateProgressBar(activeStep) {
  const progressBar = document.getElementById('progressBar');
  if (progressBar) {
    const progress = (activeStep / 4) * 100;
    progressBar.style.width = `${progress}%`;
  }
  
  // Update individual progress segments
  const progressSegments = document.querySelectorAll('.flex-1 .h-full');
  progressSegments.forEach((segment, index) => {
    if (index < activeStep - 1) {
      segment.classList.remove('bg-gray-300');
      segment.classList.add('bg-blue-500');
      segment.style.width = '100%';
    } else {
      segment.classList.remove('bg-blue-500');
      segment.classList.add('bg-gray-300');
      segment.style.width = '0%';
    }
  });
}

function goToStep(stepNumber) {
  // Validate current step before moving
  if (!validateCurrentStep()) {
    return;
  }
  
  // Special handling for step 4 (summary)
  if (stepNumber === 4) {
    updateBookingSummary();
  }
  
  showStep(stepNumber);
  
  // Add smooth scroll to top
  const bookingForm = document.getElementById('bookingForm');
  if (bookingForm) {
    bookingForm.scrollIntoView({ behavior: 'smooth', block: 'start' });
  }
}

function validateCurrentStep() {
  switch (currentBookingStep) {
    case 1:
      if (!selectedRoom) {
        showNotification('❌ กรุณาเลือกห้องประชุมก่อนดำเนินการต่อ', 'error');
        return false;
      }
      break;
      
    case 2:
      const bookingDate = document.getElementById('bookingDateForm').value;
      if (!bookingDate || !selectedTime) {
        showNotification('❌ กรุณาเลือกวันที่และเวลาก่อนดำเนินการต่อ', 'error');
        return false;
      }
      
      // Validate custom time if selected
      if (selectedTime === 'custom') {
        const startTime = document.getElementById('startTimeForm').value;
        const endTime = document.getElementById('endTimeForm').value;
        if (!startTime || !endTime) {
          showNotification('❌ กรุณาระบุเวลาเริ่มและเวลาสิ้นสุด', 'error');
          return false;
        }
        if (startTime >= endTime) {
          showNotification('❌ เวลาเริ่มต้องน้อยกว่าเวลาสิ้นสุด', 'error');
          return false;
        }
      }
      break;
      
    case 3:
      const bookerName = document.getElementById('bookerNameForm').value.trim();
      const department = document.getElementById('departmentForm').value;
      const meetingTopic = document.getElementById('meetingTopicForm').value.trim();
      const attendees = document.getElementById('attendeesForm').value;
      
      if (!bookerName || !department || !meetingTopic || !attendees) {
        showNotification('❌ กรุณากรอกข้อมูลที่จำเป็นให้ครบถ้วน', 'error');
        return false;
      }
      
      const attendeesNum = parseInt(attendees);
      if (attendeesNum < 1 || attendeesNum > 50) {
        showNotification('❌ จำนวนผู้เข้าร่วมต้องอยู่ระหว่าง 1-50 คน', 'error');
        return false;
      }
      break;
  }
  
  return true;
}

function updateBookingSummary() {
  // Get form data
  const bookerName = document.getElementById('bookerNameForm').value.trim();
  const department = document.getElementById('departmentForm').value;
  const meetingTopic = document.getElementById('meetingTopicForm').value.trim();
  const attendees = document.getElementById('attendeesForm').value;
  const bookingDate = document.getElementById('bookingDateForm').value;
  const phone = document.getElementById('phoneForm').value.trim();
  
  // Get time display
  let timeDisplay = selectedTime;
  if (selectedTime === 'custom') {
    const startTime = document.getElementById('startTimeForm').value;
    const endTime = document.getElementById('endTimeForm').value;
    timeDisplay = `${startTime}-${endTime}`;
  }
  
  // Format date
  const formattedDate = new Date(bookingDate).toLocaleDateString('th-TH', {
    year: 'numeric',
    month: 'long',
    day: 'numeric',
    weekday: 'long'
  });
  
  // Update summary fields
  document.getElementById('summaryRoom').textContent = selectedRoom;
  document.getElementById('summaryDate').textContent = formattedDate;
  document.getElementById('summaryTime').textContent = timeDisplay;
  document.getElementById('summaryTopic').textContent = meetingTopic;
  document.getElementById('summaryBooker').textContent = bookerName;
  document.getElementById('summaryDepartment').textContent = department;
  document.getElementById('summaryAttendees').textContent = `${attendees} คน`;
  
  // Handle phone number
  const phoneRow = document.getElementById('summaryPhoneRow');
  const phoneElement = document.getElementById('summaryPhone');
  if (phone) {
    phoneElement.textContent = phone;
    phoneRow.style.display = 'flex';
  } else {
    phoneRow.style.display = 'none';
  }
  
  // Handle equipment
  const equipment = [];
  document.querySelectorAll('.equipment-checkbox-form:checked').forEach(checkbox => {
    equipment.push(checkbox.value);
  });
  
  const equipmentSection = document.getElementById('summaryEquipmentSection');
  const equipmentContainer = document.getElementById('summaryEquipment');
  
  if (equipment.length > 0) {
    equipmentContainer.innerHTML = equipment.map(eq => `
      <span class="bg-blue-100 text-blue-800 px-3 py-1 rounded-full text-sm font-medium">
        ${eq}
      </span>
    `).join('');
    equipmentSection.style.display = 'block';
  } else {
    equipmentSection.style.display = 'none';
  }
}

function checkRoomAvailability() {
  const bookings = JSON.parse(localStorage.getItem('bookings') || '[]');
  const selectedDate = document.getElementById('bookingDateForm').value;
  const selectedTimeSlot = selectedTime;
  
  if (!selectedDate || !selectedTimeSlot) return;
  
  // Check each room's availability
  document.querySelectorAll('.room-card').forEach(card => {
    const roomName = card.dataset.room;
    const isBooked = bookings.some(booking => 
      booking.room === roomName && 
      booking.date === selectedDate && 
      booking.time === selectedTimeSlot
    );
    
    // Update room card appearance
    const statusIndicator = card.querySelector('.room-status') || document.createElement('div');
    statusIndicator.className = 'room-status absolute -top-2 -right-2 w-6 h-6 rounded-full flex items-center justify-center text-xs font-bold shadow-lg';
    
    if (isBooked) {
      statusIndicator.className += ' bg-red-500 text-white animate-pulse';
      statusIndicator.innerHTML = '<i class="fas fa-times"></i>';
      statusIndicator.title = 'ห้องไม่ว่าง';
      card.classList.add('opacity-50', 'cursor-not-allowed');
      card.classList.remove('hover:border-blue-300');
    } else {
      statusIndicator.className += ' bg-green-500 text-white';
      statusIndicator.innerHTML = '<i class="fas fa-check"></i>';
      statusIndicator.title = 'ห้องว่าง';
      card.classList.remove('opacity-50', 'cursor-not-allowed');
      card.classList.add('hover:border-blue-300');
    }
    
    if (!card.querySelector('.room-status')) {
      card.style.position = 'relative';
      card.appendChild(statusIndicator);
    }
  });
}

function selectRoom(roomCard) {
  const roomName = roomCard.dataset.room;
  
  // Check if room is available
  if (roomCard.classList.contains('cursor-not-allowed')) {
    showNotification(`❌ ${roomName} ไม่ว่างในเวลาที่เลือก กรุณาเลือกห้องอื่นหรือเวลาอื่น`, 'error', 4000);
    
    // Shake animation for unavailable room
    roomCard.style.animation = 'shake 0.5s ease-in-out';
    setTimeout(() => {
      roomCard.style.animation = '';
    }, 500);
    return;
  }
  
  // Remove previous selection
  document.querySelectorAll('.room-card').forEach(card => {
    card.classList.remove('ring-2', 'ring-blue-500', 'bg-blue-100', 'transform', 'scale-105', 'shadow-xl');
  });
  
  // Add selection to clicked room with enhanced effects
  roomCard.classList.add('ring-2', 'ring-blue-500', 'bg-blue-100', 'transform', 'scale-105', 'shadow-xl');
  selectedRoom = roomName;
  
  // Enable next button for step 1
  const nextBtn = document.getElementById('nextToStep2');
  if (nextBtn) {
    nextBtn.disabled = false;
    nextBtn.classList.remove('opacity-50', 'cursor-not-allowed');
  }
  
  // Success feedback
  showNotification(`✅ เลือก ${roomName} แล้ว คลิก "ถัดไป" เพื่อเลือกเวลา`, 'success', 3000);
}

function selectTimeSlot(timeSlot) {
  const timeValue = timeSlot.dataset.time;
  
  // Remove previous selection
  document.querySelectorAll('.time-slot-btn').forEach(btn => {
    btn.classList.remove('bg-blue-500', 'text-white', 'border-blue-500', 'transform', 'scale-105', 'shadow-lg');
    btn.classList.add('border-gray-300', 'hover:bg-blue-50', 'hover:border-blue-300');
  });
  
  // Add selection to clicked slot
  timeSlot.classList.remove('border-gray-300', 'hover:bg-blue-50', 'hover:border-blue-300');
  timeSlot.classList.add('bg-blue-500', 'text-white', 'border-blue-500', 'transform', 'scale-105', 'shadow-lg');
  
  selectedTime = timeValue;
  
  // Show/hide custom time section
  const customTimeSection = document.getElementById('customTimeForm');
  if (selectedTime === 'custom') {
    customTimeSection.classList.remove('hidden');
    // Disable next button until custom time is set
    const nextBtn = document.getElementById('nextToStep3');
    if (nextBtn) {
      nextBtn.disabled = true;
      nextBtn.classList.add('opacity-50', 'cursor-not-allowed');
    }
  } else {
    customTimeSection.classList.add('hidden');
    
    // Enable next button for step 2
    const nextBtn = document.getElementById('nextToStep3');
    if (nextBtn) {
      nextBtn.disabled = false;
      nextBtn.classList.remove('opacity-50', 'cursor-not-allowed');
    }
    
    // Check room availability when time is selected
    checkRoomAvailability();
    
    // Success feedback
    const timeDisplay = timeValue === '09:00-12:00' ? 'ช่วงเช้า (09:00-12:00)' :
                       timeValue === '13:00-16:00' ? 'ช่วงบ่าย (13:00-16:00)' :
                       timeValue === '09:00-16:00' ? 'เต็มวัน (09:00-16:00)' : timeValue;
    
    showNotification(`⏰ เลือกเวลา ${timeDisplay} แล้ว คลิก "ถัดไป" เพื่อกรอกข้อมูล`, 'success', 3000);
  }
}

function submitBooking(event) {
  event.preventDefault();
  
  // Get form data
  const bookerName = document.getElementById('bookerNameForm').value.trim();
  const department = document.getElementById('departmentForm').value;
  const meetingTopic = document.getElementById('meetingTopicForm').value.trim();
  const attendees = document.getElementById('attendeesForm').value;
  const bookingDate = document.getElementById('bookingDateForm').value;
  const phone = document.getElementById('phoneForm').value.trim();
  
  // Validate form
  if (!selectedRoom || !selectedTime || !bookerName || !department || !meetingTopic || !attendees || !bookingDate) {
    showNotification('❌ กรุณากรอกข้อมูลให้ครบถ้วน', 'error');
    return;
  }
  
  // Get time details
  let timeDisplay = selectedTime;
  if (selectedTime === 'custom') {
    const startTime = document.getElementById('startTimeForm').value;
    const endTime = document.getElementById('endTimeForm').value;
    if (!startTime || !endTime) {
      showNotification('❌ กรุณาระบุเวลาเริ่มและเวลาสิ้นสุด', 'error');
      return;
    }
    
    // Validate time range
    if (startTime >= endTime) {
      showNotification('❌ เวลาเริ่มต้องน้อยกว่าเวลาสิ้นสุด', 'error');
      return;
    }
    
    timeDisplay = `${startTime}-${endTime}`;
  }
  
  // Check for duplicate booking with enhanced validation
  const existingBookings = JSON.parse(localStorage.getItem('bookings') || '[]');
  
  // Check for exact match
  const exactDuplicate = existingBookings.find(booking => 
    booking.room === selectedRoom && 
    booking.date === bookingDate && 
    booking.time === timeDisplay
  );
  
  // Check for overlapping time slots
  const overlappingBookings = existingBookings.filter(booking => 
    booking.room === selectedRoom && 
    booking.date === bookingDate &&
    checkTimeOverlap(booking.time, timeDisplay)
  );
  
  if (exactDuplicate) {
    const formattedDate = new Date(bookingDate).toLocaleDateString('th-TH', {
      year: 'numeric',
      month: 'long',
      day: 'numeric',
      weekday: 'long'
    });
    
    // Show detailed conflict notification for exact duplicate
    showDuplicateBookingAlert(exactDuplicate, formattedDate, 'exact');
    
    // Highlight conflicting fields
    highlightConflictFields();
    
    // Play alert sound (if supported)
    playAlertSound();
    
    return;
  }
  
  if (overlappingBookings.length > 0) {
    const formattedDate = new Date(bookingDate).toLocaleDateString('th-TH', {
      year: 'numeric',
      month: 'long',
      day: 'numeric',
      weekday: 'long'
    });
    
    // Show overlapping time alert
    showDuplicateBookingAlert(overlappingBookings[0], formattedDate, 'overlap');
    
    // Highlight conflicting fields
    highlightConflictFields();
    
    // Play alert sound (if supported)
    playAlertSound();
    
    return;
  }
  
  // Validate attendees
  const attendeesNum = parseInt(attendees);
  if (attendeesNum < 1 || attendeesNum > 50) {
    showNotification('❌ จำนวนผู้เข้าร่วมต้องอยู่ระหว่าง 1-50 คน', 'error');
    return;
  }
  
  // Get selected equipment
  const equipment = [];
  document.querySelectorAll('.equipment-checkbox-form:checked').forEach(checkbox => {
    equipment.push(checkbox.value);
  });
  
  // Create booking object
  const booking = {
    room: selectedRoom,
    date: bookingDate,
    time: timeDisplay,
    booker: bookerName,
    department: department,
    topic: meetingTopic,
    attendees: attendeesNum,
    phone: phone,
    equipment: equipment,
    id: Date.now(),
    createdAt: new Date().toISOString(),
    status: 'confirmed'
  };
  
  // Save booking
  saveBooking(booking);
  
  // Play success sound
  playSuccessSound();
  
  // Show success modal
  showSuccessModal(booking);
  
  // Reset form
  resetForm();
}

function saveBooking(booking) {
  let bookings = JSON.parse(localStorage.getItem('bookings') || '[]');
  bookings.push(booking);
  localStorage.setItem('bookings', JSON.stringify(bookings));
  
  // Update displays
  updateTodayBookings();
  generateCalendar();
  updateStatsDisplay();
}

function showSuccessModal(booking) {
  const modal = document.getElementById('successModal');
  const detailsDiv = document.getElementById('bookingDetails');
  
  currentBookingData = booking;
  
  // Enhanced booking details with beautiful styling
  const formattedDate = new Date(booking.date).toLocaleDateString('th-TH', {
    year: 'numeric',
    month: 'long',
    day: 'numeric',
    weekday: 'long'
  });
  
  detailsDiv.innerHTML = `
    <div class="space-y-4">
      <div class="text-center mb-4">
        <h4 class="text-lg font-bold text-gray-800 mb-2">
          <i class="fas fa-clipboard-check mr-2 text-green-600"></i>รายละเอียดการจอง
        </h4>
        <div class="w-16 h-1 bg-gradient-to-r from-green-400 to-blue-400 rounded-full mx-auto"></div>
      </div>
      
      <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
        <div class="bg-gradient-to-r from-blue-50 to-blue-100 p-4 rounded-xl border-l-4 border-blue-500">
          <div class="flex items-center">
            <i class="fas fa-door-open text-blue-600 mr-3 text-xl"></i>
            <div>
              <div class="text-sm text-gray-600">ห้องประชุม</div>
              <div class="font-bold text-blue-800 text-lg">${booking.room}</div>
            </div>
          </div>
        </div>
        
        <div class="bg-gradient-to-r from-green-50 to-green-100 p-4 rounded-xl border-l-4 border-green-500">
          <div class="flex items-center">
            <i class="fas fa-calendar text-green-600 mr-3 text-xl"></i>
            <div>
              <div class="text-sm text-gray-600">วันที่</div>
              <div class="font-bold text-green-800">${formattedDate}</div>
            </div>
          </div>
        </div>
        
        <div class="bg-gradient-to-r from-orange-50 to-orange-100 p-4 rounded-xl border-l-4 border-orange-500">
          <div class="flex items-center">
            <i class="fas fa-clock text-orange-600 mr-3 text-xl"></i>
            <div>
              <div class="text-sm text-gray-600">เวลา</div>
              <div class="font-bold text-orange-800 text-lg">${booking.time}</div>
            </div>
          </div>
        </div>
        
        <div class="bg-gradient-to-r from-purple-50 to-purple-100 p-4 rounded-xl border-l-4 border-purple-500">
          <div class="flex items-center">
            <i class="fas fa-users text-purple-600 mr-3 text-xl"></i>
            <div>
              <div class="text-sm text-gray-600">จำนวนผู้เข้าร่วม</div>
              <div class="font-bold text-purple-800 text-lg">${booking.attendees} คน</div>
            </div>
          </div>
        </div>
      </div>
      
      <div class="bg-gradient-to-r from-indigo-50 to-indigo-100 p-4 rounded-xl border-l-4 border-indigo-500">
        <div class="flex items-start">
          <i class="fas fa-clipboard-list text-indigo-600 mr-3 text-xl mt-1"></i>
          <div class="flex-1">
            <div class="text-sm text-gray-600">หัวข้อการประชุม</div>
            <div class="font-bold text-indigo-800 text-lg">${booking.topic}</div>
          </div>
        </div>
      </div>
      
      <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
        <div class="bg-gradient-to-r from-teal-50 to-teal-100 p-4 rounded-xl border-l-4 border-teal-500">
          <div class="flex items-center">
            <i class="fas fa-user text-teal-600 mr-3 text-xl"></i>
            <div>
              <div class="text-sm text-gray-600">ผู้จอง</div>
              <div class="font-bold text-teal-800">${booking.booker}</div>
            </div>
          </div>
        </div>
        
        <div class="bg-gradient-to-r from-pink-50 to-pink-100 p-4 rounded-xl border-l-4 border-pink-500">
          <div class="flex items-center">
            <i class="fas fa-building text-pink-600 mr-3 text-xl"></i>
            <div>
              <div class="text-sm text-gray-600">แผนก</div>
              <div class="font-bold text-pink-800">${booking.department}</div>
            </div>
          </div>
        </div>
      </div>
      
      ${booking.phone ? `
        <div class="bg-gradient-to-r from-cyan-50 to-cyan-100 p-4 rounded-xl border-l-4 border-cyan-500">
          <div class="flex items-center">
            <i class="fas fa-phone text-cyan-600 mr-3 text-xl"></i>
            <div>
              <div class="text-sm text-gray-600">เบอร์โทรศัพท์</div>
              <div class="font-bold text-cyan-800">${booking.phone}</div>
            </div>
          </div>
        </div>
      ` : ''}
      
      ${booking.equipment && booking.equipment.length > 0 ? `
        <div class="bg-gradient-to-r from-yellow-50 to-yellow-100 p-4 rounded-xl border-l-4 border-yellow-500">
          <div class="flex items-start">
            <i class="fas fa-tools text-yellow-600 mr-3 text-xl mt-1"></i>
            <div class="flex-1">
              <div class="text-sm text-gray-600 mb-2">อุปกรณ์ที่ต้องการ</div>
              <div class="flex flex-wrap gap-2">
                ${booking.equipment.map(eq => `
                  <span class="bg-white bg-opacity-80 text-yellow-800 px-3 py-1 rounded-full text-sm font-medium shadow-sm border border-yellow-200">
                    <i class="fas fa-check-circle mr-1 text-green-500"></i>${eq}
                  </span>
                `).join('')}
              </div>
            </div>
          </div>
        </div>
      ` : ''}
    </div>
  `;
  
  // Generate confetti
  generateConfetti();
  
  // Start count-up animations
  setTimeout(() => {
    startCountUpAnimations();
  }, 1000);
  
  // Add print booking functionality
  const printBtn = document.getElementById('printBooking');
  if (printBtn) {
    printBtn.onclick = () => printBookingDetails(booking.id);
  }
  
  modal.classList.remove('hidden');
}

function closeSuccessModal() {
  document.getElementById('successModal').classList.add('hidden');
}

function resetForm() {
  // Reset form fields
  const form = document.getElementById('submitForm');
  if (form) {
    form.reset();
  }
  
  // Reset individual form fields
  document.getElementById('bookerNameForm').value = '';
  document.getElementById('departmentForm').value = '';
  document.getElementById('meetingTopicForm').value = '';
  document.getElementById('attendeesForm').value = '';
  document.getElementById('phoneForm').value = '';
  
  // Reset selections
  document.querySelectorAll('.room-card').forEach(card => {
    card.classList.remove('ring-2', 'ring-blue-500', 'bg-blue-100', 'transform', 'scale-105', 'shadow-xl');
  });
  document.querySelectorAll('.time-slot-btn').forEach(btn => {
    btn.classList.remove('bg-blue-500', 'text-white', 'border-blue-500', 'transform', 'scale-105', 'shadow-lg');
    btn.classList.add('border-gray-300', 'hover:bg-blue-50', 'hover:border-blue-300');
  });
  
  // Reset equipment checkboxes
  document.querySelectorAll('.equipment-checkbox-form').forEach(checkbox => {
    checkbox.checked = false;
  });
  
  selectedRoom = '';
  selectedTime = '';
  
  // Hide custom time section
  document.getElementById('customTimeForm').classList.add('hidden');
  
  // Set today's date again
  const today = new Date().toISOString().split('T')[0];
  document.getElementById('bookingDateForm').value = today;
  
  // Reset step to 1
  currentBookingStep = 1;
  showStep(1);
  
  // Reset button states
  document.getElementById('nextToStep2').disabled = true;
  document.getElementById('nextToStep2').classList.add('opacity-50', 'cursor-not-allowed');
  
  document.getElementById('nextToStep3').disabled = true;
  document.getElementById('nextToStep3').classList.add('opacity-50', 'cursor-not-allowed');
}

function cancelBooking() {
  // Show confirmation dialog
  const confirmModal = document.createElement('div');
  confirmModal.className = 'fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-50';
  confirmModal.innerHTML = `
    <div class="bg-white rounded-2xl p-8 max-w-md mx-4 text-center animate-slideIn">
      <div class="text-orange-500 text-6xl mb-4">
        <i class="fas fa-exclamation-triangle"></i>
      </div>
      <h3 class="text-2xl font-bold text-orange-600 mb-4">⚠️ ยกเลิกการจอง</h3>
      
      <div class="bg-orange-50 border-2 border-orange-200 rounded-lg p-4 mb-6">
        <p class="text-orange-800">
          <i class="fas fa-info-circle mr-2"></i>
          คุณต้องการยกเลิกการจองห้องประชุมหรือไม่?<br>
          <span class="text-sm">ข้อมูลที่กรอกจะหายไป</span>
        </p>
      </div>
      
      <div class="flex space-x-3 justify-center">
        <button onclick="confirmCancelBooking(); this.closest('.fixed').remove();" class="bg-red-500 text-white px-6 py-3 rounded-lg hover:bg-red-600 transition-colors font-semibold">
          <i class="fas fa-times mr-2"></i>ยืนยันยกเลิก
        </button>
        <button onclick="this.closest('.fixed').remove();" class="bg-gray-600 text-white px-6 py-3 rounded-lg hover:bg-gray-700 transition-colors font-semibold">
          <i class="fas fa-arrow-left mr-2"></i>กลับไปจอง
        </button>
      </div>
    </div>
  `;
  
  document.body.appendChild(confirmModal);
}

function confirmCancelBooking() {
  resetForm();
  document.getElementById('bookingForm').classList.add('hidden');
  document.getElementById('welcomeSection').classList.remove('hidden');
  
  // Reset step to 1
  currentBookingStep = 1;
  
  // Update active navigation state
  updateActiveNavigation('home');
  
  showNotification('❌ ยกเลิกการจองแล้ว', 'info', 2000);
}

// Navigation functions
function showWelcomeSection() {
  // Hide all sections
  document.getElementById('welcomeSection').classList.remove('hidden');
  document.getElementById('bookingForm').classList.add('hidden');
  document.getElementById('todayBookingsSection').classList.add('hidden');
  
  // Update active navigation state
  updateActiveNavigation('home');
}

function toggleMobileMenu() {
  const mobileMenu = document.getElementById('mobileMenu');
  const mobileMenuBtn = document.getElementById('mobileMenuBtn');
  const icon = mobileMenuBtn.querySelector('i');
  
  if (mobileMenu.classList.contains('hidden')) {
    mobileMenu.classList.remove('hidden');
    icon.classList.remove('fa-bars');
    icon.classList.add('fa-times');
  } else {
    mobileMenu.classList.add('hidden');
    icon.classList.remove('fa-times');
    icon.classList.add('fa-bars');
  }
}

function updateActiveNavigation(activeSection) {
  // Remove active state from all navigation buttons
  const navButtons = document.querySelectorAll('nav button');
  navButtons.forEach(btn => {
    btn.classList.remove('bg-white', 'bg-opacity-20', 'text-yellow-300');
  });
  
  // Add active state to current section
  let activeButton = null;
  switch(activeSection) {
    case 'home':
      activeButton = document.querySelector('button[onclick*="showWelcomeSection"]');
      break;
    case 'booking':
      activeButton = document.querySelector('button[onclick*="showBookingForm"]');
      break;
    case 'today':
      activeButton = document.querySelector('button[onclick*="showTodayBookingsSection"]');
      break;
  }
  
  if (activeButton) {
    activeButton.classList.add('bg-white', 'bg-opacity-20', 'text-yellow-300');
  }
}

function updateTodayBookings() {
  const bookings = JSON.parse(localStorage.getItem('bookings') || '[]');
  const today = new Date().toISOString().split('T')[0];
  const todayBookings = bookings.filter(booking => booking.date === today);
  
  const container = document.getElementById('todayBookings');
  
  if (todayBookings.length === 0) {
    container.innerHTML = `
      <div class="text-center py-6">
        <div class="text-gray-400 text-4xl mb-3">
          <i class="fas fa-calendar-times"></i>
        </div>
        <p class="text-gray-500 text-sm">ไม่มีการจองวันนี้</p>
        <button onclick="showBookingForm()" class="mt-3 text-xs bg-blue-500 text-white px-3 py-2 rounded-lg hover:bg-blue-600 transition-colors">
          <i class="fas fa-plus mr-1"></i>จองเลย
        </button>
      </div>
    `;
    return;
  }
  
  // Room color mapping
  const roomColors = {
    'ห้อง 1A': { bg: 'from-red-50 to-red-100', border: 'border-red-400', text: 'text-red-700', icon: 'text-red-600' },
    'ห้อง 1B': { bg: 'from-orange-50 to-orange-100', border: 'border-orange-400', text: 'text-orange-700', icon: 'text-orange-600' },
    'ห้อง 500': { bg: 'from-blue-50 to-blue-100', border: 'border-blue-400', text: 'text-blue-700', icon: 'text-blue-600' },
    'ห้อง 501': { bg: 'from-green-50 to-green-100', border: 'border-green-400', text: 'text-green-700', icon: 'text-green-600' },
    'ห้อง 502': { bg: 'from-purple-50 to-purple-100', border: 'border-purple-400', text: 'text-purple-700', icon: 'text-purple-600' }
  };
  
  container.innerHTML = todayBookings.map((booking, index) => {
    const colors = roomColors[booking.room] || { bg: 'from-gray-50 to-gray-100', border: 'border-gray-400', text: 'text-gray-700', icon: 'text-gray-600' };
    
    return `
      <div class="booking-item bg-gradient-to-r ${colors.bg} p-4 rounded-xl border-2 ${colors.border} shadow-sm hover:shadow-md transition-all duration-300 transform hover:scale-105 animate-slideIn" style="animation-delay: ${index * 0.1}s">
        <div class="flex justify-between items-start">
          <div class="flex-1">
            <div class="flex items-center mb-2">
              <div class="w-3 h-3 rounded-full bg-green-500 mr-2 animate-pulse"></div>
              <h4 class="font-bold ${colors.text} text-sm">${booking.topic}</h4>
            </div>
            
            <div class="space-y-1 mb-3">
              <div class="flex items-center text-xs">
                <i class="fas fa-door-open ${colors.icon} mr-2 w-3"></i>
                <span class="font-semibold ${colors.text}">${booking.room}</span>
              </div>
              <div class="flex items-center text-xs">
                <i class="fas fa-clock ${colors.icon} mr-2 w-3"></i>
                <span class="font-bold text-gray-800">${booking.time}</span>
              </div>
              <div class="flex items-center text-xs">
                <i class="fas fa-user ${colors.icon} mr-2 w-3"></i>
                <span class="text-gray-700">${booking.booker}</span>
              </div>
              <div class="flex items-center text-xs">
                <i class="fas fa-building ${colors.icon} mr-2 w-3"></i>
                <span class="text-gray-600">${booking.department}</span>
              </div>
              ${booking.attendees ? `
                <div class="flex items-center text-xs">
                  <i class="fas fa-users ${colors.icon} mr-2 w-3"></i>
                  <span class="text-gray-600">${booking.attendees} คน</span>
                </div>
              ` : ''}
            </div>
            
            ${booking.equipment && booking.equipment.length > 0 ? `
              <div class="flex flex-wrap gap-1 mb-2">
                ${booking.equipment.slice(0, 2).map(eq => `
                  <span class="bg-white bg-opacity-70 text-xs px-2 py-1 rounded-full ${colors.text} font-medium shadow-sm">
                    ${eq}
                  </span>
                `).join('')}
                ${booking.equipment.length > 2 ? `
                  <span class="text-xs ${colors.text} opacity-75">+${booking.equipment.length - 2}</span>
                ` : ''}
              </div>
            ` : ''}
            
            <div class="flex items-center justify-between">
              <div class="flex items-center">
                <span class="bg-green-500 text-white px-2 py-1 rounded-full text-xs font-bold shadow-sm">
                  <i class="fas fa-check-circle mr-1"></i>ยืนยัน
                </span>
              </div>
              
              <div class="admin-controls ${isAdmin ? '' : 'hidden'} flex space-x-1">
                <button onclick="editBooking(${booking.id})" class="text-xs bg-blue-500 text-white px-2 py-1 rounded hover:bg-blue-600 transition-colors shadow-sm">
                  <i class="fas fa-edit"></i>
                </button>
                <button onclick="deleteAdminBooking(${booking.id})" class="text-xs bg-red-500 text-white px-2 py-1 rounded hover:bg-red-600 transition-colors shadow-sm">
                  <i class="fas fa-trash"></i>
                </button>
              </div>
            </div>
          </div>
        </div>
      </div>
    `;
  }).join('');
}

function generateCalendar() {
  const year = currentCalendarDate.getFullYear();
  const month = currentCalendarDate.getMonth();
  
  // Update month display
  const monthNames = [
    'มกราคม', 'กุมภาพันธ์', 'มีนาคม', 'เมษายน', 'พฤษภาคม', 'มิถุนายน',
    'กรกฎาคม', 'สิงหาคม', 'กันยายน', 'ตุลาคม', 'พฤศจิกายน', 'ธันวาคม'
  ];
  document.getElementById('currentMonth').textContent = `${monthNames[month]} ${year + 543}`;
  
  // Get first day of month and number of days
  const firstDay = new Date(year, month, 1);
  const lastDay = new Date(year, month + 1, 0);
  const daysInMonth = lastDay.getDate();
  const startingDayOfWeek = firstDay.getDay();
  
  // Get today's date
  const today = new Date();
  const todayStr = today.toISOString().split('T')[0];
  
  // Get bookings for this month
  const allBookings = JSON.parse(localStorage.getItem('bookings') || '[]');
  const monthBookings = allBookings.filter(booking => {
    const bookingDate = new Date(booking.date);
    return bookingDate.getFullYear() === year && bookingDate.getMonth() === month;
  });
  
  // Create calendar grid
  const calendarGrid = document.getElementById('calendarGrid');
  calendarGrid.innerHTML = '';
  
  // Add empty cells for days before the first day of the month
  for (let i = 0; i < startingDayOfWeek; i++) {
    const emptyCell = document.createElement('div');
    emptyCell.className = 'h-8';
    calendarGrid.appendChild(emptyCell);
  }
  
  // Add days of the month
  for (let day = 1; day <= daysInMonth; day++) {
    const dayCell = document.createElement('div');
    const dateStr = `${year}-${String(month + 1).padStart(2, '0')}-${String(day).padStart(2, '0')}`;
    
    dayCell.className = 'calendar-day min-h-20 p-2 flex flex-col cursor-pointer rounded-lg transition-all duration-300 hover:bg-gray-100 border border-gray-200 hover:shadow-md';
    
    // Get bookings for this specific date
    const dayBookings = monthBookings.filter(booking => booking.date === dateStr);
    const hasBookings = dayBookings.length > 0;
    const isToday = dateStr === todayStr;
    
    // Add special styling
    if (isToday && hasBookings) {
      dayCell.className += ' bg-gradient-to-br from-green-400 to-green-500 text-white font-bold hover:from-green-500 hover:to-green-600 border-green-600 shadow-lg';
    } else if (isToday) {
      dayCell.className += ' bg-gradient-to-br from-green-500 to-green-600 text-white font-bold hover:from-green-600 hover:to-green-700 border-green-600 shadow-lg';
    } else if (hasBookings) {
      dayCell.className += ' bg-gradient-to-br from-blue-50 to-blue-100 hover:from-blue-100 hover:to-blue-200 border-blue-300 shadow-sm';
    }
    
    // Add day number
    const dayNumber = document.createElement('div');
    dayNumber.className = isToday ? 'text-sm font-bold mb-2 text-center' : 'text-sm font-semibold mb-2 text-center text-gray-700';
    dayNumber.textContent = day;
    dayCell.appendChild(dayNumber);
    
    // Add booking information with better styling
    if (hasBookings) {
      // Room color mapping
      const roomColors = {
        'ห้อง 1A': 'bg-red-500',
        'ห้อง 1B': 'bg-orange-500', 
        'ห้อง 500': 'bg-blue-500',
        'ห้อง 501': 'bg-green-500',
        'ห้อง 502': 'bg-purple-500'
      };
      
      dayBookings.slice(0, 3).forEach((booking, index) => {
        const bookingDiv = document.createElement('div');
        const roomColor = roomColors[booking.room] || 'bg-gray-500';
        bookingDiv.className = `text-xs ${roomColor} text-white px-2 py-1 rounded-full mb-1 truncate font-medium shadow-sm animate-pulse`;
        bookingDiv.style.animationDelay = `${index * 0.2}s`;
        bookingDiv.style.animationDuration = '2s';
        bookingDiv.style.animationIterationCount = '3';
        
        const roomShort = booking.room.replace('ห้อง ', '');
        const timeShort = booking.time.split('-')[0];
        bookingDiv.textContent = `${roomShort} ${timeShort}`;
        bookingDiv.title = `📋 ${booking.topic}\n🏢 ${booking.room}\n⏰ ${booking.time}\n👤 ${booking.booker} (${booking.department})`;
        
        dayCell.appendChild(bookingDiv);
        
        // Remove animation after it completes
        setTimeout(() => {
          bookingDiv.classList.remove('animate-pulse');
        }, 6000 + (index * 200));
      });
      
      if (dayBookings.length > 3) {
        const moreDiv = document.createElement('div');
        moreDiv.className = 'text-xs text-blue-700 font-bold text-center bg-blue-100 rounded-full px-2 py-1 animate-bounce';
        moreDiv.textContent = `+${dayBookings.length - 3}`;
        moreDiv.title = `มีการจองทั้งหมด ${dayBookings.length} รายการในวันนี้`;
        dayCell.appendChild(moreDiv);
        
        // Remove bounce animation after 3 seconds
        setTimeout(() => {
          moreDiv.classList.remove('animate-bounce');
        }, 3000);
      }
      
      // Add booking count badge
      const countBadge = document.createElement('div');
      countBadge.className = 'absolute -top-1 -right-1 bg-red-500 text-white text-xs rounded-full w-5 h-5 flex items-center justify-center font-bold shadow-lg animate-pulse';
      countBadge.textContent = dayBookings.length;
      countBadge.title = `${dayBookings.length} การจองในวันนี้`;
      dayCell.style.position = 'relative';
      dayCell.appendChild(countBadge);
      
      // Remove pulse animation after 4 seconds
      setTimeout(() => {
        countBadge.classList.remove('animate-pulse');
      }, 4000);
    }
    
    // Add click handler to show day details
    dayCell.addEventListener('click', () => showDayBookings(dateStr, dayBookings));
    
    calendarGrid.appendChild(dayCell);
  }
}

function updateStatsDisplay() {
  const stats = JSON.parse(localStorage.getItem('stats') || '{"todayCount": 2, "weekCount": 8, "popularRoom": "ห้อง 500"}');
  
  document.getElementById('todayCount').textContent = stats.todayCount;
  document.getElementById('weekCount').textContent = stats.weekCount;
  document.getElementById('popularRoom').textContent = stats.popularRoom;
}

// Admin functions
function showAdminModal() {
  document.getElementById('adminModal').classList.remove('hidden');
}

function closeAdminModal() {
  document.getElementById('adminModal').classList.add('hidden');
  
  // Clear password field and error messages
  const passwordInput = document.getElementById('adminPassword');
  const passwordError = document.getElementById('passwordError');
  
  if (passwordInput) {
    passwordInput.value = '';
    passwordInput.classList.remove('border-red-500', 'bg-red-50');
    passwordInput.style.animation = '';
  }
  
  if (passwordError) {
    passwordError.classList.add('hidden');
  }
  
  // Reset password visibility to hidden
  const passwordIcon = document.getElementById('passwordIcon');
  if (passwordInput && passwordIcon) {
    passwordInput.type = 'password';
    passwordIcon.classList.remove('fa-eye-slash');
    passwordIcon.classList.add('fa-eye');
  }
}

function adminLogin(event) {
  if (event) {
    event.preventDefault();
  }
  
  const passwordInput = document.getElementById('adminPassword');
  const passwordError = document.getElementById('passwordError');
  const enteredPassword = passwordInput.value.trim();
  const correctPassword = '123456';
  
  // Hide previous error
  passwordError.classList.add('hidden');
  
  // Validate password
  if (!enteredPassword) {
    passwordError.textContent = 'กรุณากรอกรหัสผ่าน';
    passwordError.classList.remove('hidden');
    passwordInput.focus();
    return;
  }
  
  if (enteredPassword !== correctPassword) {
    passwordError.innerHTML = '<i class="fas fa-exclamation-triangle mr-1"></i>รหัสผ่านไม่ถูกต้อง กรุณาลองใหม่อีกครั้ง';
    passwordError.classList.remove('hidden');
    
    // Add shake animation to password field
    passwordInput.classList.add('border-red-500', 'bg-red-50');
    passwordInput.style.animation = 'shake 0.5s ease-in-out';
    
    // Clear password field
    passwordInput.value = '';
    passwordInput.focus();
    
    // Remove error styling after animation
    setTimeout(() => {
      passwordInput.style.animation = '';
      passwordInput.classList.remove('border-red-500', 'bg-red-50');
    }, 500);
    
    showNotification('❌ รหัสผ่านไม่ถูกต้อง กรุณาลองใหม่อีกครั้ง', 'error', 3000);
    return;
  }
  
  // Successful login
  isAdmin = true;
  document.getElementById('adminBtn').classList.add('hidden');
  document.getElementById('adminStatus').classList.remove('hidden');
  
  // Clear password field
  passwordInput.value = '';
  
  closeAdminModal();
  
  // Show admin controls
  document.querySelectorAll('.admin-controls').forEach(control => {
    control.classList.remove('hidden');
  });
  
  // Show admin controls first
  document.querySelectorAll('.admin-controls').forEach(control => {
    control.classList.remove('hidden');
  });
  
  // Setup stats button listeners after showing admin controls
  setTimeout(() => {
    setupStatsButtonListeners();
  }, 100);
  
  updateTodayBookings();
  showNotification('🔐 เข้าสู่ระบบผู้ดูแลสำเร็จ! คุณสามารถเพิ่ม/ลบ/แก้ไขข้อมูลได้แล้ว', 'success', 4000);
}

function adminLogout() {
  isAdmin = false;
  document.getElementById('adminBtn').classList.remove('hidden');
  document.getElementById('adminStatus').classList.add('hidden');
  document.querySelectorAll('.admin-controls').forEach(control => {
    control.classList.add('hidden');
  });
  updateTodayBookings();
}

// Show admin menu
function showAdminMenu() {
  updateAdminStats();
  document.getElementById('adminMenuModal').classList.remove('hidden');
}

function closeAdminMenu() {
  document.getElementById('adminMenuModal').classList.add('hidden');
}

function updateAdminStats() {
  const bookings = JSON.parse(localStorage.getItem('bookings') || '[]');
  const today = new Date().toISOString().split('T')[0];
  const thisWeekStart = new Date();
  thisWeekStart.setDate(thisWeekStart.getDate() - thisWeekStart.getDay());
  const thisWeekStartStr = thisWeekStart.toISOString().split('T')[0];
  
  const todayBookings = bookings.filter(b => b.date === today).length;
  const thisWeekBookings = bookings.filter(b => b.date >= thisWeekStartStr).length;
  
  document.getElementById('adminTotalBookings').textContent = bookings.length;
  document.getElementById('adminTodayBookings').textContent = todayBookings;
  document.getElementById('adminThisWeekBookings').textContent = thisWeekBookings;
}

// Admin add booking functions
function showAdminAddBooking() {
  document.getElementById('adminMenuModal').classList.add('hidden');
  document.getElementById('adminAddBookingModal').classList.remove('hidden');
  
  const today = new Date().toISOString().split('T')[0];
  document.getElementById('adminDate').value = today;
  
  // Set default time values
  document.getElementById('adminStartTime').value = '09:00';
  document.getElementById('adminEndTime').value = '12:00';
}

function closeAdminAddBooking() {
  document.getElementById('adminAddBookingModal').classList.add('hidden');
  document.getElementById('adminAddBookingForm').reset();
  
  // Reset form to add mode
  const modalTitle = document.querySelector('#adminAddBookingModal h3');
  modalTitle.innerHTML = '<i class="fas fa-plus-circle mr-2 text-green-600"></i>เพิ่มการจองใหม่ (Admin)';
  
  const submitBtn = document.querySelector('#adminAddBookingForm button[type="submit"]');
  submitBtn.innerHTML = '<i class="fas fa-plus mr-2"></i>เพิ่มการจอง';
  
  // Clear editing ID
  delete document.getElementById('adminAddBookingForm').dataset.editingId;
  
  // Uncheck all equipment checkboxes
  document.querySelectorAll('.admin-equipment-checkbox').forEach(checkbox => {
    checkbox.checked = false;
  });
}

function submitAdminAddBooking(event) {
  event.preventDefault();
  
  const form = event.target;
  const editingId = form.dataset.editingId;
  const isEditing = !!editingId;
  
  const room = document.getElementById('adminRoom').value;
  const date = document.getElementById('adminDate').value;
  const startTime = document.getElementById('adminStartTime').value;
  const endTime = document.getElementById('adminEndTime').value;
  const booker = document.getElementById('adminBooker').value.trim();
  const department = document.getElementById('adminDepartment').value;
  const topic = document.getElementById('adminTopic').value.trim();
  const attendees = document.getElementById('adminAttendees').value;
  const phone = document.getElementById('adminPhone').value.trim();
  
  // Validate required fields
  if (!room || !date || !startTime || !endTime || !booker || !department || !topic || !attendees) {
    showNotification('❌ กรุณากรอกข้อมูลที่จำเป็นให้ครบถ้วน', 'error');
    return;
  }
  
  // Validate time
  if (startTime >= endTime) {
    showNotification('❌ เวลาเริ่มต้องน้อยกว่าเวลาสิ้นสุด', 'error');
    return;
  }
  
  // Validate attendees
  const attendeesNum = parseInt(attendees);
  if (attendeesNum < 1 || attendeesNum > 50) {
    showNotification('❌ จำนวนผู้เข้าร่วมต้องอยู่ระหว่าง 1-50 คน', 'error');
    return;
  }
  
  // Check for conflicts (exclude current booking if editing)
  const existingBookings = JSON.parse(localStorage.getItem('bookings') || '[]');
  const timeDisplay = `${startTime}-${endTime}`;
  
  const hasConflict = existingBookings.some(booking => 
    booking.room === room && 
    booking.date === date && 
    booking.time === timeDisplay &&
    (!isEditing || booking.id != editingId)
  );
  
  if (hasConflict) {
    showNotification('❌ มีการจองซ้ำในห้องและเวลาเดียวกัน', 'error');
    return;
  }
  
  // Get selected equipment
  const equipment = [];
  document.querySelectorAll('.admin-equipment-checkbox:checked').forEach(checkbox => {
    equipment.push(checkbox.value);
  });
  
  if (isEditing) {
    // Update existing booking
    const bookingIndex = existingBookings.findIndex(b => b.id == editingId);
    if (bookingIndex !== -1) {
      existingBookings[bookingIndex] = {
        ...existingBookings[bookingIndex],
        room: room,
        date: date,
        time: timeDisplay,
        booker: booker,
        department: department,
        topic: topic,
        attendees: attendeesNum,
        phone: phone,
        equipment: equipment,
        updatedAt: new Date().toISOString(),
        updatedBy: 'admin'
      };
      
      localStorage.setItem('bookings', JSON.stringify(existingBookings));
      showNotification('✅ แก้ไขการจองสำเร็จ!', 'success');
    }
  } else {
    // Create new booking
    const booking = {
      id: Date.now() + Math.floor(Math.random() * 1000),
      room: room,
      date: date,
      time: timeDisplay,
      booker: booker,
      department: department,
      topic: topic,
      attendees: attendeesNum,
      phone: phone,
      equipment: equipment,
      createdAt: new Date().toISOString(),
      createdBy: 'admin',
      status: 'confirmed'
    };
    
    existingBookings.push(booking);
    localStorage.setItem('bookings', JSON.stringify(existingBookings));
    showNotification('✅ เพิ่มการจองสำเร็จ!', 'success');
  }
  
  // Update displays
  updateTodayBookings();
  generateCalendar();
  updateStatsDisplay();
  updateAdminStats();
  
  // Refresh manage bookings if open
  const manageModal = document.getElementById('adminManageBookingsModal');
  if (!manageModal.classList.contains('hidden')) {
    loadAdminBookingsList();
  }
  
  // Refresh today bookings section if open
  const todaySection = document.getElementById('todayBookingsSection');
  if (!todaySection.classList.contains('hidden')) {
    loadTodayBookingsSection();
  }
  
  // Close modal and show admin menu
  closeAdminAddBooking();
  
  setTimeout(() => {
    showAdminMenu();
  }, 1500);
}

// Admin manage bookings functions
function showAdminManageBookings() {
  document.getElementById('adminMenuModal').classList.add('hidden');
  document.getElementById('adminManageBookingsModal').classList.remove('hidden');
  loadAdminBookingsList();
}

function closeAdminManageBookings() {
  document.getElementById('adminManageBookingsModal').classList.add('hidden');
}

function loadAdminBookingsList() {
  let bookings = JSON.parse(localStorage.getItem('bookings') || '[]');
  
  const searchTerm = document.getElementById('adminSearchBookings')?.value.toLowerCase() || '';
  const roomFilter = document.getElementById('adminFilterRoom')?.value || '';
  const dateFilter = document.getElementById('adminFilterDate')?.value || '';
  const sortBy = document.getElementById('adminSortBy')?.value || 'date';
  
  // Apply filters
  if (searchTerm) {
    bookings = bookings.filter(booking => 
      booking.booker.toLowerCase().includes(searchTerm) ||
      booking.topic.toLowerCase().includes(searchTerm) ||
      booking.room.toLowerCase().includes(searchTerm) ||
      booking.department.toLowerCase().includes(searchTerm)
    );
  }
  
  if (roomFilter) {
    bookings = bookings.filter(booking => booking.room === roomFilter);
  }
  
  if (dateFilter) {
    const today = new Date();
    const todayStr = today.toISOString().split('T')[0];
    
    switch (dateFilter) {
      case 'today':
        bookings = bookings.filter(booking => booking.date === todayStr);
        break;
      case 'tomorrow':
        const tomorrow = new Date(today);
        tomorrow.setDate(tomorrow.getDate() + 1);
        const tomorrowStr = tomorrow.toISOString().split('T')[0];
        bookings = bookings.filter(booking => booking.date === tomorrowStr);
        break;
    }
  }
  
  // Sort bookings
  bookings.sort((a, b) => {
    switch (sortBy) {
      case 'date':
        return new Date(a.date) - new Date(b.date);
      case 'time':
        return a.time.localeCompare(b.time);
      case 'room':
        return a.room.localeCompare(b.room);
      case 'booker':
        return a.booker.localeCompare(b.booker);
      default:
        return 0;
    }
  });
  
  const container = document.getElementById('adminBookingsList');
  const countElement = document.getElementById('adminTotalBookingsCount');
  
  countElement.textContent = bookings.length;
  
  if (bookings.length === 0) {
    container.innerHTML = `
      <div class="text-center py-12">
        <div class="text-gray-400 text-6xl mb-4">
          <i class="fas fa-search"></i>
        </div>
        <h4 class="text-xl font-semibold text-gray-600 mb-2">ไม่พบข้อมูลการจอง</h4>
        <p class="text-gray-500">ลองเปลี่ยนเงื่อนไขการค้นหาหรือกรอง</p>
      </div>
    `;
    return;
  }
  
  container.innerHTML = bookings.map(booking => {
    const formattedDate = new Date(booking.date).toLocaleDateString('th-TH', {
      year: 'numeric',
      month: 'short',
      day: 'numeric'
    });
    
    const statusColor = booking.status === 'confirmed' ? 'bg-green-100 text-green-800' : 'bg-yellow-100 text-yellow-800';
    const statusIcon = booking.status === 'confirmed' ? 'fas fa-check-circle' : 'fas fa-clock';
    
    return `
      <div class="admin-booking-item bg-white border-2 border-gray-200 p-5 rounded-xl hover:shadow-lg transition-all duration-300 hover:border-blue-300" data-booking-id="${booking.id}">
        <div class="flex items-start justify-between">
          <div class="flex items-start space-x-4">
            <input type="checkbox" class="admin-booking-checkbox mt-2 w-5 h-5 text-blue-600 rounded focus:ring-blue-500" data-booking-id="${booking.id}">
            <div class="flex-1">
              <div class="flex items-center justify-between mb-3">
                <div class="flex items-center space-x-3">
                  <h4 class="text-xl font-bold text-gray-800">${booking.topic}</h4>
                  <span class="text-xs ${statusColor} px-2 py-1 rounded-full font-medium">
                    <i class="${statusIcon} mr-1"></i>${booking.status === 'confirmed' ? 'ยืนยันแล้ว' : 'รอยืนยัน'}
                  </span>
                </div>
                <span class="text-xs bg-gray-100 px-3 py-1 rounded-full font-mono">ID: ${booking.id}</span>
              </div>
              
              <div class="grid grid-cols-1 md:grid-cols-3 gap-6 text-sm mb-4">
                <div class="space-y-2">
                  <div class="flex items-center">
                    <i class="fas fa-door-open text-blue-600 mr-3 w-5"></i>
                    <span class="font-semibold text-gray-700">ห้อง:</span>
                    <span class="ml-2 font-bold text-blue-800">${booking.room}</span>
                  </div>
                  <div class="flex items-center">
                    <i class="fas fa-calendar text-green-600 mr-3 w-5"></i>
                    <span class="font-semibold text-gray-700">วันที่:</span>
                    <span class="ml-2 text-gray-800">${formattedDate}</span>
                  </div>
                  <div class="flex items-center">
                    <i class="fas fa-clock text-orange-600 mr-3 w-5"></i>
                    <span class="font-semibold text-gray-700">เวลา:</span>
                    <span class="ml-2 font-bold text-orange-800">${booking.time}</span>
                  </div>
                </div>
                
                <div class="space-y-2">
                  <div class="flex items-center">
                    <i class="fas fa-user text-purple-600 mr-3 w-5"></i>
                    <span class="font-semibold text-gray-700">ผู้จอง:</span>
                    <span class="ml-2 text-gray-800">${booking.booker}</span>
                  </div>
                  <div class="flex items-center">
                    <i class="fas fa-building text-teal-600 mr-3 w-5"></i>
                    <span class="font-semibold text-gray-700">แผนก:</span>
                    <span class="ml-2 text-gray-800">${booking.department}</span>
                  </div>
                  <div class="flex items-center">
                    <i class="fas fa-users text-pink-600 mr-3 w-5"></i>
                    <span class="font-semibold text-gray-700">จำนวน:</span>
                    <span class="ml-2 font-bold text-pink-800">${booking.attendees} คน</span>
                  </div>
                </div>
                
                <div class="space-y-2">
                  ${booking.phone ? `
                    <div class="flex items-center">
                      <i class="fas fa-phone text-blue-500 mr-3 w-5"></i>
                      <span class="font-semibold text-gray-700">โทร:</span>
                      <span class="ml-2 text-gray-800">${booking.phone}</span>
                    </div>
                  ` : ''}
                  ${booking.equipment && booking.equipment.length > 0 ? `
                    <div class="flex items-start">
                      <i class="fas fa-tools text-gray-600 mr-3 w-5 mt-0.5"></i>
                      <div>
                        <span class="font-semibold text-gray-700">อุปกรณ์:</span>
                        <div class="flex flex-wrap gap-1 mt-1">
                          ${booking.equipment.slice(0, 3).map(eq => `
                            <span class="bg-blue-100 text-blue-800 text-xs px-2 py-1 rounded-full font-medium">${eq}</span>
                          `).join('')}
                          ${booking.equipment.length > 3 ? `<span class="text-xs text-gray-500 bg-gray-100 px-2 py-1 rounded-full">+${booking.equipment.length - 3}</span>` : ''}
                        </div>
                      </div>
                    </div>
                  ` : ''}
                  ${booking.createdAt ? `
                    <div class="flex items-center">
                      <i class="fas fa-calendar-plus text-gray-500 mr-3 w-5"></i>
                      <span class="font-semibold text-gray-700">สร้างเมื่อ:</span>
                      <span class="ml-2 text-xs text-gray-600">${new Date(booking.createdAt).toLocaleDateString('th-TH')}</span>
                    </div>
                  ` : ''}
                </div>
              </div>
              
              ${booking.equipment && booking.equipment.length > 3 ? `
                <div class="bg-gray-50 p-3 rounded-lg mb-3">
                  <div class="flex items-start">
                    <i class="fas fa-list text-gray-600 mr-2 mt-0.5"></i>
                    <div>
                      <span class="text-sm font-semibold text-gray-700">อุปกรณ์ทั้งหมด:</span>
                      <div class="flex flex-wrap gap-1 mt-1">
                        ${booking.equipment.map(eq => `
                          <span class="bg-white text-gray-700 text-xs px-2 py-1 rounded border">${eq}</span>
                        `).join('')}
                      </div>
                    </div>
                  </div>
                </div>
              ` : ''}
            </div>
          </div>
          
          <div class="flex flex-col space-y-2 ml-4">
            <button onclick="viewBookingDetails(${booking.id})" class="bg-green-500 text-white px-4 py-2 rounded-lg hover:bg-green-600 transition-colors text-sm font-medium shadow-sm">
              <i class="fas fa-eye mr-2"></i>ดูรายละเอียด
            </button>
            <button onclick="editBooking(${booking.id})" class="bg-blue-500 text-white px-4 py-2 rounded-lg hover:bg-blue-600 transition-colors text-sm font-medium shadow-sm">
              <i class="fas fa-edit mr-2"></i>แก้ไข
            </button>
            <button onclick="deleteAdminBooking(${booking.id})" class="bg-red-500 text-white px-4 py-2 rounded-lg hover:bg-red-600 transition-colors text-sm font-medium shadow-sm">
              <i class="fas fa-trash mr-2"></i>ลบ
            </button>
          </div>
        </div>
      </div>
    `;
  }).join('');
}

function deleteAdminBooking(bookingId) {
  if (!isAdmin) {
    showNotification('❌ คุณไม่มีสิทธิ์ในการลบการจอง', 'error');
    return;
  }
  
  console.log('=== DELETE ADMIN BOOKING DEBUG ===');
  console.log('Input bookingId:', bookingId, 'Type:', typeof bookingId);
  
  // Get current bookings
  let bookings = JSON.parse(localStorage.getItem('bookings') || '[]');
  console.log('Total bookings before delete:', bookings.length);
  
  // Convert ID to string for consistent comparison
  const targetId = String(bookingId);
  console.log('Target ID as string:', targetId);
  
  // Find booking using string comparison
  const booking = bookings.find(b => String(b.id) === targetId);
  
  if (!booking) {
    console.log('❌ Booking not found for deletion');
    showNotification(`❌ ไม่พบข้อมูลการจอง (ID: ${bookingId})`, 'error');
    return;
  }
  
  console.log('✅ Found booking for deletion:', booking.topic, 'with ID:', booking.id);
  
  const formattedDate = new Date(booking.date).toLocaleDateString('th-TH', {
    year: 'numeric',
    month: 'long',
    day: 'numeric'
  });
  
  // Create custom confirmation modal instead of browser confirm
  const confirmModal = document.createElement('div');
  confirmModal.className = 'fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-50';
  confirmModal.innerHTML = `
    <div class="bg-white rounded-2xl p-8 max-w-md mx-4 text-center animate-slideIn">
      <div class="text-red-500 text-6xl mb-4">
        <i class="fas fa-trash-alt"></i>
      </div>
      <h3 class="text-2xl font-bold text-red-600 mb-4">⚠️ ยืนยันการลบ</h3>
      
      <div class="bg-red-50 border-2 border-red-200 rounded-lg p-4 mb-6 text-left">
        <h4 class="font-bold text-red-800 mb-3">
          <i class="fas fa-exclamation-triangle mr-2"></i>คุณต้องการลบการจองนี้หรือไม่?
        </h4>
        
        <div class="space-y-2 text-sm">
          <div class="flex items-center">
            <i class="fas fa-clipboard-list text-red-600 mr-2 w-4"></i>
            <span class="font-semibold">หัวข้อ:</span>
            <span class="ml-2">${booking.topic}</span>
          </div>
          <div class="flex items-center">
            <i class="fas fa-door-open text-red-600 mr-2 w-4"></i>
            <span class="font-semibold">ห้อง:</span>
            <span class="ml-2 font-bold">${booking.room}</span>
          </div>
          <div class="flex items-center">
            <i class="fas fa-calendar text-red-600 mr-2 w-4"></i>
            <span class="font-semibold">วันที่:</span>
            <span class="ml-2">${formattedDate}</span>
          </div>
          <div class="flex items-center">
            <i class="fas fa-clock text-red-600 mr-2 w-4"></i>
            <span class="font-semibold">เวลา:</span>
            <span class="ml-2 font-bold">${booking.time}</span>
          </div>
          <div class="flex items-center">
            <i class="fas fa-user text-red-600 mr-2 w-4"></i>
            <span class="font-semibold">ผู้จอง:</span>
            <span class="ml-2">${booking.booker}</span>
          </div>
        </div>
      </div>
      
      <div class="bg-yellow-50 border border-yellow-200 rounded-lg p-3 mb-6">
        <p class="text-sm text-yellow-800">
          <i class="fas fa-exclamation-triangle mr-2"></i>
          <strong>คำเตือน:</strong> การดำเนินการนี้ไม่สามารถยกเลิกได้
        </p>
      </div>
      
      <div class="flex space-x-3 justify-center">
        <button onclick="actuallyDeleteBooking('${targetId}'); this.closest('.fixed').remove();" class="bg-red-500 text-white px-6 py-3 rounded-lg hover:bg-red-600 transition-colors font-semibold">
          <i class="fas fa-trash mr-2"></i>ยืนยันการลบ
        </button>
        <button onclick="this.closest('.fixed').remove(); showNotification('❌ ยกเลิกการลบข้อมูล', 'info');" class="bg-gray-600 text-white px-6 py-3 rounded-lg hover:bg-gray-700 transition-colors font-semibold">
          <i class="fas fa-times mr-2"></i>ยกเลิก
        </button>
      </div>
    </div>
  `;
  
  document.body.appendChild(confirmModal);
  
  // Auto remove after 30 seconds
  setTimeout(() => {
    if (document.body.contains(confirmModal)) {
      document.body.removeChild(confirmModal);
      showNotification('⏰ หมดเวลายืนยัน - ยกเลิกการลบข้อมูล', 'warning');
    }
  }, 30000);
}

// New function to handle actual deletion after confirmation
function actuallyDeleteBooking(targetId) {
  console.log('=== ACTUALLY DELETE BOOKING ===');
  console.log('Confirming deletion for ID:', targetId);
  
  // Get current bookings
  let bookings = JSON.parse(localStorage.getItem('bookings') || '[]');
  
  // Find booking again to ensure it still exists
  const booking = bookings.find(b => String(b.id) === targetId);
  
  if (!booking) {
    console.log('❌ Booking no longer exists');
    showNotification('❌ ไม่พบข้อมูลการจอง อาจถูกลบไปแล้ว', 'error');
    return;
  }
  
  // Remove booking using filter with string comparison
  const updatedBookings = bookings.filter(b => String(b.id) !== targetId);
  
  const deletedCount = bookings.length - updatedBookings.length;
  console.log(`Deletion result - Original: ${bookings.length}, Updated: ${updatedBookings.length}, Deleted: ${deletedCount}`);
  
  if (deletedCount === 0) {
    console.log('❌ No bookings were deleted');
    showNotification('❌ ไม่สามารถลบการจองได้ กรุณาลองใหม่อีกครั้ง', 'error');
    return;
  }
  
  // Save the updated bookings
  try {
    localStorage.setItem('bookings', JSON.stringify(updatedBookings));
    console.log('✅ Updated bookings saved to localStorage');
  } catch (error) {
    console.log('❌ Error saving to localStorage:', error);
    showNotification('❌ เกิดข้อผิดพลาดในการบันทึกข้อมูล', 'error');
    return;
  }
  
  // Update all displays
  updateTodayBookings();
  generateCalendar();
  updateStatsDisplay();
  updateAdminStats();
  
  // Refresh manage bookings list if modal is open
  const manageModal = document.getElementById('adminManageBookingsModal');
  if (!manageModal.classList.contains('hidden')) {
    setTimeout(() => {
      loadAdminBookingsList();
    }, 100);
  }
  
  // Refresh today bookings section if open
  const todaySection = document.getElementById('todayBookingsSection');
  if (!todaySection.classList.contains('hidden')) {
    setTimeout(() => {
      loadTodayBookingsSection();
    }, 100);
  }
  
  showNotification(`✅ ลบการจอง "${booking.topic}" สำเร็จ!`, 'success');
  console.log('✅ Delete operation completed successfully');
}

// Keep the old function for backward compatibility
function confirmDeleteBooking(targetId) {
  actuallyDeleteBooking(targetId);
}

function deleteSelectedAdminBookings() {
  if (!isAdmin) {
    showNotification('❌ คุณไม่มีสิทธิ์ในการลบการจอง', 'error');
    return;
  }
  
  const selectedCheckboxes = document.querySelectorAll('.admin-booking-checkbox:checked');
  
  if (selectedCheckboxes.length === 0) {
    showNotification('⚠️ กรุณาเลือกรายการที่ต้องการลบ', 'warning');
    return;
  }
  
  // Get selected IDs and convert to strings
  const selectedIds = Array.from(selectedCheckboxes).map(cb => String(cb.getAttribute('data-booking-id')));
  
  console.log('=== DELETE SELECTED DEBUG ===');
  console.log('Selected checkboxes count:', selectedCheckboxes.length);
  console.log('Selected IDs:', selectedIds);
  
  // Get current bookings
  let bookings = JSON.parse(localStorage.getItem('bookings') || '[]');
  console.log('Total bookings before filter:', bookings.length);
  
  // Find selected bookings using string comparison
  const selectedBookings = bookings.filter(booking => {
    const bookingIdStr = String(booking.id);
    const isSelected = selectedIds.includes(bookingIdStr);
    console.log(`Checking booking "${booking.topic}" (ID: ${booking.id}): ${isSelected ? 'SELECTED ✅' : 'not selected ❌'}`);
    return isSelected;
  });
  
  console.log('Found selected bookings:', selectedBookings.length);
  
  if (selectedBookings.length === 0) {
    showNotification('❌ ไม่พบรายการที่เลือกในระบบ กรุณาลองใหม่', 'error');
    return;
  }
  
  // Create custom confirmation modal for multiple deletions
  const confirmModal = document.createElement('div');
  confirmModal.className = 'fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-50';
  confirmModal.innerHTML = `
    <div class="bg-white rounded-2xl p-8 max-w-2xl mx-4 text-center animate-slideIn max-h-96 overflow-y-auto">
      <div class="text-red-500 text-6xl mb-4">
        <i class="fas fa-trash-alt"></i>
      </div>
      <h3 class="text-2xl font-bold text-red-600 mb-4">⚠️ ยืนยันการลบหลายรายการ</h3>
      
      <div class="bg-red-50 border-2 border-red-200 rounded-lg p-4 mb-6">
        <h4 class="font-bold text-red-800 mb-3">
          <i class="fas fa-exclamation-triangle mr-2"></i>คุณต้องการลบการจองที่เลือกหรือไม่?
        </h4>
        
        <div class="text-center mb-4">
          <span class="bg-red-100 text-red-800 px-4 py-2 rounded-full font-bold text-lg">
            จำนวน: ${selectedBookings.length} รายการ
          </span>
        </div>
        
        <div class="max-h-40 overflow-y-auto text-left">
          <div class="space-y-2 text-sm">
            ${selectedBookings.slice(0, 5).map(booking => `
              <div class="flex items-center bg-white p-2 rounded border">
                <i class="fas fa-clipboard-list text-red-600 mr-2 w-4"></i>
                <div class="flex-1">
                  <div class="font-semibold">${booking.topic}</div>
                  <div class="text-xs text-gray-600">${booking.room} | ${booking.time} | ${booking.booker}</div>
                </div>
              </div>
            `).join('')}
            ${selectedBookings.length > 5 ? `
              <div class="text-center text-gray-600 text-sm py-2">
                <i class="fas fa-ellipsis-h mr-2"></i>และอีก ${selectedBookings.length - 5} รายการ
              </div>
            ` : ''}
          </div>
        </div>
      </div>
      
      <div class="bg-yellow-50 border border-yellow-200 rounded-lg p-3 mb-6">
        <p class="text-sm text-yellow-800">
          <i class="fas fa-exclamation-triangle mr-2"></i>
          <strong>คำเตือน:</strong> การดำเนินการนี้ไม่สามารถยกเลิกได้
        </p>
      </div>
      
      <div class="flex space-x-3 justify-center">
        <button onclick="confirmDeleteSelectedBookings(${JSON.stringify(selectedIds).replace(/"/g, '&quot;')}); this.closest('.fixed').remove();" class="bg-red-500 text-white px-6 py-3 rounded-lg hover:bg-red-600 transition-colors font-semibold">
          <i class="fas fa-trash mr-2"></i>ยืนยันการลบ ${selectedBookings.length} รายการ
        </button>
        <button onclick="this.closest('.fixed').remove(); showNotification('❌ ยกเลิกการลบข้อมูล', 'info');" class="bg-gray-600 text-white px-6 py-3 rounded-lg hover:bg-gray-700 transition-colors font-semibold">
          <i class="fas fa-times mr-2"></i>ยกเลิก
        </button>
      </div>
    </div>
  `;
  
  document.body.appendChild(confirmModal);
  
  // Auto remove after 30 seconds
  setTimeout(() => {
    if (document.body.contains(confirmModal)) {
      document.body.removeChild(confirmModal);
      showNotification('⏰ หมดเวลายืนยัน - ยกเลิกการลบข้อมูล', 'warning');
    }
  }, 30000);
}

// New function to handle actual deletion of selected bookings after confirmation
function confirmDeleteSelectedBookings(selectedIds) {
  console.log('=== CONFIRM DELETE SELECTED BOOKINGS ===');
  console.log('Confirming deletion for IDs:', selectedIds);
  
  // Get current bookings
  let bookings = JSON.parse(localStorage.getItem('bookings') || '[]');
  
  // Remove selected bookings using filter with string comparison
  const updatedBookings = bookings.filter(booking => {
    const bookingIdStr = String(booking.id);
    const shouldKeep = !selectedIds.includes(bookingIdStr);
    console.log(`Processing booking "${booking.topic}" (ID: ${booking.id}): ${shouldKeep ? 'KEEP ✅' : 'DELETE 🗑️'}`);
    return shouldKeep;
  });
  
  const deletedCount = bookings.length - updatedBookings.length;
  
  console.log(`=== DELETION SUMMARY ===`);
  console.log(`Original count: ${bookings.length}`);
  console.log(`Updated count: ${updatedBookings.length}`);
  console.log(`Deleted count: ${deletedCount}`);
  console.log(`Expected deleted: ${selectedIds.length}`);
  
  if (deletedCount === 0) {
    showNotification('❌ ไม่สามารถลบการจองได้ กรุณาตรวจสอบและลองใหม่', 'error');
    return;
  }
  
  // Save updated bookings
  localStorage.setItem('bookings', JSON.stringify(updatedBookings));
  console.log('✅ Updated bookings saved to localStorage');
  
  // Clear all checkboxes
  document.querySelectorAll('.admin-booking-checkbox').forEach(cb => {
    cb.checked = false;
  });
  
  // Reset select all button
  const selectAllBtn = document.getElementById('adminSelectAllBookings');
  if (selectAllBtn) {
    selectAllBtn.innerHTML = '<i class="fas fa-check-square mr-1"></i>เลือกทั้งหมด';
  }
  
  // Update all displays
  updateTodayBookings();
  generateCalendar();
  updateStatsDisplay();
  updateAdminStats();
  
  // Refresh manage bookings list
  setTimeout(() => {
    loadAdminBookingsList();
    showNotification(`✅ ลบการจองสำเร็จ ${deletedCount} รายการ!`, 'success', 4000);
  }, 200);
  
  // Refresh today bookings section if open
  const todaySection = document.getElementById('todayBookingsSection');
  if (!todaySection.classList.contains('hidden')) {
    setTimeout(() => {
      loadTodayBookingsSection();
    }, 300);
  }
  
  console.log('✅ Delete operation completed successfully');
}

function selectAllAdminBookings() {
  const checkboxes = document.querySelectorAll('.admin-booking-checkbox');
  const selectAllBtn = document.getElementById('adminSelectAllBookings');
  const allChecked = Array.from(checkboxes).every(cb => cb.checked);
  
  checkboxes.forEach(checkbox => {
    checkbox.checked = !allChecked;
  });
  
  selectAllBtn.innerHTML = allChecked 
    ? '<i class="fas fa-check-square mr-1"></i>เลือกทั้งหมด'
    : '<i class="fas fa-square mr-1"></i>ยกเลิกทั้งหมด';
}



// Setup stats button listeners
function setupStatsButtonListeners() {
  // Remove existing listeners first
  const editStatsBtn = document.getElementById('editStatsBtn');
  const resetStatsBtn = document.getElementById('resetStatsBtn');
  const resetAllBtn = document.getElementById('resetAllBtn');
  
  console.log('Setting up stats button listeners...');
  console.log('Stats button elements found:', {
    editStatsBtn: !!editStatsBtn,
    resetStatsBtn: !!resetStatsBtn,
    resetAllBtn: !!resetAllBtn
  });
  
  // Add event listeners directly without setTimeout
  if (editStatsBtn) {
    // Remove existing listener if any
    editStatsBtn.removeEventListener('click', editStats);
    editStatsBtn.addEventListener('click', editStats);
    console.log('✅ Edit stats button listener added');
  }
  
  if (resetStatsBtn) {
    // Remove existing listener if any
    resetStatsBtn.removeEventListener('click', resetStats);
    resetStatsBtn.addEventListener('click', resetStats);
    console.log('✅ Reset stats button listener added');
  }
  
  if (resetAllBtn) {
    // Remove existing listener if any
    resetAllBtn.removeEventListener('click', resetAllData);
    resetAllBtn.addEventListener('click', resetAllData);
    console.log('✅ Reset all button listener added');
  }
  
  console.log('✅ Stats button listeners setup completed');
}

// Setup admin button listeners
function setupAdminButtonListeners() {
  // Wait for DOM to be ready and setup listeners with delay
  setTimeout(() => {
    console.log('Setting up admin button listeners...');
    
    // Admin menu buttons
    const closeAdminMenu1 = document.getElementById('closeAdminMenu');
    const closeAdminMenu2 = document.getElementById('closeAdminMenuBtn');
    const addNewBookingBtn = document.getElementById('addNewBookingBtn');
    const manageBookingsBtn = document.getElementById('manageBookingsBtn');
    
    console.log('Admin menu elements found:', {
      closeAdminMenu1: !!closeAdminMenu1,
      closeAdminMenu2: !!closeAdminMenu2,
      addNewBookingBtn: !!addNewBookingBtn,
      manageBookingsBtn: !!manageBookingsBtn
    });
    
    if (closeAdminMenu1) closeAdminMenu1.addEventListener('click', closeAdminMenu);
    if (closeAdminMenu2) closeAdminMenu2.addEventListener('click', closeAdminMenu);
    if (addNewBookingBtn) addNewBookingBtn.addEventListener('click', showAdminAddBooking);
    if (manageBookingsBtn) manageBookingsBtn.addEventListener('click', showAdminManageBookings);
    
    // Admin add booking modal
    const closeAdminAddBooking1 = document.getElementById('closeAdminAddBooking');
    const cancelAdminAddBooking = document.getElementById('cancelAdminAddBooking');
    const adminAddBookingForm = document.getElementById('adminAddBookingForm');
    
    console.log('Admin add booking elements found:', {
      closeAdminAddBooking1: !!closeAdminAddBooking1,
      cancelAdminAddBooking: !!cancelAdminAddBooking,
      adminAddBookingForm: !!adminAddBookingForm
    });
    
    if (closeAdminAddBooking1) closeAdminAddBooking1.addEventListener('click', closeAdminAddBooking);
    if (cancelAdminAddBooking) cancelAdminAddBooking.addEventListener('click', closeAdminAddBooking);
    if (adminAddBookingForm) adminAddBookingForm.addEventListener('submit', submitAdminAddBooking);
    
    // Admin manage bookings modal
    const closeAdminManageBookings1 = document.getElementById('closeAdminManageBookings');
    const closeAdminManageBookings2 = document.getElementById('closeAdminManageBookingsBtn');
    const adminSelectAllBookings = document.getElementById('adminSelectAllBookings');
    const adminDeleteSelectedBookings = document.getElementById('adminDeleteSelectedBookings');
    
    console.log('Admin manage bookings elements found:', {
      closeAdminManageBookings1: !!closeAdminManageBookings1,
      closeAdminManageBookings2: !!closeAdminManageBookings2,
      adminSelectAllBookings: !!adminSelectAllBookings,
      adminDeleteSelectedBookings: !!adminDeleteSelectedBookings
    });
    
    if (closeAdminManageBookings1) closeAdminManageBookings1.addEventListener('click', closeAdminManageBookings);
    if (closeAdminManageBookings2) closeAdminManageBookings2.addEventListener('click', closeAdminManageBookings);
    if (adminSelectAllBookings) adminSelectAllBookings.addEventListener('click', selectAllAdminBookings);
    if (adminDeleteSelectedBookings) adminDeleteSelectedBookings.addEventListener('click', deleteSelectedAdminBookings);
    
    // Filter and search listeners
    const adminSearchBookings = document.getElementById('adminSearchBookings');
    const adminFilterRoom = document.getElementById('adminFilterRoom');
    const adminFilterDate = document.getElementById('adminFilterDate');
    const adminSortBy = document.getElementById('adminSortBy');
    
    console.log('Filter elements found:', {
      adminSearchBookings: !!adminSearchBookings,
      adminFilterRoom: !!adminFilterRoom,
      adminFilterDate: !!adminFilterDate,
      adminSortBy: !!adminSortBy
    });
    
    if (adminSearchBookings) adminSearchBookings.addEventListener('input', loadAdminBookingsList);
    if (adminFilterRoom) adminFilterRoom.addEventListener('change', loadAdminBookingsList);
    if (adminFilterDate) adminFilterDate.addEventListener('change', loadAdminBookingsList);
    if (adminSortBy) adminSortBy.addEventListener('change', loadAdminBookingsList);
    
    console.log('Admin button listeners setup completed');
  }, 100);
}



// Today's Bookings Functions
function showTodayBookingsSection() {
  document.getElementById('welcomeSection').classList.add('hidden');
  document.getElementById('bookingForm').classList.add('hidden');
  document.getElementById('todayBookingsSection').classList.remove('hidden');
  
  // Update active navigation state
  updateActiveNavigation('today');
  
  loadTodayBookingsSection();
}

function hideTodayBookingsSection() {
  document.getElementById('todayBookingsSection').classList.add('hidden');
  document.getElementById('welcomeSection').classList.remove('hidden');
  
  // Update active navigation state
  updateActiveNavigation('home');
}

function loadTodayBookingsSection() {
  const bookings = JSON.parse(localStorage.getItem('bookings') || '[]');
  const today = new Date().toISOString().split('T')[0];
  const todayBookings = bookings.filter(booking => booking.date === today);
  
  const container = document.getElementById('todayBookingsList');
  const emptyState = document.getElementById('emptyTodayBookings');
  
  if (todayBookings.length === 0) {
    container.innerHTML = '';
    emptyState.classList.remove('hidden');
    return;
  }
  
  emptyState.classList.add('hidden');
  
  container.innerHTML = todayBookings.map(booking => {
    const roomColors = {
      'ห้อง 1A': 'from-red-50 to-red-100 border-red-200',
      'ห้อง 1B': 'from-orange-50 to-orange-100 border-orange-200',
      'ห้อง 500': 'from-blue-50 to-blue-100 border-blue-200',
      'ห้อง 501': 'from-green-50 to-green-100 border-green-200',
      'ห้อง 502': 'from-purple-50 to-purple-100 border-purple-200'
    };
    
    const roomColor = roomColors[booking.room] || 'from-gray-50 to-gray-100 border-gray-200';
    
    return `
      <div class="booking-card bg-gradient-to-r ${roomColor} p-6 rounded-xl border-2 shadow-sm hover:shadow-md transition-all duration-300">
        <div class="flex justify-between items-start mb-4">
          <div class="flex-1">
            <h4 class="text-xl font-bold text-gray-800 mb-2">${booking.topic}</h4>
            
            <div class="grid grid-cols-1 md:grid-cols-2 gap-4 mb-4">
              <div class="space-y-2">
                <div class="flex items-center">
                  <i class="fas fa-door-open text-blue-600 mr-3 w-4"></i>
                  <span class="font-semibold text-gray-700">ห้อง:</span>
                  <span class="ml-2 font-bold text-gray-800">${booking.room}</span>
                </div>
                <div class="flex items-center">
                  <i class="fas fa-clock text-green-600 mr-3 w-4"></i>
                  <span class="font-semibold text-gray-700">เวลา:</span>
                  <span class="ml-2 font-bold text-gray-800">${booking.time}</span>
                </div>
                <div class="flex items-center">
                  <i class="fas fa-users text-orange-600 mr-3 w-4"></i>
                  <span class="font-semibold text-gray-700">จำนวนคน:</span>
                  <span class="ml-2 font-bold text-gray-800">${booking.attendees} คน</span>
                </div>
              </div>
              
              <div class="space-y-2">
                <div class="flex items-center">
                  <i class="fas fa-user text-purple-600 mr-3 w-4"></i>
                  <span class="font-semibold text-gray-700">ผู้จอง:</span>
                  <span class="ml-2 text-gray-800">${booking.booker}</span>
                </div>
                <div class="flex items-center">
                  <i class="fas fa-building text-teal-600 mr-3 w-4"></i>
                  <span class="font-semibold text-gray-700">แผนก:</span>
                  <span class="ml-2 text-gray-800">${booking.department}</span>
                </div>
                ${booking.phone ? `
                  <div class="flex items-center">
                    <i class="fas fa-phone text-indigo-600 mr-3 w-4"></i>
                    <span class="font-semibold text-gray-700">โทร:</span>
                    <span class="ml-2 text-gray-800">${booking.phone}</span>
                  </div>
                ` : ''}
              </div>
            </div>
            
            ${booking.equipment && booking.equipment.length > 0 ? `
              <div class="mb-4">
                <div class="flex items-start">
                  <i class="fas fa-tools text-gray-600 mr-3 w-4 mt-0.5"></i>
                  <div>
                    <span class="font-semibold text-gray-700">อุปกรณ์:</span>
                    <div class="flex flex-wrap gap-2 mt-1">
                      ${booking.equipment.map(equipment => `
                        <span class="bg-white bg-opacity-70 text-gray-700 px-2 py-1 rounded-full text-xs font-medium">
                          ${equipment}
                        </span>
                      `).join('')}
                    </div>
                  </div>
                </div>
              </div>
            ` : ''}
            
            <div class="flex justify-between items-center pt-4 border-t border-white border-opacity-50">
              <div class="flex items-center space-x-4">
                <span class="bg-green-500 text-white px-3 py-1 rounded-full text-xs font-semibold">
                  <i class="fas fa-check-circle mr-1"></i>ยืนยันแล้ว
                </span>
              </div>
              
              <div class="flex space-x-2">
                <div class="admin-controls ${isAdmin ? '' : 'hidden'}">
                  <button onclick="editBooking(${booking.id})" class="bg-blue-500 text-white px-3 py-2 rounded-lg hover:bg-blue-600 transition-colors text-sm mr-2">
                    <i class="fas fa-edit mr-1"></i>แก้ไข
                  </button>
                  <button onclick="confirmDeleteBooking(${booking.id})" class="bg-red-500 text-white px-3 py-2 rounded-lg hover:bg-red-600 transition-colors text-sm">
                    <i class="fas fa-trash mr-1"></i>ลบ
                  </button>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    `;
  }).join('');
}

function refreshTodayBookings() {
  loadTodayBookingsSection();
  showNotification('🔄 รีเฟรชข้อมูลสำเร็จ', 'success', 2000);
}

// Check if two time slots overlap
function checkTimeOverlap(time1, time2) {
  if (time1 === time2) return true;
  
  const parseTime = (timeStr) => {
    const [start, end] = timeStr.split('-');
    return {
      start: start.trim(),
      end: end.trim()
    };
  };
  
  const slot1 = parseTime(time1);
  const slot2 = parseTime(time2);
  
  // Convert time to minutes for easier comparison
  const timeToMinutes = (timeStr) => {
    const [hours, minutes] = timeStr.split(':').map(Number);
    return hours * 60 + minutes;
  };
  
  const slot1Start = timeToMinutes(slot1.start);
  const slot1End = timeToMinutes(slot1.end);
  const slot2Start = timeToMinutes(slot2.start);
  const slot2End = timeToMinutes(slot2.end);
  
  // Check for overlap: slot1 starts before slot2 ends AND slot2 starts before slot1 ends
  return (slot1Start < slot2End && slot2Start < slot1End);
}

// Play alert sound for duplicate booking
function playAlertSound() {
  try {
    // Create audio context for beep sound
    const audioContext = new (window.AudioContext || window.webkitAudioContext)();
    
    // Create oscillator for beep sound
    const oscillator = audioContext.createOscillator();
    const gainNode = audioContext.createGain();
    
    oscillator.connect(gainNode);
    gainNode.connect(audioContext.destination);
    
    // Set frequency and type
    oscillator.frequency.setValueAtTime(800, audioContext.currentTime); // High pitch beep
    oscillator.type = 'sine';
    
    // Set volume
    gainNode.gain.setValueAtTime(0.1, audioContext.currentTime);
    gainNode.gain.exponentialRampToValueAtTime(0.01, audioContext.currentTime + 0.5);
    
    // Play beep for 0.5 seconds
    oscillator.start(audioContext.currentTime);
    oscillator.stop(audioContext.currentTime + 0.5);
    
    // Play second beep after short delay
    setTimeout(() => {
      const oscillator2 = audioContext.createOscillator();
      const gainNode2 = audioContext.createGain();
      
      oscillator2.connect(gainNode2);
      gainNode2.connect(audioContext.destination);
      
      oscillator2.frequency.setValueAtTime(600, audioContext.currentTime);
      oscillator2.type = 'sine';
      
      gainNode2.gain.setValueAtTime(0.1, audioContext.currentTime);
      gainNode2.gain.exponentialRampToValueAtTime(0.01, audioContext.currentTime + 0.5);
      
      oscillator2.start(audioContext.currentTime);
      oscillator2.stop(audioContext.currentTime + 0.5);
    }, 200);
    
  } catch (error) {
    console.log('Audio not supported or blocked:', error);
    // Fallback: vibrate if supported (mobile devices)
    if (navigator.vibrate) {
      navigator.vibrate([200, 100, 200]);
    }
  }
}

// Enhanced duplicate booking alert with sad graphic
function showDuplicateBookingAlert(conflictBooking, formattedDate, conflictType = 'exact') {
  // Determine alert type and styling
  const alertConfig = {
    exact: {
      title: '😢 ห้องไม่ว่างแล้ว!',
      subtitle: 'มีการจองซ้ำในเวลาเดียวกันแล้ว',
      bgColor: 'from-red-500 to-red-600',
      borderColor: 'border-red-300',
      textColor: 'text-red-800',
      iconColor: 'text-red-600',
      icon: 'fas fa-ban',
      alertSound: 'error'
    },
    overlap: {
      title: '😔 เวลาซ้อนทับ!',
      subtitle: 'เวลาที่เลือกซ้อนทับกับการจองที่มีอยู่',
      bgColor: 'from-orange-500 to-red-500',
      borderColor: 'border-orange-300',
      textColor: 'text-orange-800',
      iconColor: 'text-orange-600',
      icon: 'fas fa-exclamation-triangle',
      alertSound: 'warning'
    }
  };
  
  const config = alertConfig[conflictType] || alertConfig.exact;
  
  const conflictModal = document.createElement('div');
  conflictModal.className = 'fixed inset-0 bg-black bg-opacity-60 flex items-center justify-center z-50 animate-fadeIn';
  conflictModal.innerHTML = `
    <div class="bg-white rounded-3xl p-8 max-w-lg mx-4 text-center animate-slideIn shadow-2xl border-4 ${config.borderColor}">
      <!-- Sad Face Graphic -->
      <div class="relative mb-6">
        <div class="mx-auto w-32 h-32 mb-6 relative">
          <!-- Main sad face -->
          <div class="w-full h-full bg-gradient-to-br from-yellow-300 to-yellow-400 rounded-full border-4 border-yellow-500 shadow-xl relative animate-sadBounce">
            <!-- Eyes -->
            <div class="absolute top-8 left-6 w-4 h-6 bg-black rounded-full transform -rotate-12 animate-pulse"></div>
            <div class="absolute top-8 right-6 w-4 h-6 bg-black rounded-full transform rotate-12 animate-pulse"></div>
            
            <!-- Animated Tears -->
            <div class="absolute top-12 left-8 w-2 h-8 bg-gradient-to-b from-blue-300 to-blue-500 rounded-full animate-tearDrop" style="animation-delay: 0.2s;"></div>
            <div class="absolute top-12 right-8 w-2 h-8 bg-gradient-to-b from-blue-300 to-blue-500 rounded-full animate-tearDrop" style="animation-delay: 0.6s;"></div>
            
            <!-- Additional tear drops -->
            <div class="absolute top-14 left-7 w-1 h-4 bg-blue-400 rounded-full animate-tearDrop opacity-70" style="animation-delay: 1s;"></div>
            <div class="absolute top-14 right-7 w-1 h-4 bg-blue-400 rounded-full animate-tearDrop opacity-70" style="animation-delay: 1.4s;"></div>
            
            <!-- Sad mouth -->
            <div class="absolute bottom-6 left-1/2 transform -translate-x-1/2 w-12 h-6 border-4 border-black border-t-0 rounded-b-full"></div>
            
            <!-- Eyebrows (sad) -->
            <div class="absolute top-4 left-4 w-6 h-1 bg-black rounded transform rotate-12"></div>
            <div class="absolute top-4 right-4 w-6 h-1 bg-black rounded transform -rotate-12"></div>
          </div>
          
          <!-- Floating sad particles -->
          <div class="absolute -top-2 -left-2 w-3 h-3 bg-blue-400 rounded-full animate-sadFloat opacity-70"></div>
          <div class="absolute -top-4 right-2 w-2 h-2 bg-blue-300 rounded-full animate-sadFloat opacity-60" style="animation-delay: 0.5s;"></div>
          <div class="absolute top-2 -right-4 w-2 h-2 bg-blue-400 rounded-full animate-sadFloat opacity-50" style="animation-delay: 1s;"></div>
          <div class="absolute -bottom-4 -left-4 w-2 h-2 bg-purple-300 rounded-full animate-sadFloat opacity-40" style="animation-delay: 1.5s;"></div>
          <div class="absolute bottom-0 right-0 w-3 h-3 bg-indigo-300 rounded-full animate-sadFloat opacity-60" style="animation-delay: 2s;"></div>
          
          <!-- Broken heart icon -->
          <div class="absolute -bottom-2 -right-2 text-red-500 text-2xl animate-pulse">
            💔
          </div>
          
          <!-- Sad cloud -->
          <div class="absolute -top-8 left-1/2 transform -translate-x-1/2 text-gray-400 text-3xl animate-sadFloat opacity-50" style="animation-delay: 0.8s;">
            ☁️
          </div>
        </div>
        
        <!-- Alert Header -->
        <div class="bg-gradient-to-r ${config.bgColor} text-white p-4 rounded-2xl mb-4 shadow-lg">
          <h3 class="text-2xl font-bold">${config.title}</h3>
          <p class="text-sm opacity-90 mt-1">${config.subtitle}</p>
        </div>
        
        <!-- Pulsing Alert Ring -->
        <div class="absolute -top-2 -right-2 w-6 h-6 bg-red-500 rounded-full animate-ping"></div>
        <div class="absolute -top-2 -right-2 w-6 h-6 bg-red-500 rounded-full"></div>
      </div>
      
      <!-- Sad Message -->
      <div class="bg-gradient-to-r from-blue-50 to-purple-50 border-2 border-blue-200 rounded-xl p-4 mb-4">
        <div class="text-center">
          <h4 class="text-lg font-bold text-blue-800 mb-2">
            😞 เสียใจด้วยนะ...
          </h4>
          <p class="text-sm text-blue-700">
            ห้องที่คุณต้องการใช้มีคนจองไปแล้ว<br>
            แต่ไม่ต้องกังวล เรามีทางเลือกอื่นให้คุณ! 💪
          </p>
        </div>
      </div>

      <!-- Conflict Details -->
      <div class="bg-gradient-to-r from-red-50 to-orange-50 border-2 ${config.borderColor} rounded-xl p-5 mb-6 text-left shadow-inner">
        <h4 class="font-bold ${config.textColor} mb-4 text-center">
          <i class="fas fa-calendar-times mr-2"></i>ห้องประชุมไม่ว่าง โปรดเลือกห้องอื่น
        </h4>
        
        <div class="grid grid-cols-1 gap-3">
          <div class="bg-white p-3 rounded-lg border-l-4 border-red-500 shadow-sm">
            <div class="flex items-center justify-between">
              <div class="flex items-center">
                <i class="fas fa-door-open ${config.iconColor} mr-3 text-lg"></i>
                <span class="font-semibold text-gray-700">ห้องประชุม:</span>
              </div>
              <span class="font-bold text-gray-800 bg-red-100 px-3 py-1 rounded-full">${conflictBooking.room}</span>
            </div>
          </div>
          
          <div class="bg-white p-3 rounded-lg border-l-4 border-orange-500 shadow-sm">
            <div class="flex items-center justify-between">
              <div class="flex items-center">
                <i class="fas fa-calendar ${config.iconColor} mr-3 text-lg"></i>
                <span class="font-semibold text-gray-700">วันที่:</span>
              </div>
              <span class="text-gray-800 bg-orange-100 px-3 py-1 rounded-full text-sm">${formattedDate}</span>
            </div>
          </div>
          
          <div class="bg-white p-3 rounded-lg border-l-4 border-yellow-500 shadow-sm">
            <div class="flex items-center justify-between">
              <div class="flex items-center">
                <i class="fas fa-clock ${config.iconColor} mr-3 text-lg"></i>
                <span class="font-semibold text-gray-700">เวลา:</span>
              </div>
              <span class="font-bold text-gray-800 bg-yellow-100 px-3 py-1 rounded-full">${conflictBooking.time}</span>
            </div>
          </div>
          
          <div class="bg-white p-3 rounded-lg border-l-4 border-blue-500 shadow-sm">
            <div class="flex items-center justify-between">
              <div class="flex items-center">
                <i class="fas fa-user ${config.iconColor} mr-3 text-lg"></i>
                <span class="font-semibold text-gray-700">ผู้จองเดิม:</span>
              </div>
              <span class="text-gray-800 bg-blue-100 px-3 py-1 rounded-full text-sm">${conflictBooking.booker}</span>
            </div>
          </div>
          
          <div class="bg-white p-3 rounded-lg border-l-4 border-green-500 shadow-sm">
            <div class="flex items-center justify-between">
              <div class="flex items-center">
                <i class="fas fa-building ${config.iconColor} mr-3 text-lg"></i>
                <span class="font-semibold text-gray-700">แผนก:</span>
              </div>
              <span class="text-gray-800 bg-green-100 px-3 py-1 rounded-full text-sm">${conflictBooking.department}</span>
            </div>
          </div>
          
          <div class="bg-white p-3 rounded-lg border-l-4 border-purple-500 shadow-sm">
            <div class="flex items-start justify-between">
              <div class="flex items-start">
                <i class="fas fa-clipboard-list ${config.iconColor} mr-3 text-lg mt-0.5"></i>
                <span class="font-semibold text-gray-700">หัวข้อ:</span>
              </div>
              <span class="text-gray-800 bg-purple-100 px-3 py-1 rounded-lg text-sm max-w-48 text-right">${conflictBooking.topic}</span>
            </div>
          </div>
        </div>
      </div>
      
      <!-- Contact Information -->
      ${conflictBooking.phone ? `
        <div class="bg-blue-50 border-2 border-blue-200 rounded-xl p-4 mb-6">
          <h5 class="font-bold text-blue-800 mb-2">
            <i class="fas fa-phone mr-2"></i>ติดต่อผู้จองเดิม
          </h5>
          <div class="flex items-center justify-center">
            <i class="fas fa-phone text-blue-600 mr-2"></i>
            <span class="font-bold text-blue-800">${conflictBooking.phone}</span>
            <button onclick="window.open('tel:${conflictBooking.phone}')" class="ml-3 bg-blue-500 text-white px-3 py-1 rounded-full text-xs hover:bg-blue-600 transition-colors">
              <i class="fas fa-phone mr-1"></i>โทร
            </button>
          </div>
        </div>
      ` : ''}
      
      <!-- Suggestions -->
      <div class="bg-gradient-to-r from-yellow-50 to-orange-50 border-2 border-yellow-200 rounded-xl p-4 mb-6">
        <h5 class="font-bold text-yellow-800 mb-3">
          <i class="fas fa-lightbulb mr-2 text-yellow-600"></i>แนวทางแก้ไข
        </h5>
        <div class="grid grid-cols-1 gap-2 text-sm">
          <div class="flex items-center text-yellow-700 bg-white p-2 rounded-lg">
            <i class="fas fa-door-open text-yellow-600 mr-2 w-4"></i>
            <span>เลือกห้องประชุมอื่น</span>
          </div>
          <div class="flex items-center text-yellow-700 bg-white p-2 rounded-lg">
            <i class="fas fa-clock text-yellow-600 mr-2 w-4"></i>
            <span>เลือกเวลาอื่น</span>
          </div>
          <div class="flex items-center text-yellow-700 bg-white p-2 rounded-lg">
            <i class="fas fa-calendar-alt text-yellow-600 mr-2 w-4"></i>
            <span>เลือกวันอื่น</span>
          </div>
          <div class="flex items-center text-yellow-700 bg-white p-2 rounded-lg">
            <i class="fas fa-handshake text-yellow-600 mr-2 w-4"></i>
            <span>ประสานงานกับผู้จองเดิม</span>
          </div>
        </div>
      </div>
      
      <!-- Action Buttons -->
      <div class="flex flex-col sm:flex-row gap-3 justify-center">
        <button onclick="this.closest('.fixed').remove(); showAvailableAlternatives('${conflictBooking.room}', '${conflictBooking.date}', '${conflictBooking.time}')" 
                class="bg-gradient-to-r from-blue-500 to-indigo-600 text-white px-6 py-3 rounded-xl hover:from-blue-600 hover:to-indigo-700 transition-all duration-300 font-semibold shadow-lg transform hover:scale-105">
          <i class="fas fa-search mr-2"></i>หาทางเลือกอื่น
        </button>
        
        <button onclick="this.closest('.fixed').remove(); checkRoomAvailability();" 
                class="bg-gradient-to-r from-green-500 to-emerald-600 text-white px-6 py-3 rounded-xl hover:from-green-600 hover:to-emerald-700 transition-all duration-300 font-semibold shadow-lg transform hover:scale-105">
          <i class="fas fa-sync-alt mr-2"></i>ตรวจสอบใหม่
        </button>
        
        <button onclick="this.closest('.fixed').remove()" 
                class="bg-gradient-to-r from-gray-500 to-gray-600 text-white px-6 py-3 rounded-xl hover:from-gray-600 hover:to-gray-700 transition-all duration-300 font-semibold shadow-lg transform hover:scale-105">
          <i class="fas fa-heart mr-2"></i>ไม่เป็นไร ลองใหม่
        </button>
      </div>
      
      <!-- Auto-close countdown -->
      <div class="mt-4 text-xs text-gray-500">
        <i class="fas fa-clock mr-1"></i>หน้าต่างนี้จะปิดอัตโนมัติใน <span id="autoCloseCountdown">20</span> วินาที
      </div>
    </div>
  `;
  
  document.body.appendChild(conflictModal);
  
  // Auto-close countdown
  let countdown = 20;
  const countdownElement = conflictModal.querySelector('#autoCloseCountdown');
  const countdownInterval = setInterval(() => {
    countdown--;
    if (countdownElement) {
      countdownElement.textContent = countdown;
    }
    
    if (countdown <= 0) {
      clearInterval(countdownInterval);
      if (document.body.contains(conflictModal)) {
        conflictModal.classList.add('animate-fadeOut');
        setTimeout(() => {
          if (document.body.contains(conflictModal)) {
            document.body.removeChild(conflictModal);
          }
        }, 300);
      }
    }
  }, 1000);
  
  // Add click outside to close
  conflictModal.addEventListener('click', function(e) {
    if (e.target === conflictModal) {
      clearInterval(countdownInterval);
      conflictModal.classList.add('animate-fadeOut');
      setTimeout(() => {
        if (document.body.contains(conflictModal)) {
          document.body.removeChild(conflictModal);
        }
      }, 300);
    }
  });
  
  // Add escape key to close
  const escapeHandler = function(e) {
    if (e.key === 'Escape') {
      clearInterval(countdownInterval);
      document.removeEventListener('keydown', escapeHandler);
      if (document.body.contains(conflictModal)) {
        conflictModal.classList.add('animate-fadeOut');
        setTimeout(() => {
          if (document.body.contains(conflictModal)) {
            document.body.removeChild(conflictModal);
          }
        }, 300);
      }
    }
  };
  document.addEventListener('keydown', escapeHandler);
}

// Enhanced highlight conflicting fields with better visual feedback
function highlightConflictFields() {
  // Highlight selected room with enhanced animation
  const selectedRoomCard = document.querySelector('.room-card.ring-2');
  if (selectedRoomCard) {
    selectedRoomCard.classList.add('ring-red-500', 'bg-red-100', 'animate-conflictShake');
    selectedRoomCard.classList.remove('ring-blue-500', 'bg-blue-100');
    
    // Add pulsing error indicator
    const errorIndicator = document.createElement('div');
    errorIndicator.className = 'absolute -top-2 -right-2 w-8 h-8 bg-red-500 text-white rounded-full flex items-center justify-center text-sm font-bold animate-ping z-10';
    errorIndicator.innerHTML = '<i class="fas fa-times"></i>';
    selectedRoomCard.style.position = 'relative';
    selectedRoomCard.appendChild(errorIndicator);
    
    setTimeout(() => {
      selectedRoomCard.classList.remove('ring-red-500', 'bg-red-100', 'animate-conflictShake');
      selectedRoomCard.classList.add('ring-blue-500', 'bg-blue-100');
      if (errorIndicator.parentNode) {
        errorIndicator.remove();
      }
    }, 3000);
  }
  
  // Highlight selected time slot with enhanced animation
  const selectedTimeSlot = document.querySelector('.time-slot-btn.bg-blue-500');
  if (selectedTimeSlot) {
    selectedTimeSlot.classList.add('bg-red-500', 'border-red-500', 'animate-conflictShake');
    selectedTimeSlot.classList.remove('bg-blue-500', 'border-blue-500');
    
    // Add error overlay
    const errorOverlay = document.createElement('div');
    errorOverlay.className = 'absolute inset-0 bg-red-500 bg-opacity-20 rounded-lg flex items-center justify-center animate-pulse';
    errorOverlay.innerHTML = '<i class="fas fa-exclamation-triangle text-red-600 text-2xl"></i>';
    selectedTimeSlot.style.position = 'relative';
    selectedTimeSlot.appendChild(errorOverlay);
    
    setTimeout(() => {
      selectedTimeSlot.classList.remove('bg-red-500', 'border-red-500', 'animate-conflictShake');
      selectedTimeSlot.classList.add('bg-blue-500', 'border-blue-500');
      if (errorOverlay.parentNode) {
        errorOverlay.remove();
      }
    }, 3000);
  }
  
  // Highlight date field with enhanced feedback
  const dateField = document.getElementById('bookingDateForm');
  if (dateField) {
    dateField.classList.add('border-red-500', 'bg-red-50', 'animate-conflictShake');
    
    // Add error message below date field
    const existingError = dateField.parentNode.querySelector('.conflict-error-message');
    if (!existingError) {
      const errorMessage = document.createElement('div');
      errorMessage.className = 'conflict-error-message text-red-600 text-sm mt-2 flex items-center animate-slideIn';
      errorMessage.innerHTML = '<i class="fas fa-exclamation-circle mr-2"></i>มีการจองซ้ำในวันและเวลานี้แล้ว';
      dateField.parentNode.appendChild(errorMessage);
      
      setTimeout(() => {
        if (errorMessage.parentNode) {
          errorMessage.remove();
        }
      }, 3000);
    }
    
    setTimeout(() => {
      dateField.classList.remove('border-red-500', 'bg-red-50', 'animate-conflictShake');
    }, 3000);
  }
  
  // Add visual feedback to form submit button
  const submitBtn = document.getElementById('submitBookingForm');
  if (submitBtn) {
    const originalText = submitBtn.innerHTML;
    submitBtn.innerHTML = '<i class="fas fa-times mr-2"></i>ไม่สามารถจองได้ - มีการจองซ้ำ';
    submitBtn.classList.add('bg-red-500', 'animate-pulse');
    submitBtn.disabled = true;
    
    setTimeout(() => {
      submitBtn.innerHTML = originalText;
      submitBtn.classList.remove('bg-red-500', 'animate-pulse');
      submitBtn.disabled = false;
    }, 3000);
  }
}

// Show available alternatives
function showAvailableAlternatives(conflictRoom, conflictDate, conflictTime) {
  const existingBookings = JSON.parse(localStorage.getItem('bookings') || '[]');
  const rooms = ['ห้อง 1A', 'ห้อง 1B', 'ห้อง 500', 'ห้อง 501', 'ห้อง 502'];
  const timeSlots = ['09:00-12:00', '13:00-16:00', '09:00-16:00'];
  
  // Find available rooms for the same date and time
  const availableRooms = rooms.filter(room => {
    if (room === conflictRoom) return false;
    return !existingBookings.some(booking => 
      booking.room === room && 
      booking.date === conflictDate && 
      booking.time === conflictTime
    );
  });
  
  // Find available time slots for the same room and date
  const availableTimes = timeSlots.filter(time => {
    if (time === conflictTime) return false;
    return !existingBookings.some(booking => 
      booking.room === conflictRoom && 
      booking.date === conflictDate && 
      booking.time === time
    );
  });
  
  const alternativeModal = document.createElement('div');
  alternativeModal.className = 'fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-50';
  alternativeModal.innerHTML = `
    <div class="bg-white rounded-2xl p-8 max-w-2xl mx-4 max-h-96 overflow-y-auto">
      <div class="flex justify-between items-center mb-6">
        <h3 class="text-xl font-bold text-blue-600">
          <i class="fas fa-search mr-2"></i>ทางเลือกที่ว่าง
        </h3>
        <button onclick="this.closest('.fixed').remove()" class="text-gray-500 hover:text-gray-700 text-xl">
          <i class="fas fa-times"></i>
        </button>
      </div>
      
      <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
        <div>
          <h4 class="font-bold text-gray-800 mb-3">
            <i class="fas fa-door-open mr-2 text-blue-600"></i>ห้องว่างในเวลาเดียวกัน
          </h4>
          <div class="text-sm text-gray-600 mb-3">
            📅 ${new Date(conflictDate).toLocaleDateString('th-TH')} | ⏰ ${conflictTime}
          </div>
          ${availableRooms.length > 0 ? `
            <div class="space-y-2">
              ${availableRooms.map(room => `
                <button onclick="selectAlternativeRoom('${room}'); this.closest('.fixed').remove();" class="w-full text-left p-3 bg-green-50 border-2 border-green-200 rounded-lg hover:bg-green-100 transition-colors">
                  <div class="font-semibold text-green-800">${room}</div>
                  <div class="text-xs text-green-600">✅ ว่าง - คลิกเพื่อเลือก</div>
                </button>
              `).join('')}
            </div>
          ` : `
            <div class="text-center py-4 text-gray-500">
              <i class="fas fa-times-circle text-2xl mb-2"></i>
              <div>ไม่มีห้องว่างในเวลานี้</div>
            </div>
          `}
        </div>
        
        <div>
          <h4 class="font-bold text-gray-800 mb-3">
            <i class="fas fa-clock mr-2 text-orange-600"></i>เวลาว่างในห้องเดียวกัน
          </h4>
          <div class="text-sm text-gray-600 mb-3">
            🏢 ${conflictRoom} | 📅 ${new Date(conflictDate).toLocaleDateString('th-TH')}
          </div>
          ${availableTimes.length > 0 ? `
            <div class="space-y-2">
              ${availableTimes.map(time => `
                <button onclick="selectAlternativeTime('${time}'); this.closest('.fixed').remove();" class="w-full text-left p-3 bg-blue-50 border-2 border-blue-200 rounded-lg hover:bg-blue-100 transition-colors">
                  <div class="font-semibold text-blue-800">${time}</div>
                  <div class="text-xs text-blue-600">✅ ว่าง - คลิกเพื่อเลือก</div>
                </button>
              `).join('')}
            </div>
          ` : `
            <div class="text-center py-4 text-gray-500">
              <i class="fas fa-times-circle text-2xl mb-2"></i>
              <div>ไม่มีเวลาว่างในห้องนี้</div>
            </div>
          `}
        </div>
      </div>
      
      <div class="flex justify-center mt-6">
        <button onclick="this.closest('.fixed').remove()" class="bg-gray-600 text-white px-6 py-2 rounded-lg hover:bg-gray-700 transition-colors">
          <i class="fas fa-times mr-2"></i>ปิด
        </button>
      </div>
    </div>
  `;
  
  document.body.appendChild(alternativeModal);
}

// Select alternative room
function selectAlternativeRoom(room) {
  // Clear previous selection
  document.querySelectorAll('.room-card').forEach(card => {
    card.classList.remove('ring-2', 'ring-blue-500', 'bg-blue-100', 'transform', 'scale-105');
  });
  
  // Find and select the new room
  const roomCard = document.querySelector(`[data-room="${room}"]`);
  if (roomCard) {
    roomCard.classList.add('ring-2', 'ring-blue-500', 'bg-blue-100', 'transform', 'scale-105');
    selectedRoom = room;
    
    // Add success animation
    roomCard.classList.add('new-booking-glow');
    setTimeout(() => {
      roomCard.classList.remove('new-booking-glow');
    }, 2000);
    
    showNotification(`✅ เลือกห้อง ${room} แล้ว กรุณาตรวจสอบข้อมูลและยืนยันการจอง`, 'success');
  }
}

// Select alternative time
function selectAlternativeTime(time) {
  // Clear previous selection
  document.querySelectorAll('.time-slot-btn').forEach(btn => {
    btn.classList.remove('bg-blue-500', 'text-white', 'border-blue-500', 'transform', 'scale-105', 'shadow-lg');
    btn.classList.add('border-gray-300', 'hover:bg-blue-50', 'hover:border-blue-300');
  });
  
  // Find and select the new time slot
  const timeSlot = document.querySelector(`[data-time="${time}"]`);
  if (timeSlot) {
    timeSlot.classList.remove('border-gray-300', 'hover:bg-blue-50', 'hover:border-blue-300');
    timeSlot.classList.add('bg-blue-500', 'text-white', 'border-blue-500', 'transform', 'scale-105', 'shadow-lg');
    selectedTime = time;
    
    // Add success animation
    timeSlot.classList.add('new-booking-glow');
    setTimeout(() => {
      timeSlot.classList.remove('new-booking-glow');
    }, 2000);
    
    showNotification(`✅ เลือกเวลา ${time} แล้ว กรุณาตรวจสอบข้อมูลและยืนยันการจอง`, 'success');
  }
}

// Notification system
function showNotification(message, type = 'info', duration = 5000) {
  const notification = document.createElement('div');
  const notificationId = 'notification-' + Date.now();
  notification.id = notificationId;
  
  const typeConfig = {
    success: { icon: 'fas fa-check-circle', bgColor: 'bg-green-500' },
    error: { icon: 'fas fa-exclamation-triangle', bgColor: 'bg-red-500' },
    warning: { icon: 'fas fa-exclamation-circle', bgColor: 'bg-yellow-500' },
    info: { icon: 'fas fa-info-circle', bgColor: 'bg-blue-500' }
  };
  
  const config = typeConfig[type] || typeConfig.info;
  
  notification.className = `fixed top-4 right-4 z-50 ${config.bgColor} text-white px-6 py-4 rounded-lg shadow-xl transform translate-x-full transition-all duration-300 max-w-sm`;
  notification.innerHTML = `
    <div class="flex items-start">
      <i class="${config.icon} mr-3 mt-0.5 text-lg"></i>
      <div class="flex-1">
        <div class="font-medium text-sm">${message}</div>
      </div>
      <button onclick="closeNotification('${notificationId}')" class="ml-4 text-white hover:text-gray-200 transition-colors">
        <i class="fas fa-times"></i>
      </button>
    </div>
  `;
  
  document.body.appendChild(notification);
  
  setTimeout(() => {
    notification.classList.remove('translate-x-full');
    notification.classList.add('translate-x-0');
  }, 100);
  
  setTimeout(() => {
    closeNotification(notificationId);
  }, duration);
}

function closeNotification(notificationId) {
  const notification = document.getElementById(notificationId);
  if (notification) {
    notification.classList.add('translate-x-full');
    notification.classList.remove('translate-x-0');
    
    setTimeout(() => {
      if (document.body.contains(notification)) {
        document.body.removeChild(notification);
      }
    }, 300);
  }
}

// Update footer information
function updateFooterInfo() {
  const lastUpdateElement = document.getElementById('lastUpdate');
  const totalUsersElement = document.getElementById('totalUsers');
  
  if (lastUpdateElement) {
    const now = new Date();
    const formattedDate = now.toLocaleDateString('th-TH', {
      day: 'numeric',
      month: 'short',
      year: 'numeric'
    });
    lastUpdateElement.textContent = formattedDate;
  }
  
  if (totalUsersElement) {
    // Calculate dynamic user count based on bookings
    const bookings = JSON.parse(localStorage.getItem('bookings') || '[]');
    const uniqueUsers = new Set(bookings.map(b => b.booker)).size;
    const baseUsers = 150;
    const totalUsers = baseUsers + uniqueUsers;
    totalUsersElement.textContent = `${totalUsers}+`;
  }
}

// Setup real-time form validation
function setupFormValidation() {
  const formFields = [
    { id: 'bookerNameForm', type: 'text', required: true },
    { id: 'departmentForm', type: 'select', required: true },
    { id: 'meetingTopicForm', type: 'text', required: true },
    { id: 'attendeesForm', type: 'number', required: true, min: 1, max: 50 },
    { id: 'phoneForm', type: 'tel', required: false },
    { id: 'bookingDateForm', type: 'date', required: true }
  ];
  
  formFields.forEach(field => {
    const element = document.getElementById(field.id);
    if (!element) return;
    
    // Add input event listener for real-time validation
    element.addEventListener('input', function() {
      validateField(element, field);
    });
    
    // Add blur event for final validation
    element.addEventListener('blur', function() {
      validateField(element, field);
    });
  });
  
  // Custom time validation
  const startTime = document.getElementById('startTimeForm');
  const endTime = document.getElementById('endTimeForm');
  
  if (startTime && endTime) {
    [startTime, endTime].forEach(timeInput => {
      timeInput.addEventListener('change', function() {
        validateTimeRange();
      });
    });
  }
}

function validateField(element, fieldConfig) {
  const value = element.value.trim();
  const isValid = validateFieldValue(value, fieldConfig);
  
  // Remove previous validation classes
  element.classList.remove('border-green-500', 'border-red-500', 'bg-green-50', 'bg-red-50');
  
  // Remove existing validation message
  const existingMessage = element.parentNode.querySelector('.validation-message');
  if (existingMessage) {
    existingMessage.remove();
  }
  
  if (fieldConfig.required && !value) {
    // Empty required field
    element.classList.add('border-gray-300');
    return;
  }
  
  if (value && !isValid.valid) {
    // Invalid value
    element.classList.add('border-red-500', 'bg-red-50');
    showValidationMessage(element, isValid.message, 'error');
  } else if (value) {
    // Valid value
    element.classList.add('border-green-500', 'bg-green-50');
    showValidationMessage(element, '✓ ถูกต้อง', 'success');
  }
}

function validateFieldValue(value, fieldConfig) {
  if (fieldConfig.type === 'text' && value.length < 2) {
    return { valid: false, message: 'กรุณากรอกอย่างน้อย 2 ตัวอักษร' };
  }
  
  if (fieldConfig.type === 'number') {
    const num = parseInt(value);
    if (isNaN(num)) {
      return { valid: false, message: 'กรุณากรอกตัวเลขเท่านั้น' };
    }
    if (fieldConfig.min && num < fieldConfig.min) {
      return { valid: false, message: `ต้องไม่น้อยกว่า ${fieldConfig.min}` };
    }
    if (fieldConfig.max && num > fieldConfig.max) {
      return { valid: false, message: `ต้องไม่เกิน ${fieldConfig.max}` };
    }
  }
  
  if (fieldConfig.type === 'tel' && value) {
    const phoneRegex = /^[0-9-+().\s]+$/;
    if (!phoneRegex.test(value)) {
      return { valid: false, message: 'รูปแบบเบอร์โทรไม่ถูกต้อง' };
    }
  }
  
  if (fieldConfig.type === 'date') {
    const selectedDate = new Date(value);
    const today = new Date();
    today.setHours(0, 0, 0, 0);
    
    if (selectedDate < today) {
      return { valid: false, message: 'ไม่สามารถจองย้อนหลังได้' };
    }
  }
  
  return { valid: true, message: '✓ ถูกต้อง' };
}

function showValidationMessage(element, message, type) {
  const messageDiv = document.createElement('div');
  messageDiv.className = `validation-message text-xs mt-1 ${type === 'error' ? 'text-red-600' : 'text-green-600'}`;
  messageDiv.textContent = message;
  
  element.parentNode.appendChild(messageDiv);
  
  // Auto-remove success messages after 3 seconds
  if (type === 'success') {
    setTimeout(() => {
      if (messageDiv.parentNode) {
        messageDiv.remove();
      }
    }, 3000);
  }
}

function validateTimeRange() {
  const startTime = document.getElementById('startTimeForm');
  const endTime = document.getElementById('endTimeForm');
  
  if (!startTime || !endTime || !startTime.value || !endTime.value) return;
  
  const start = startTime.value;
  const end = endTime.value;
  
  // Remove previous validation
  [startTime, endTime].forEach(input => {
    input.classList.remove('border-red-500', 'border-green-500', 'bg-red-50', 'bg-green-50');
    const message = input.parentNode.querySelector('.validation-message');
    if (message) message.remove();
  });
  
  // Validate working hours (08:00-18:00)
  if (start < '08:00' || end > '18:00') {
    [startTime, endTime].forEach(input => {
      input.classList.add('border-red-500', 'bg-red-50');
    });
    showValidationMessage(startTime, 'เวลาทำการ 08:00-18:00 เท่านั้น', 'error');
    return;
  }
  
  // Validate time range
  if (start >= end) {
    [startTime, endTime].forEach(input => {
      input.classList.add('border-red-500', 'bg-red-50');
    });
    showValidationMessage(startTime, 'เวลาเริ่มต้องน้อยกว่าเวลาสิ้นสุด', 'error');
    return;
  }
  
  // Valid time range
  [startTime, endTime].forEach(input => {
    input.classList.add('border-green-500', 'bg-green-50');
  });
  showValidationMessage(startTime, `✓ ช่วงเวลา ${start}-${end} ถูกต้อง`, 'success');
  
  // Update selected time for availability check
  selectedTime = `${start}-${end}`;
  checkRoomAvailability();
}

// Show day bookings function
function showDayBookings(dateStr, dayBookings) {
  const formattedDate = new Date(dateStr).toLocaleDateString('th-TH', {
    year: 'numeric',
    month: 'long',
    day: 'numeric',
    weekday: 'long'
  });
  
  if (dayBookings.length === 0) {
    showNotification(`📅 ${formattedDate}\n\nไม่มีการจองในวันนี้`, 'info', 3000);
    return;
  }
  
  const bookingDetails = dayBookings.map(booking => 
    `🏢 ${booking.room} | ⏰ ${booking.time}\n📋 ${booking.topic}\n👤 ${booking.booker} (${booking.department})`
  ).join('\n\n');
  
  const message = `📅 ${formattedDate}\n\n📊 การจองทั้งหมด: ${dayBookings.length} รายการ\n\n${bookingDetails}`;
  
  // Create custom modal for day details
  const modal = document.createElement('div');
  modal.className = 'fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-50';
  modal.innerHTML = `
    <div class="bg-white rounded-2xl p-6 max-w-2xl mx-4 max-h-96 overflow-y-auto">
      <div class="flex justify-between items-center mb-4">
        <h3 class="text-xl font-bold text-gray-800">
          <i class="fas fa-calendar-day mr-2 text-blue-600"></i>${formattedDate}
        </h3>
        <button onclick="this.closest('.fixed').remove()" class="text-gray-500 hover:text-gray-700 text-xl">
          <i class="fas fa-times"></i>
        </button>
      </div>
      
      <div class="space-y-3">
        ${dayBookings.map(booking => {
          const roomColors = {
            'ห้อง 1A': 'from-red-50 to-red-100 border-red-300',
            'ห้อง 1B': 'from-orange-50 to-orange-100 border-orange-300',
            'ห้อง 500': 'from-blue-50 to-blue-100 border-blue-300',
            'ห้อง 501': 'from-green-50 to-green-100 border-green-300',
            'ห้อง 502': 'from-purple-50 to-purple-100 border-purple-300'
          };
          const roomColor = roomColors[booking.room] || 'from-gray-50 to-gray-100 border-gray-300';
          
          return `
            <div class="bg-gradient-to-r ${roomColor} p-4 rounded-lg border-2">
              <div class="flex justify-between items-start">
                <div class="flex-1">
                  <h4 class="font-bold text-gray-800 mb-2">${booking.topic}</h4>
                  <div class="grid grid-cols-2 gap-2 text-sm">
                    <div><i class="fas fa-door-open text-blue-600 mr-1"></i>${booking.room}</div>
                    <div><i class="fas fa-clock text-green-600 mr-1"></i>${booking.time}</div>
                    <div><i class="fas fa-user text-purple-600 mr-1"></i>${booking.booker}</div>
                    <div><i class="fas fa-building text-teal-600 mr-1"></i>${booking.department}</div>
                  </div>
                  ${booking.equipment && booking.equipment.length > 0 ? `
                    <div class="mt-2">
                      <div class="flex flex-wrap gap-1">
                        ${booking.equipment.map(eq => `
                          <span class="bg-white bg-opacity-70 text-xs px-2 py-1 rounded-full text-gray-700">
                            ${eq}
                          </span>
                        `).join('')}
                      </div>
                    </div>
                  ` : ''}
                </div>
                <div class="admin-controls ${isAdmin ? '' : 'hidden'} flex flex-col space-y-1 ml-4">
                  <button onclick="editBooking(${booking.id}); this.closest('.fixed').remove();" class="text-xs bg-blue-500 text-white px-2 py-1 rounded hover:bg-blue-600">
                    <i class="fas fa-edit mr-1"></i>แก้ไข
                  </button>
                  <button onclick="deleteAdminBooking(${booking.id}); this.closest('.fixed').remove();" class="text-xs bg-red-500 text-white px-2 py-1 rounded hover:bg-red-600">
                    <i class="fas fa-trash mr-1"></i>ลบ
                  </button>
                </div>
              </div>
            </div>
          `;
        }).join('')}
      </div>
      
      <div class="flex justify-center mt-6">
        <button onclick="this.closest('.fixed').remove()" class="bg-gray-600 text-white px-6 py-2 rounded-lg hover:bg-gray-700 transition-colors">
          <i class="fas fa-times mr-2"></i>ปิด
        </button>
      </div>
    </div>
  `;
  
  document.body.appendChild(modal);
  
  // Auto remove after 10 seconds
  setTimeout(() => {
    if (document.body.contains(modal)) {
      document.body.removeChild(modal);
    }
  }, 10000);
}

// Edit booking functionality
function editBooking(id) {
  if (!isAdmin) {
    showNotification('❌ คุณไม่มีสิทธิ์ในการแก้ไขการจอง', 'error');
    return;
  }
  
  // Convert to multiple formats for comparison
  const targetIdStr = String(id);
  const targetIdNum = parseInt(id);
  
  const bookings = JSON.parse(localStorage.getItem('bookings') || '[]');
  
  console.log('=== EDIT BOOKING DEBUG ===');
  console.log('Target ID (string):', targetIdStr);
  console.log('Target ID (number):', targetIdNum);
  console.log('All bookings:', bookings.map(b => ({ 
    id: b.id, 
    idType: typeof b.id, 
    idStr: String(b.id), 
    idNum: parseInt(b.id),
    topic: b.topic 
  })));
  
  // Find booking using multiple comparison methods
  const booking = bookings.find(b => 
    String(b.id) === targetIdStr || 
    parseInt(b.id) === targetIdNum ||
    b.id === id ||
    b.id == id
  );
  
  if (!booking) {
    console.log('❌ Booking not found for edit with any comparison method');
    showNotification('❌ ไม่พบข้อมูลการจอง (ID: ' + id + ')', 'error');
    return;
  }
  
  console.log('✅ Found booking for edit:', booking.topic, 'with ID:', booking.id);
  
  // Close any open modals
  document.getElementById('adminMenuModal').classList.add('hidden');
  document.getElementById('adminManageBookingsModal').classList.add('hidden');
  
  // Open edit modal
  document.getElementById('adminAddBookingModal').classList.remove('hidden');
  
  // Populate form with existing data
  document.getElementById('adminRoom').value = booking.room;
  document.getElementById('adminDate').value = booking.date;
  
  // Parse time
  const timeParts = booking.time.split('-');
  document.getElementById('adminStartTime').value = timeParts[0];
  document.getElementById('adminEndTime').value = timeParts[1];
  
  document.getElementById('adminBooker').value = booking.booker;
  document.getElementById('adminDepartment').value = booking.department;
  document.getElementById('adminTopic').value = booking.topic;
  document.getElementById('adminAttendees').value = booking.attendees;
  document.getElementById('adminPhone').value = booking.phone || '';
  
  // Set equipment checkboxes
  document.querySelectorAll('.admin-equipment-checkbox').forEach(checkbox => {
    checkbox.checked = booking.equipment && booking.equipment.includes(checkbox.value);
  });
  
  // Change form title and button
  const modalTitle = document.querySelector('#adminAddBookingModal h3');
  modalTitle.innerHTML = '<i class="fas fa-edit mr-2 text-blue-600"></i>แก้ไขการจอง (Admin)';
  
  const submitBtn = document.querySelector('#adminAddBookingForm button[type="submit"]');
  submitBtn.innerHTML = '<i class="fas fa-save mr-2"></i>บันทึกการแก้ไข';
  
  // Store the original booking ID for update (use the actual ID from the found booking)
  document.getElementById('adminAddBookingForm').dataset.editingId = booking.id;
  
  console.log('Stored editing ID:', booking.id);
}

// View booking details function
function viewBookingDetails(id) {
  console.log('=== VIEW BOOKING DETAILS ===');
  console.log('Target ID:', id, 'Type:', typeof id);
  
  const bookings = JSON.parse(localStorage.getItem('bookings') || '[]');
  const booking = bookings.find(b => 
    String(b.id) === String(id) || 
    parseInt(b.id) === parseInt(id) ||
    b.id === id ||
    b.id == id
  );
  
  if (!booking) {
    showNotification('❌ ไม่พบข้อมูลการจอง', 'error');
    return;
  }
  
  const formattedDate = new Date(booking.date).toLocaleDateString('th-TH', {
    year: 'numeric',
    month: 'long',
    day: 'numeric',
    weekday: 'long'
  });
  
  const formattedCreatedAt = booking.createdAt ? 
    new Date(booking.createdAt).toLocaleString('th-TH', {
      year: 'numeric',
      month: 'long',
      day: 'numeric',
      hour: '2-digit',
      minute: '2-digit'
    }) : 'ไม่ระบุ';
  
  const formattedUpdatedAt = booking.updatedAt ? 
    new Date(booking.updatedAt).toLocaleString('th-TH', {
      year: 'numeric',
      month: 'long',
      day: 'numeric',
      hour: '2-digit',
      minute: '2-digit'
    }) : null;
  
  // Create detailed view modal
  const detailModal = document.createElement('div');
  detailModal.className = 'fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-50';
  detailModal.innerHTML = `
    <div class="bg-white rounded-2xl p-8 max-w-4xl mx-4 w-full max-h-screen overflow-y-auto">
      <div class="flex justify-between items-center mb-6">
        <div class="flex items-center">
          <div class="bg-gradient-to-r from-green-500 to-emerald-600 p-3 rounded-full mr-4">
            <i class="fas fa-eye text-2xl text-white"></i>
          </div>
          <div>
            <h3 class="text-2xl font-bold text-gray-800">รายละเอียดการจอง</h3>
            <p class="text-sm text-gray-600">ข้อมูลการจองห้องประชุมแบบละเอียด</p>
          </div>
        </div>
        <button onclick="this.closest('.fixed').remove()" class="text-gray-500 hover:text-gray-700 text-2xl">
          <i class="fas fa-times"></i>
        </button>
      </div>

      <!-- Booking Status -->
      <div class="bg-gradient-to-r from-green-50 to-emerald-50 border-2 border-green-200 rounded-xl p-4 mb-6">
        <div class="flex items-center justify-between">
          <div class="flex items-center">
            <i class="fas fa-check-circle text-2xl text-green-600 mr-3"></i>
            <div>
              <h4 class="text-lg font-bold text-green-800">สถานะการจอง</h4>
              <p class="text-sm text-green-700">${booking.status === 'confirmed' ? 'ยืนยันการจองแล้ว' : 'รอการยืนยัน'}</p>
            </div>
          </div>
          <div class="text-right">
            <div class="text-xs text-gray-600">รหัสการจอง</div>
            <div class="text-lg font-bold text-gray-800 font-mono">#${booking.id}</div>
          </div>
        </div>
      </div>

      <!-- Main Information -->
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-6 mb-6">
        <!-- Left Column -->
        <div class="space-y-6">
          <!-- Meeting Details -->
          <div class="bg-blue-50 border-2 border-blue-200 rounded-xl p-5">
            <h4 class="text-lg font-bold text-blue-800 mb-4">
              <i class="fas fa-clipboard-list mr-2"></i>ข้อมูลการประชุม
            </h4>
            <div class="space-y-3">
              <div class="flex items-start">
                <i class="fas fa-bookmark text-blue-600 mr-3 w-5 mt-1"></i>
                <div>
                  <span class="text-sm font-semibold text-gray-700">หัวข้อการประชุม:</span>
                  <div class="text-lg font-bold text-gray-800 mt-1">${booking.topic}</div>
                </div>
              </div>
              <div class="flex items-center">
                <i class="fas fa-users text-purple-600 mr-3 w-5"></i>
                <span class="text-sm font-semibold text-gray-700">จำนวนผู้เข้าร่วม:</span>
                <span class="ml-2 text-lg font-bold text-purple-800">${booking.attendees} คน</span>
              </div>
            </div>
          </div>

          <!-- Location & Time -->
          <div class="bg-orange-50 border-2 border-orange-200 rounded-xl p-5">
            <h4 class="text-lg font-bold text-orange-800 mb-4">
              <i class="fas fa-map-marker-alt mr-2"></i>สถานที่และเวลา
            </h4>
            <div class="space-y-3">
              <div class="flex items-center">
                <i class="fas fa-door-open text-orange-600 mr-3 w-5"></i>
                <span class="text-sm font-semibold text-gray-700">ห้องประชุม:</span>
                <span class="ml-2 text-lg font-bold text-orange-800">${booking.room}</span>
              </div>
              <div class="flex items-center">
                <i class="fas fa-calendar text-green-600 mr-3 w-5"></i>
                <span class="text-sm font-semibold text-gray-700">วันที่:</span>
                <span class="ml-2 text-gray-800">${formattedDate}</span>
              </div>
              <div class="flex items-center">
                <i class="fas fa-clock text-red-600 mr-3 w-5"></i>
                <span class="text-sm font-semibold text-gray-700">เวลา:</span>
                <span class="ml-2 text-lg font-bold text-red-800">${booking.time}</span>
              </div>
            </div>
          </div>
        </div>

        <!-- Right Column -->
        <div class="space-y-6">
          <!-- Contact Information -->
          <div class="bg-purple-50 border-2 border-purple-200 rounded-xl p-5">
            <h4 class="text-lg font-bold text-purple-800 mb-4">
              <i class="fas fa-address-card mr-2"></i>ข้อมูลผู้จอง
            </h4>
            <div class="space-y-3">
              <div class="flex items-center">
                <i class="fas fa-user text-purple-600 mr-3 w-5"></i>
                <span class="text-sm font-semibold text-gray-700">ชื่อผู้จอง:</span>
                <span class="ml-2 text-lg font-bold text-gray-800">${booking.booker}</span>
              </div>
              <div class="flex items-center">
                <i class="fas fa-building text-teal-600 mr-3 w-5"></i>
                <span class="text-sm font-semibold text-gray-700">แผนก:</span>
                <span class="ml-2 text-gray-800">${booking.department}</span>
              </div>
              ${booking.phone ? `
                <div class="flex items-center">
                  <i class="fas fa-phone text-blue-600 mr-3 w-5"></i>
                  <span class="text-sm font-semibold text-gray-700">เบอร์โทรศัพท์:</span>
                  <span class="ml-2 text-gray-800">${booking.phone}</span>
                </div>
              ` : ''}
            </div>
          </div>

          <!-- Equipment -->
          ${booking.equipment && booking.equipment.length > 0 ? `
            <div class="bg-gray-50 border-2 border-gray-200 rounded-xl p-5">
              <h4 class="text-lg font-bold text-gray-800 mb-4">
                <i class="fas fa-tools mr-2"></i>อุปกรณ์ที่ต้องการ
              </h4>
              <div class="grid grid-cols-1 gap-2">
                ${booking.equipment.map(eq => `
                  <div class="flex items-center bg-white p-3 rounded-lg border">
                    <i class="fas fa-check-circle text-green-600 mr-3"></i>
                    <span class="text-gray-800 font-medium">${eq}</span>
                  </div>
                `).join('')}
              </div>
            </div>
          ` : `
            <div class="bg-gray-50 border-2 border-gray-200 rounded-xl p-5">
              <h4 class="text-lg font-bold text-gray-800 mb-4">
                <i class="fas fa-tools mr-2"></i>อุปกรณ์ที่ต้องการ
              </h4>
              <div class="text-center py-4">
                <i class="fas fa-times-circle text-gray-400 text-2xl mb-2"></i>
                <p class="text-gray-500">ไม่ต้องการอุปกรณ์เพิ่มเติม</p>
              </div>
            </div>
          `}
        </div>
      </div>

      <!-- System Information -->
      <div class="bg-gray-50 border-2 border-gray-200 rounded-xl p-5 mb-6">
        <h4 class="text-lg font-bold text-gray-800 mb-4">
          <i class="fas fa-info-circle mr-2"></i>ข้อมูลระบบ
        </h4>
        <div class="grid grid-cols-1 md:grid-cols-2 gap-4 text-sm">
          <div class="flex items-center">
            <i class="fas fa-calendar-plus text-green-600 mr-3 w-5"></i>
            <span class="font-semibold text-gray-700">สร้างเมื่อ:</span>
            <span class="ml-2 text-gray-800">${formattedCreatedAt}</span>
          </div>
          ${formattedUpdatedAt ? `
            <div class="flex items-center">
              <i class="fas fa-edit text-blue-600 mr-3 w-5"></i>
              <span class="font-semibold text-gray-700">แก้ไขล่าสุด:</span>
              <span class="ml-2 text-gray-800">${formattedUpdatedAt}</span>
            </div>
          ` : ''}
          <div class="flex items-center">
            <i class="fas fa-user-shield text-purple-600 mr-3 w-5"></i>
            <span class="font-semibold text-gray-700">สร้างโดย:</span>
            <span class="ml-2 text-gray-800">${booking.createdBy || 'ผู้ใช้งาน'}</span>
          </div>
          ${booking.updatedBy ? `
            <div class="flex items-center">
              <i class="fas fa-user-edit text-orange-600 mr-3 w-5"></i>
              <span class="font-semibold text-gray-700">แก้ไขโดย:</span>
              <span class="ml-2 text-gray-800">${booking.updatedBy}</span>
            </div>
          ` : ''}
        </div>
      </div>

      <!-- Action Buttons -->
      <div class="flex flex-wrap gap-3 justify-center">
        <button onclick="editBooking(${booking.id}); this.closest('.fixed').remove();" class="bg-blue-500 text-white px-6 py-3 rounded-lg hover:bg-blue-600 transition-colors font-medium shadow-lg">
          <i class="fas fa-edit mr-2"></i>แก้ไขการจอง
        </button>
        <button onclick="deleteAdminBooking(${booking.id}); this.closest('.fixed').remove();" class="bg-red-500 text-white px-6 py-3 rounded-lg hover:bg-red-600 transition-colors font-medium shadow-lg">
          <i class="fas fa-trash mr-2"></i>ลบการจอง
        </button>
        <button onclick="printBookingDetails(${booking.id})" class="bg-green-500 text-white px-6 py-3 rounded-lg hover:bg-green-600 transition-colors font-medium shadow-lg">
          <i class="fas fa-print mr-2"></i>พิมพ์รายละเอียด
        </button>
        <button onclick="this.closest('.fixed').remove()" class="bg-gray-600 text-white px-6 py-3 rounded-lg hover:bg-gray-700 transition-colors font-medium shadow-lg">
          <i class="fas fa-times mr-2"></i>ปิด
        </button>
      </div>
    </div>
  `;
  
  document.body.appendChild(detailModal);
  
  // Auto remove after 30 seconds
  setTimeout(() => {
    if (document.body.contains(detailModal)) {
      document.body.removeChild(detailModal);
    }
  }, 30000);
}

// Generate enhanced confetti and fireworks animation
function generateConfetti() {
  const confettiContainer = document.querySelector('.confetti-container');
  const fireworksContainer = document.querySelector('.fireworks-container');
  
  if (!confettiContainer) return;
  
  // Clear existing effects
  confettiContainer.innerHTML = '';
  if (fireworksContainer) fireworksContainer.innerHTML = '';
  
  const colors = ['#ff6b6b', '#4ecdc4', '#45b7d1', '#96ceb4', '#feca57', '#ff9ff3', '#54a0ff', '#ffd700', '#ff4757', '#2ed573'];
  const shapes = ['square', 'circle', 'triangle', 'diamond', 'star'];
  
  // Create enhanced confetti pieces (100 pieces for more dramatic effect)
  for (let i = 0; i < 100; i++) {
    const confetti = document.createElement('div');
    const color = colors[Math.floor(Math.random() * colors.length)];
    const shape = shapes[Math.floor(Math.random() * shapes.length)];
    const size = Math.random() * 12 + 6; // 6-18px (larger)
    const left = Math.random() * 100;
    const animationDuration = Math.random() * 3 + 3; // 3-6s (longer)
    const delay = Math.random() * 3; // 0-3s delay
    
    confetti.className = 'confetti-piece';
    confetti.style.left = left + '%';
    confetti.style.backgroundColor = color;
    confetti.style.width = size + 'px';
    confetti.style.height = size + 'px';
    confetti.style.animationDuration = animationDuration + 's';
    confetti.style.animationDelay = delay + 's';
    confetti.style.zIndex = '1000';
    
    // Enhanced shapes
    if (shape === 'circle') {
      confetti.style.borderRadius = '50%';
    } else if (shape === 'triangle') {
      confetti.style.width = '0';
      confetti.style.height = '0';
      confetti.style.backgroundColor = 'transparent';
      confetti.style.borderLeft = (size/2) + 'px solid transparent';
      confetti.style.borderRight = (size/2) + 'px solid transparent';
      confetti.style.borderBottom = size + 'px solid ' + color;
    } else if (shape === 'diamond') {
      confetti.style.transform = 'rotate(45deg)';
      confetti.style.borderRadius = '20%';
    } else if (shape === 'star') {
      confetti.innerHTML = '★';
      confetti.style.backgroundColor = 'transparent';
      confetti.style.color = color;
      confetti.style.fontSize = size + 'px';
      confetti.style.textAlign = 'center';
      confetti.style.lineHeight = '1';
    }
    
    confettiContainer.appendChild(confetti);
  }
  
  // Generate fireworks
  if (fireworksContainer) {
    generateFireworks(fireworksContainer, colors);
  }
  
  // Remove effects after animation
  setTimeout(() => {
    confettiContainer.innerHTML = '';
    if (fireworksContainer) fireworksContainer.innerHTML = '';
  }, 8000);
}

// Generate fireworks effect
function generateFireworks(container, colors) {
  const fireworkPositions = [
    { x: 20, y: 30 },
    { x: 80, y: 25 },
    { x: 50, y: 40 },
    { x: 30, y: 60 },
    { x: 70, y: 55 }
  ];
  
  fireworkPositions.forEach((pos, index) => {
    setTimeout(() => {
      createFirework(container, pos.x, pos.y, colors);
    }, index * 800);
  });
}

function createFirework(container, x, y, colors) {
  const particleCount = 20;
  const color = colors[Math.floor(Math.random() * colors.length)];
  
  for (let i = 0; i < particleCount; i++) {
    const particle = document.createElement('div');
    particle.className = 'firework';
    particle.style.left = x + '%';
    particle.style.top = y + '%';
    particle.style.backgroundColor = color;
    
    const angle = (i / particleCount) * 2 * Math.PI;
    const velocity = Math.random() * 100 + 50;
    const vx = Math.cos(angle) * velocity;
    const vy = Math.sin(angle) * velocity;
    
    particle.style.setProperty('--vx', vx + 'px');
    particle.style.setProperty('--vy', vy + 'px');
    
    // Enhanced firework animation
    particle.style.animation = `fireworkParticle 2s ease-out forwards`;
    
    container.appendChild(particle);
    
    // Remove particle after animation
    setTimeout(() => {
      if (particle.parentNode) {
        particle.parentNode.removeChild(particle);
      }
    }, 2000);
  }
}

// Add firework particle animation to CSS (will be injected)
const fireworkStyle = document.createElement('style');
fireworkStyle.textContent = `
  @keyframes fireworkParticle {
    0% {
      transform: translate(0, 0) scale(1);
      opacity: 1;
    }
    100% {
      transform: translate(var(--vx, 0), var(--vy, 0)) scale(0);
      opacity: 0;
    }
  }
`;
document.head.appendChild(fireworkStyle);

// Start count-up animations
function startCountUpAnimations() {
  const countUpElements = document.querySelectorAll('.animate-countUp');
  
  countUpElements.forEach(element => {
    const target = parseInt(element.getAttribute('data-target'));
    const suffix = element.getAttribute('data-suffix') || '';
    let current = 0;
    const increment = target / 30; // 30 steps
    const duration = 1500; // 1.5 seconds
    const stepTime = duration / 30;
    
    const timer = setInterval(() => {
      current += increment;
      if (current >= target) {
        current = target;
        clearInterval(timer);
      }
      element.textContent = Math.floor(current) + suffix;
    }, stepTime);
  });
}

// Enhanced success modal with sound effect
function playSuccessSound() {
  try {
    // Create a pleasant success sound using Web Audio API
    const audioContext = new (window.AudioContext || window.webkitAudioContext)();
    
    // Create a sequence of pleasant tones
    const frequencies = [523.25, 659.25, 783.99]; // C5, E5, G5 (major chord)
    
    frequencies.forEach((freq, index) => {
      setTimeout(() => {
        const oscillator = audioContext.createOscillator();
        const gainNode = audioContext.createGain();
        
        oscillator.connect(gainNode);
        gainNode.connect(audioContext.destination);
        
        oscillator.frequency.setValueAtTime(freq, audioContext.currentTime);
        oscillator.type = 'sine';
        
        // Envelope for smooth sound
        gainNode.gain.setValueAtTime(0, audioContext.currentTime);
        gainNode.gain.linearRampToValueAtTime(0.1, audioContext.currentTime + 0.1);
        gainNode.gain.exponentialRampToValueAtTime(0.01, audioContext.currentTime + 0.5);
        
        oscillator.start(audioContext.currentTime);
        oscillator.stop(audioContext.currentTime + 0.5);
      }, index * 150);
    });
    
  } catch (error) {
    console.log('Audio not supported:', error);
  }
}

// Enhanced close modal with fade out
function closeSuccessModal() {
  const modal = document.getElementById('successModal');
  const modalContent = modal.querySelector('.bg-white');
  
  // Add fade out animation
  modalContent.style.animation = 'successBounce 0.5s ease-in reverse';
  modal.style.animation = 'fadeOut 0.5s ease-out';
  
  setTimeout(() => {
    modal.classList.add('hidden');
    modal.style.animation = '';
    modalContent.style.animation = '';
    
    // Clear confetti
    const confettiContainer = document.querySelector('.confetti-container');
    if (confettiContainer) {
      confettiContainer.innerHTML = '';
    }
  }, 500);
}

// Print booking details function
function printBookingDetails(id) {
  const bookings = JSON.parse(localStorage.getItem('bookings') || '[]');
  const booking = bookings.find(b => 
    String(b.id) === String(id) || 
    parseInt(b.id) === parseInt(id) ||
    b.id === id ||
    b.id == id
  );
  
  if (!booking) {
    showNotification('❌ ไม่พบข้อมูลการจอง', 'error');
    return;
  }
  
  const formattedDate = new Date(booking.date).toLocaleDateString('th-TH', {
    year: 'numeric',
    month: 'long',
    day: 'numeric',
    weekday: 'long'
  });
  
  const printContent = `
    <html>
    <head>
      <title>รายละเอียดการจอง #${booking.id}</title>
      <style>
        body { font-family: 'Sarabun', Arial, sans-serif; margin: 20px; }
        .header { text-align: center; border-bottom: 2px solid #333; padding-bottom: 20px; margin-bottom: 30px; }
        .section { margin-bottom: 20px; }
        .label { font-weight: bold; color: #333; }
        .value { margin-left: 10px; }
        .equipment-list { list-style-type: none; padding-left: 0; }
        .equipment-list li { padding: 5px 0; border-bottom: 1px solid #eee; }
        .footer { margin-top: 40px; text-align: center; font-size: 12px; color: #666; }
      </style>
    </head>
    <body>
      <div class="header">
        <h1>ใบยืนยันการจองห้องประชุม</h1>
        <h2>กลุ่มบริษัท TAISIN</h2>
        <p>รหัสการจอง: #${booking.id}</p>
      </div>
      
      <div class="section">
        <h3>ข้อมูลการประชุม</h3>
        <p><span class="label">หัวข้อการประชุม:</span><span class="value">${booking.topic}</span></p>
        <p><span class="label">ห้องประชุม:</span><span class="value">${booking.room}</span></p>
        <p><span class="label">วันที่:</span><span class="value">${formattedDate}</span></p>
        <p><span class="label">เวลา:</span><span class="value">${booking.time}</span></p>
        <p><span class="label">จำนวนผู้เข้าร่วม:</span><span class="value">${booking.attendees} คน</span></p>
      </div>
      
      <div class="section">
        <h3>ข้อมูลผู้จอง</h3>
        <p><span class="label">ชื่อผู้จอง:</span><span class="value">${booking.booker}</span></p>
        <p><span class="label">แผนก:</span><span class="value">${booking.department}</span></p>
        ${booking.phone ? `<p><span class="label">เบอร์โทรศัพท์:</span><span class="value">${booking.phone}</span></p>` : ''}
      </div>
      
      ${booking.equipment && booking.equipment.length > 0 ? `
        <div class="section">
          <h3>อุปกรณ์ที่ต้องการ</h3>
          <ul class="equipment-list">
            ${booking.equipment.map(eq => `<li>✓ ${eq}</li>`).join('')}
          </ul>
        </div>
      ` : ''}
      
      <div class="footer">
        <p>พิมพ์เมื่อ: ${new Date().toLocaleString('th-TH')}</p>
        <p>ระบบการจองห้องประชุม TAISIN GROUP</p>
      </div>
    </body>
    </html>
  `;
  
  const printWindow = window.open('', '_blank');
  printWindow.document.write(printContent);
  printWindow.document.close();
  printWindow.print();
  
  showNotification('📄 เปิดหน้าต่างพิมพ์แล้ว', 'success', 3000);
}

// Confirm delete booking function for today's bookings section
function confirmDeleteBooking(id) {
  if (!isAdmin) {
    showNotification('❌ คุณไม่มีสิทธิ์ในการลบการจอง', 'error');
    return;
  }
  
  console.log('=== CONFIRM DELETE BOOKING ===');
  console.log('confirmDeleteBooking called with ID:', id, 'Type:', typeof id);
  
  // Call the main delete function
  deleteAdminBooking(id);
}

function deleteBooking(id) {
  if (!isAdmin) {
    showNotification('❌ คุณไม่มีสิทธิ์ในการลบการจอง', 'error');
    return;
  }
  
  console.log('=== DELETE BOOKING WRAPPER ===');
  console.log('deleteBooking called with ID:', id, 'Type:', typeof id);
  
  // Call the main delete function
  deleteAdminBooking(id);
}

// Stats management functions
function editStats() {
  console.log('editStats function called, isAdmin:', isAdmin);
  
  if (!isAdmin) {
    showNotification('❌ คุณไม่มีสิทธิ์ในการแก้ไขสถิติ', 'error');
    return;
  }
  
  console.log('✅ Admin verified, opening edit stats modal');
  
  const currentStats = JSON.parse(localStorage.getItem('stats') || '{"todayCount": 2, "weekCount": 8, "popularRoom": "ห้อง 500"}');
  console.log('Current stats:', currentStats);
  
  const editModal = document.createElement('div');
  editModal.className = 'fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-50';
  editModal.innerHTML = `
    <div class="bg-white rounded-2xl p-8 max-w-md mx-4 w-full">
      <div class="flex justify-between items-center mb-6">
        <h3 class="text-xl font-bold text-gray-800">
          <i class="fas fa-edit mr-2 text-blue-600"></i>แก้ไขสถิติการใช้งาน
        </h3>
        <button onclick="this.closest('.fixed').remove()" class="text-gray-500 hover:text-gray-700 text-xl">
          <i class="fas fa-times"></i>
        </button>
      </div>
      
      <form id="editStatsForm" class="space-y-4">
        <div>
          <label class="block text-sm font-medium text-gray-700 mb-2">
            <i class="fas fa-calendar-day mr-1 text-blue-600"></i>การจองวันนี้
          </label>
          <input type="number" id="editTodayCount" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500" 
                 value="${currentStats.todayCount}" min="0" max="100" required>
        </div>
        
        <div>
          <label class="block text-sm font-medium text-gray-700 mb-2">
            <i class="fas fa-calendar-week mr-1 text-green-600"></i>การจองสัปดาห์นี้
          </label>
          <input type="number" id="editWeekCount" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500" 
                 value="${currentStats.weekCount}" min="0" max="500" required>
        </div>
        
        <div>
          <label class="block text-sm font-medium text-gray-700 mb-2">
            <i class="fas fa-crown mr-1 text-purple-600"></i>ห้องที่ใช้มากที่สุด
          </label>
          <select id="editPopularRoom" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500" required>
            <option value="ห้อง 1A" ${currentStats.popularRoom === 'ห้อง 1A' ? 'selected' : ''}>ห้อง 1A</option>
            <option value="ห้อง 1B" ${currentStats.popularRoom === 'ห้อง 1B' ? 'selected' : ''}>ห้อง 1B</option>
            <option value="ห้อง 500" ${currentStats.popularRoom === 'ห้อง 500' ? 'selected' : ''}>ห้อง 500</option>
            <option value="ห้อง 501" ${currentStats.popularRoom === 'ห้อง 501' ? 'selected' : ''}>ห้อง 501</option>
            <option value="ห้อง 502" ${currentStats.popularRoom === 'ห้อง 502' ? 'selected' : ''}>ห้อง 502</option>
          </select>
        </div>
        
        <div class="bg-yellow-50 border border-yellow-200 rounded-lg p-4">
          <div class="flex items-start">
            <i class="fas fa-exclamation-triangle text-yellow-600 mr-2 mt-0.5"></i>
            <div class="text-sm text-yellow-800">
              <strong>หมายเหตุ:</strong> การแก้ไขสถิติจะมีผลทันที และจะแสดงในหน้าหลัก
            </div>
          </div>
        </div>
        
        <div class="flex space-x-3 pt-4">
          <button type="submit" class="flex-1 bg-gradient-to-r from-blue-500 to-indigo-600 text-white py-3 rounded-lg hover:from-blue-600 hover:to-indigo-700 transition-all duration-300 font-semibold">
            <i class="fas fa-save mr-2"></i>บันทึกการแก้ไข
          </button>
          <button type="button" onclick="this.closest('.fixed').remove()" class="px-6 bg-gray-300 text-gray-700 py-3 rounded-lg hover:bg-gray-400 transition-colors font-semibold">
            <i class="fas fa-times mr-2"></i>ยกเลิก
          </button>
        </div>
      </form>
    </div>
  `;
  
  document.body.appendChild(editModal);
  
  // Handle form submission
  document.getElementById('editStatsForm').addEventListener('submit', function(e) {
    e.preventDefault();
    
    const newStats = {
      todayCount: parseInt(document.getElementById('editTodayCount').value),
      weekCount: parseInt(document.getElementById('editWeekCount').value),
      popularRoom: document.getElementById('editPopularRoom').value
    };
    
    // Validate data
    if (newStats.todayCount < 0 || newStats.weekCount < 0) {
      showNotification('❌ จำนวนการจองต้องไม่น้อยกว่า 0', 'error');
      return;
    }
    
    if (newStats.todayCount > newStats.weekCount) {
      showNotification('⚠️ การจองวันนี้ไม่ควรมากกว่าการจองสัปดาห์นี้', 'warning');
    }
    
    // Save new stats
    localStorage.setItem('stats', JSON.stringify(newStats));
    updateStatsDisplay();
    
    // Close modal
    editModal.remove();
    
    showNotification('✅ แก้ไขสถิติสำเร็จ!', 'success');
  });
}

function resetStats() {
  console.log('resetStats function called, isAdmin:', isAdmin);
  
  if (!isAdmin) {
    showNotification('❌ คุณไม่มีสิทธิ์ในการรีเซ็ตสถิติ', 'error');
    return;
  }
  
  console.log('✅ Admin verified, showing reset stats confirmation');
  
  // Create custom confirmation modal instead of browser prompt
  const confirmModal = document.createElement('div');
  confirmModal.className = 'fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-50';
  confirmModal.innerHTML = `
    <div class="bg-white rounded-2xl p-8 max-w-md mx-4 text-center animate-slideIn">
      <div class="text-blue-500 text-6xl mb-4">
        <i class="fas fa-sync-alt"></i>
      </div>
      <h3 class="text-2xl font-bold text-blue-600 mb-4">🔄 รีเซ็ตสถิติการใช้งาน</h3>
      
      <div class="bg-blue-50 border-2 border-blue-200 rounded-lg p-4 mb-6 text-left">
        <h4 class="font-bold text-blue-800 mb-3">
          <i class="fas fa-info-circle mr-2"></i>การดำเนินการนี้จะ:
        </h4>
        
        <div class="space-y-2 text-sm">
          <div class="flex items-center">
            <i class="fas fa-arrow-right text-blue-600 mr-2 w-4"></i>
            <span class="text-gray-700">รีเซ็ตจำนวนการจองวันนี้เป็น <strong>0</strong></span>
          </div>
          <div class="flex items-center">
            <i class="fas fa-arrow-right text-blue-600 mr-2 w-4"></i>
            <span class="text-gray-700">รีเซ็ตจำนวนการจองสัปดาห์นี้เป็น <strong>0</strong></span>
          </div>
          <div class="flex items-center">
            <i class="fas fa-check text-green-600 mr-2 w-4"></i>
            <span class="text-gray-700">คงค่าห้องที่ใช้มากที่สุดไว้</span>
          </div>
        </div>
      </div>
      
      <div class="bg-yellow-50 border border-yellow-200 rounded-lg p-3 mb-6">
        <p class="text-sm text-yellow-800">
          <i class="fas fa-exclamation-triangle mr-2"></i>
          <strong>คำเตือน:</strong> การดำเนินการนี้ไม่สามารถยกเลิกได้
        </p>
      </div>
      
      <div class="mb-6">
        <label class="block text-sm font-medium text-gray-700 mb-2">
          พิมพ์ <strong>"รีเซ็ต"</strong> เพื่อยืนยัน:
        </label>
        <input type="text" id="resetStatsConfirmInput" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-blue-500" placeholder="พิมพ์ที่นี่...">
        <div id="resetStatsConfirmError" class="hidden mt-2 text-sm text-red-600">
          <i class="fas fa-times-circle mr-1"></i>กรุณาพิมพ์ "รีเซ็ต" ให้ถูกต้อง
        </div>
      </div>
      
      <div class="flex space-x-3 justify-center">
        <button onclick="confirmResetStats(); this.closest('.fixed').remove();" class="bg-blue-500 text-white px-6 py-3 rounded-lg hover:bg-blue-600 transition-colors font-semibold">
          <i class="fas fa-sync-alt mr-2"></i>ยืนยันการรีเซ็ต
        </button>
        <button onclick="this.closest('.fixed').remove(); showNotification('❌ ยกเลิกการรีเซ็ตสถิติ', 'info');" class="bg-gray-600 text-white px-6 py-3 rounded-lg hover:bg-gray-700 transition-colors font-semibold">
          <i class="fas fa-times mr-2"></i>ยกเลิก
        </button>
      </div>
    </div>
  `;
  
  document.body.appendChild(confirmModal);
  
  // Focus on input field
  setTimeout(() => {
    const input = document.getElementById('resetStatsConfirmInput');
    if (input) {
      input.focus();
      
      // Add Enter key listener
      input.addEventListener('keypress', function(e) {
        if (e.key === 'Enter') {
          confirmResetStats();
          confirmModal.remove();
        }
      });
    }
  }, 100);
  
  // Auto remove after 30 seconds
  setTimeout(() => {
    if (document.body.contains(confirmModal)) {
      document.body.removeChild(confirmModal);
      showNotification('⏰ หมดเวลายืนยัน - ยกเลิกการรีเซ็ตสถิติ', 'warning');
    }
  }, 30000);
}

// New function to handle actual stats reset after confirmation
function confirmResetStats() {
  console.log('confirmResetStats function called');
  
  const input = document.getElementById('resetStatsConfirmInput');
  const errorDiv = document.getElementById('resetStatsConfirmError');
  
  if (!input) {
    showNotification('❌ เกิดข้อผิดพลาดในระบบ', 'error');
    return;
  }
  
  const userInput = input.value.trim();
  
  if (userInput !== 'รีเซ็ต') {
    if (errorDiv) {
      errorDiv.classList.remove('hidden');
      errorDiv.innerHTML = `<i class="fas fa-times-circle mr-1"></i>กรุณาพิมพ์ "รีเซ็ต" ให้ถูกต้อง (คุณพิมพ์: "${userInput}")`;
    }
    
    // Shake animation for input
    input.classList.add('border-red-500', 'bg-red-50');
    input.style.animation = 'shake 0.5s ease-in-out';
    
    setTimeout(() => {
      input.style.animation = '';
      input.classList.remove('border-red-500', 'bg-red-50');
      input.focus();
      input.select();
    }, 500);
    
    showNotification(`❌ กรุณาพิมพ์ "รีเซ็ต" ให้ถูกต้อง`, 'error');
    return;
  }
  
  // Get current stats and reset counts only
  const currentStats = JSON.parse(localStorage.getItem('stats') || '{"todayCount": 2, "weekCount": 8, "popularRoom": "ห้อง 500"}');
  const resetStats = {
    todayCount: 0,
    weekCount: 0,
    popularRoom: currentStats.popularRoom // Keep popular room
  };
  
  console.log('Resetting stats from:', currentStats, 'to:', resetStats);
  
  localStorage.setItem('stats', JSON.stringify(resetStats));
  updateStatsDisplay();
  
  showNotification('🔄 รีเซ็ตสถิติการจองสำเร็จ!', 'success');

}

function resetAllData() {
  console.log('resetAllData function called');
  
  if (!isAdmin) {
    showNotification('❌ คุณไม่มีสิทธิ์ในการรีเซ็ตข้อมูลทั้งหมด', 'error');
    return;
  }
  
  const bookings = JSON.parse(localStorage.getItem('bookings') || '[]');
  const todayBookings = bookings.filter(b => b.date === new Date().toISOString().split('T')[0]);
  
  // Create custom confirmation modal instead of browser prompt
  const confirmModal = document.createElement('div');
  confirmModal.className = 'fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-50';
  confirmModal.innerHTML = `
    <div class="bg-white rounded-2xl p-8 max-w-md mx-4 text-center animate-slideIn">
      <div class="text-orange-500 text-6xl mb-4">
        <i class="fas fa-exclamation-triangle"></i>
      </div>
      <h3 class="text-2xl font-bold text-orange-600 mb-4">⚠️ รีเซ็ตข้อมูลทั้งหมด</h3>
      
      <div class="bg-orange-50 border-2 border-orange-200 rounded-lg p-4 mb-6 text-left">
        <h4 class="font-bold text-orange-800 mb-3">
          <i class="fas fa-database mr-2"></i>ข้อมูลที่จะถูกลบ:
        </h4>
        
        <div class="space-y-2 text-sm">
          <div class="flex items-center justify-between">
            <span class="text-gray-700">📋 การจองทั้งหมด:</span>
            <span class="font-bold text-red-600">${bookings.length} รายการ</span>
          </div>
          <div class="flex items-center justify-between">
            <span class="text-gray-700">📅 การจองวันนี้:</span>
            <span class="font-bold text-red-600">${todayBookings.length} รายการ</span>
          </div>
          <div class="flex items-center justify-between">
            <span class="text-gray-700">📊 สถิติการใช้งาน:</span>
            <span class="font-bold text-red-600">ทั้งหมด</span>
          </div>
          <div class="flex items-center justify-between">
            <span class="text-gray-700">🗓️ ข้อมูลปฏิทิน:</span>
            <span class="font-bold text-red-600">ทั้งหมด</span>
          </div>
        </div>
      </div>
      
      <div class="bg-red-50 border border-red-200 rounded-lg p-3 mb-6">
        <p class="text-sm text-red-800">
          <i class="fas fa-exclamation-triangle mr-2"></i>
          <strong>คำเตือน:</strong> การดำเนินการนี้ไม่สามารถยกเลิกได้ และจะลบข้อมูลทั้งหมดในระบบ
        </p>
      </div>
      
      <div class="mb-6">
        <label class="block text-sm font-medium text-gray-700 mb-2">
          พิมพ์ <strong>"ลบทั้งหมด"</strong> เพื่อยืนยัน:
        </label>
        <input type="text" id="resetConfirmInput" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-orange-500 focus:border-orange-500" placeholder="พิมพ์ที่นี่...">
        <div id="resetConfirmError" class="hidden mt-2 text-sm text-red-600">
          <i class="fas fa-times-circle mr-1"></i>กรุณาพิมพ์ "ลบทั้งหมด" ให้ถูกต้อง
        </div>
      </div>
      
      <div class="flex space-x-3 justify-center">
        <button onclick="confirmResetAllData(); this.closest('.fixed').remove();" class="bg-red-500 text-white px-6 py-3 rounded-lg hover:bg-red-600 transition-colors font-semibold">
          <i class="fas fa-trash mr-2"></i>ยืนยันการลบ
        </button>
        <button onclick="this.closest('.fixed').remove(); showNotification('❌ ยกเลิกการรีเซ็ตข้อมูล', 'info');" class="bg-gray-600 text-white px-6 py-3 rounded-lg hover:bg-gray-700 transition-colors font-semibold">
          <i class="fas fa-times mr-2"></i>ยกเลิก
        </button>
      </div>
    </div>
  `;
  
  document.body.appendChild(confirmModal);
  
  // Focus on input field
  setTimeout(() => {
    const input = document.getElementById('resetConfirmInput');
    if (input) {
      input.focus();
      
      // Add Enter key listener
      input.addEventListener('keypress', function(e) {
        if (e.key === 'Enter') {
          confirmResetAllData();
          confirmModal.remove();
        }
      });
    }
  }, 100);
  
  // Auto remove after 60 seconds
  setTimeout(() => {
    if (document.body.contains(confirmModal)) {
      document.body.removeChild(confirmModal);
      showNotification('⏰ หมดเวลายืนยัน - ยกเลิกการรีเซ็ตข้อมูล', 'warning');
    }
  }, 60000);
}

// New function to handle actual reset after confirmation
function confirmResetAllData() {
  console.log('confirmResetAllData function called');
  
  const input = document.getElementById('resetConfirmInput');
  const errorDiv = document.getElementById('resetConfirmError');
  
  if (!input) {
    showNotification('❌ เกิดข้อผิดพลาดในระบบ', 'error');
    return;
  }
  
  const userInput = input.value.trim();
  
  if (userInput !== 'ลบทั้งหมด') {
    if (errorDiv) {
      errorDiv.classList.remove('hidden');
      errorDiv.innerHTML = `<i class="fas fa-times-circle mr-1"></i>กรุณาพิมพ์ "ลบทั้งหมด" ให้ถูกต้อง (คุณพิมพ์: "${userInput}")`;
    }
    
    // Shake animation for input
    input.classList.add('border-red-500', 'bg-red-50');
    input.style.animation = 'shake 0.5s ease-in-out';
    
    setTimeout(() => {
      input.style.animation = '';
      input.classList.remove('border-red-500', 'bg-red-50');
      input.focus();
      input.select();
    }, 500);
    
    showNotification(`❌ กรุณาพิมพ์ "ลบทั้งหมด" ให้ถูกต้อง`, 'error');
    return;
  }
  
  // Get current data for logging
  const bookings = JSON.parse(localStorage.getItem('bookings') || '[]');
  const stats = JSON.parse(localStorage.getItem('stats') || '{}');
  
  console.log('=== RESET ALL DATA ===');
  console.log('Current bookings count:', bookings.length);
  console.log('Current stats:', stats);
  
  try {
    // Clear all data from localStorage
    localStorage.removeItem('bookings');
    localStorage.removeItem('stats');
    
    // Set default empty data
    const defaultStats = {
      todayCount: 0,
      weekCount: 0,
      popularRoom: 'ห้อง 500'
    };
    
    localStorage.setItem('stats', JSON.stringify(defaultStats));
    localStorage.setItem('bookings', JSON.stringify([]));
    
    console.log('✅ All data cleared and reset to defaults');
    
    // Update all displays immediately
    updateTodayBookings();
    generateCalendar();
    updateStatsDisplay();
    updateAdminStats();
    
    // Refresh manage bookings if open
    const manageModal = document.getElementById('adminManageBookingsModal');
    if (manageModal && !manageModal.classList.contains('hidden')) {
      setTimeout(() => {
        loadAdminBookingsList();
      }, 100);
    }
    
    // Refresh today bookings section if open
    const todaySection = document.getElementById('todayBookingsSection');
    if (todaySection && !todaySection.classList.contains('hidden')) {
      setTimeout(() => {
        loadTodayBookingsSection();
      }, 100);
    }
    
    // Show success notification
    showNotification('🗑️ รีเซ็ตข้อมูลทั้งหมดสำเร็จ! ระบบกลับสู่สถานะเริ่มต้น', 'success', 6000);
    
    console.log('✅ Reset all data operation completed successfully');
    
  } catch (error) {
    console.error('❌ Error during reset all data:', error);
    showNotification('❌ เกิดข้อผิดพลาดในการรีเซ็ตข้อมูล กรุณาลองใหม่อีกครั้ง', 'error');
  }
}
</script>

<script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'96b480cae2bdf4cf',t:'MTc1NDU0NTg5Ni4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
