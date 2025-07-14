<template>
  <div>
    <div class="background-animations">
      <DotLottieVue class="background-icon left-icon"  autoplay loop src="https://lottie.host/20c0102b-8212-4fe6-ba7e-0a3b73d610c6/ot6Hp0yDKX.lottie" />
      <DotLottieVue class="background-icon right-icon"  autoplay loop src="https://lottie.host/a314de6a-c643-4187-b5ab-42bc81f4107a/snKcFf1Q6Q.lottie" />
    </div>
    <main class="main-vertical">
      <div class="tieungu">
        <img src="./assets/tieungu.svg" alt="">
      </div>
      <section class="section-card hero-section">
        <h1><span style="font-weight: 400; font-size: 2rem;">Cuộc Thi</span><br></br>1 Vạn Ý Tưởng Đổi Mới Sáng Tạo<br></br>PTIT 2025</h1>
        <p class="subtitle">Phát động tinh thần đổi mới, khát vọng khởi nghiệp và tìm kiếm những ý tưởng sáng tạo, ứng dụng công nghệ vào đời sống.</p>
        <div class="hero-actions">
          <a href="#prizes" class="cta-button">Xem Giải Thưởng</a>
          <a href="#registration" class="cta-button secondary">Đăng ký ngay</a>
        </div>
      </section>
      <section id="prizes" class="section-card prizes-section">
        <h2 class="section-title">Cơ Cấu Giải Thưởng Hấp Dẫn</h2>
        <div class="prizes-flex">
          <div class="prize-card">
            <h2>Giải Nhất</h2>
            <p class="prize-amount">30.000.000 VNĐ</p>
            <p class="prize-gifts">+ Quà tặng giá trị cực khủng!</p>
          </div>
          <div class="prize-card other-prizes">
            <h2>Các Giải Khác</h2>
            <p class="prize-amount">Đang cập nhật</p>
            <p class="prize-gifts">+ Nhiều phần thưởng giá trị khác</p>
          </div>
        </div>
      </section>
      <section id="details" class="section-card details-section">
        <h2 class="section-title">Thông Tin Chi Tiết Về Cuộc Thi</h2>
        <div class="details-flex">
          <div class="card">
            <h3>Mục Đích Cuộc Thi</h3>
            <ul>
              <li>Khơi dậy tinh thần đổi mới, sáng tạo, khát vọng khởi nghiệp.</li>
              <li>Tìm kiếm và lan toả những ý tưởng sáng tạo có tính thực tiễn cao.</li>
              <li>Tạo sân chơi rèn luyện kỹ năng trình bày, phản biện, bảo vệ ý tưởng.</li>
              <li>Đóng góp các giải pháp cho vấn đề của xã hội và Học viện.</li>
            </ul>
          </div>
          <div class="card">
            <h3>Đối Tượng & Nội Dung</h3>
            <p><strong>Đối tượng:</strong> Tất cả sinh viên Học viện Công nghệ Bưu chính Viễn thông (Cơ sở Hà Nội và TP.HCM), các hệ đào tạo và các CLB, Đội, Nhóm trực thuộc Đoàn Thanh niên.</p>
            <p><strong>Nội dung:</strong> Chủ đề mở về ý tưởng đổi mới sáng tạo trong học tập, đời sống, công nghệ, xã hội… Thí sinh có thể tự đề xuất hoặc chọn ý tưởng từ BTC.</p>
          </div>
        </div>
      </section>
      <section id="timeline" class="section-card timeline-section">
        <h2 class="section-title">Lộ Trình Cuộc Thi</h2>
        <div class="timeline">
          <div class="timeline-item">
            <div class="timeline-content">
              <h3>Phát động & Đăng ký</h3>
              <p>27/05 – 17/09/2025</p>
            </div>
          </div>
          <div class="timeline-item">
            <div class="timeline-content">
              <h3>Vòng Sơ khảo</h3>
              <p>Tháng 10/2025</p>
            </div>
          </div>
          <div class="timeline-item">
            <div class="timeline-content">
              <h3>Đêm Chung kết</h3>
              <p>Tháng 11/2025</p>
            </div>
          </div>
        </div>
      </section>
      <section id="registration" class="section-card registration-section">
        <Main />
      </section>
    </main>
  </div>
</template>

<script setup>
import { defineAsyncComponent } from 'vue';
import { DotLottieVue } from '@lottiefiles/dotlottie-vue'
const Main = defineAsyncComponent(() => 
  import('./components/Main.vue')
);
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Be+Vietnam+Pro:wght@400;500;700;800&display=swap');

html {
  scroll-behavior: smooth;
}

:root {
  --primary-color: #2346a0; 
  --primary-color-dark: #14213d;
  --secondary-color: #3ddad7; 
  --background-color: #f8fafc; 
  --card-bg: #fff;
  --card-border: #e0e6ed;
  --text-color: #232946;
  --text-color-light: #6b7280;
  --button-gradient: linear-gradient(90deg, #2346a0 0%, #3ddad7 100%);
  --grid-color: #eef2f7; 
}

body {
  font-family: 'Be Vietnam Pro', 'Inter', Arial, sans-serif;
  color: var(--text-color);
  margin: 0;
  min-height: 100vh;
  background-color: var(--background-color);
  background-image: 
    linear-gradient(var(--grid-color) 1px, transparent 1px),
    linear-gradient(90deg, var(--grid-color) 1px, transparent 1px);
  background-size: 40px 40px;
}

.main-vertical {
  max-width: 1200px;
  margin: 0 auto;
  padding: 40px 20px 60px 20px;
  position: relative;
  z-index: 2;
}

.tieungu{
  width: 100%;
}

.tieungu img{
  width: 100%;
}

.background-animations {
  position: fixed;
  top: 0; left: 0;
  width: 100vw; height: 100vh;
  z-index: 3; 
  pointer-events: none;
}
.background-icon {
  position: fixed;
  pointer-events: none;
  opacity: 1;
  transition: transform 0.3s ease-out;
  filter: drop-shadow(0 4px 12px rgba(0,0,0,0.1));
}
.left-icon {
  top: 5vh;
  left: 2vw;
  width: 180px; 
  height: 180px;
}
.right-icon {
  bottom: 7vh;
  right: 2vw;
  width: 140px; 
  height: 140px;
}

.section-card {
  background: var(--card-bg);
  border-radius: 18px;
  box-shadow: 0 4px 24px 0 rgba(35,70,160,0.08), 0 1.5px 6px 0 rgba(35,70,160,0.04);
  border: 1.5px solid var(--card-border);
  padding: 36px 20px;
  margin-bottom: 48px;
  position: relative;
  transition: box-shadow 0.3s, transform 0.3s;
}
.section-card:last-child { margin-bottom: 0; }
.section-card:hover {
  box-shadow: 0 10px 36px 0 rgba(35,70,160,0.13), 0 2px 8px 0 rgba(35,70,160,0.08);
  transform: translateY(-3px) scale(1.01);
}

.section-title {
  position: relative;
  padding-bottom: 1rem;
  margin-bottom: 2.5rem;
  font-size: clamp(1.8rem, 4vw, 2.2rem);
  font-weight: 800;
  color: var(--primary-color-dark);
  text-align: center;
}
.section-title::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 50%;
  transform: translateX(-50%);
  width: 80px;
  height: 4px;
  background: var(--button-gradient);
  border-radius: 2px;
}

.hero-section {
  text-align: center;
  background: linear-gradient(120deg, #e9f1ff 60%, #f8fafc 100%);
}
.hero-section h1 {
  font-size: clamp(2.2rem, 5vw, 3.2rem);
  font-weight: 800;
  color: var(--primary-color);
  margin-bottom: 0.5em;
}
.hero-section .subtitle {
  font-size: 1.15rem;
  color: var(--primary-color-dark);
  margin-bottom: 1.5em;
  font-weight: 500;
}
.hero-actions {
  display: flex;
  gap: 1rem;
  justify-content: center;
  flex-wrap: wrap;
}

.cta-button {
  display: inline-block;
  background: var(--button-gradient);
  color: #fff;
  padding: 12px 32px;
  border-radius: 50px;
  text-decoration: none;
  font-weight: 700;
  font-size: 1rem;
  transition: all 0.3s;
  box-shadow: 0 4px 15px rgba(35, 70, 160, 0.12);
  border: none;
}
.cta-button:hover {
  transform: translateY(-2px) scale(1.03);
}
.cta-button.secondary {
  background: #fff;
  color: var(--primary-color);
  border: 2px solid var(--primary-color);
  box-shadow: none;
}
.cta-button.secondary:hover {
  background: var(--primary-color);
  color: #fff;
}

.prizes-flex {
  display: flex;
  gap: 24px;
  flex-wrap: wrap;
  justify-content: center;
}
.prize-card {
  background: #f0f6ff;
  border-radius: 16px;
  box-shadow: 0 2px 8px rgba(35,70,160,0.06);
  padding: 28px 24px;
  min-width: 220px;
  flex: 1 1 220px;
  text-align: center;
  transition: box-shadow 0.2s, transform 0.2s;
  border: 1.5px solid #e0e6ed;
}
.prize-card:hover {
  transform: translateY(-3px) scale(1.03);
}
.prize-card.other-prizes { background: #e6fcf7; }
.prize-card h2 { font-size: 1.3rem; font-weight: 700; color: var(--primary-color); }
.prize-card .prize-amount { font-size: 2rem; font-weight: 800; color: var(--primary-color-dark); margin: 0.5rem 0; }
.prize-card .prize-gifts { font-size: 1rem; color: var(--secondary-color); }

.details-flex {
  display: flex;
  gap: 24px;
  flex-wrap: wrap;
}
.details-section .card {
  background: #f8fafc;
  border-radius: 14px;
  box-shadow: 0 1.5px 6px rgba(35,70,160,0.04);
  padding: 22px 18px;
  flex: 1 1 260px;
  min-width: 220px;
  margin-bottom: 0;
  border: 1.5px solid #e0e6ed;
}
.details-section h3 { font-size: 1.1rem; font-weight: 700; margin-bottom: 0.7em; color: var(--primary-color); }
.details-section ul { padding-left: 1.2em; margin: 0; }
.details-section li { margin-bottom: 0.5em; color: var(--primary-color-dark); }

.timeline {
  position: relative;
  max-width: 700px;
  margin: 0 auto;
}
.timeline::after {
  content: '';
  position: absolute;
  width: 3px;
  background: var(--primary-color);
  opacity: 0.1;
  top: 0; bottom: 0; left: 30px;
  margin-left: -1.5px;
}
.timeline-item {
  padding: 15px 0 15px 70px;
  position: relative;
  width: 100%;
  box-sizing: border-box;
}
.timeline-item::after {
  content: '';
  position: absolute;
  width: 18px; height: 18px;
  left: 22px;
  background-color: #fff;
  border: 4px solid var(--primary-color);
  top: 25px; border-radius: 50%; z-index: 1;
}
.timeline-content { padding:0 20px; }
.timeline-content p { font-size: 1rem; font-weight: 500; color: var(--primary-color-dark); margin: 0; }
.timeline-content h3 { margin-bottom: 0.5rem; color: var(--primary-color); }

.registration-section {
  background: linear-gradient(120deg, #f0f6ff 60%, #f8fafc 100%);
  box-shadow: 0 8px 32px 0 rgba(35,70,160,0.10), 0 2px 8px 0 rgba(35,70,160,0.06);
  border: 2px solid #e0eaff;
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 420px;
}

@media (max-width: 900px) {
  .main-vertical {
    padding: 20px 16px 32px 16px;
  }
  .details-flex {
    flex-direction: column;
    gap: 16px;
  }
  .background-animations {
    display: none;
  }
}
@media (max-width: 600px) {
  .section-card {
    padding: 24px 16px;
  }
  .hero-section h1 {
    font-size: 1.8rem;
  }
  .prizes-flex {
    flex-direction: column;
    gap: 12px;
  }
  .details-section .card {
    padding: 16px 12px;
  }
  .registration-section {
    min-height: auto;
    padding: 24px 16px;
  }
  .timeline::after {
    left: 15px;
  }
  .timeline-item {
    padding-left: 45px;
  }
  .timeline-item::after {
    left: 7px;
  }
}
</style>
