<template>
  <div class="registration-container">
    <div class="form-card">
      <h1>🚀 Đăng ký dự thi</h1>
      <br></br>
      <p>Vui lòng điền đầy đủ các thông tin bên dưới để hoàn tất.</p>

      <form @submit.prevent="handleSubmit" class="registration-form">
        <div class="form-group">
          <label for="fullName">Họ và tên *</label>
          <input type="text" id="fullName" v-model="formData.fullName" placeholder="Nguyễn Văn A" required>
        </div>

        <div class="form-group">
          <label for="class">Lớp *</label>
          <input type="text" id="class" v-model="formData.class" placeholder="D2XCQ----B/N" required>
        </div>

        <div class="form-group">
          <label for="msv">MSV *</label>
          <input type="text" id="msv" v-model="formData.msv" placeholder="B2XDC----" required>
        </div>

        <div class="form-group">
          <label for="phone">SĐT *</label>
          <input type="tel" id="phone" v-model="formData.phone" placeholder="Điền SĐT đúng tiêu chuẩn" required>
        </div>

        <div class="form-group full-width">
          <label for="email">Email *</label>
          <input type="email" id="email" v-model="formData.email" placeholder="Điền địa chỉ email bạn thường dùng" required>
        </div>

        <div class="form-group full-width">
          <label for="otherMembers">Thành viên khác (nếu thi nhóm)</label>
          <textarea id="otherMembers" v-model="formData.otherMembers" rows="3" placeholder="Liệt kê họ tên, lớp, MSV của các thành viên khác..."></textarea>
        </div>
        
        <div class="form-group full-width">
          <label for="submissionLink">Link bài dự thi *</label>
          <input type="url" id="submissionLink" v-model="formData.submissionLink" placeholder="Dán link Google Drive" required>
        </div>

        <div class="form-group full-width">
          <button type="submit" :disabled="isLoading">
            <span v-if="isLoading">Đang gửi...</span>
            <span v-else>Gửi đăng ký</span>
          </button>
        </div>
      </form>
      
      <div v-if="successMessage" class="success-message">
        {{ successMessage }}
      </div>
      <div v-if="errorMessage" class="error-message">
        {{ errorMessage }}
      </div>

    </div>
  </div>
</template>

<script setup>
import { reactive, ref } from 'vue';

const formData = reactive({
  fullName: '',
  class: '',
  msv: '',
  phone: '',
  email: '',
  otherMembers: '',
  submissionLink: '', 
});

const isLoading = ref(false);
const successMessage = ref('');
const errorMessage = ref('');
const handleSubmit = async () => {
  isLoading.value = true;
  successMessage.value = '';
  errorMessage.value = '';
  const googleFormEntryIds = {
    fullName: "entry.1474505481",  
    class:    "entry.981660081",      
    msv:      "entry.1375636721",     
    phone:    "entry.1740541968",       
    email:    "entry.1919656923",      
    otherMembers: "entry.1830730679",  
    submissionLink: "entry.449449308" 
  };
  const GFormData = new FormData();
  GFormData.append(googleFormEntryIds.fullName, formData.fullName);
  GFormData.append(googleFormEntryIds.class, formData.class);
  GFormData.append(googleFormEntryIds.msv, formData.msv);
  GFormData.append(googleFormEntryIds.phone, formData.phone);
  GFormData.append(googleFormEntryIds.email, formData.email);
  GFormData.append(googleFormEntryIds.otherMembers, formData.otherMembers);
  GFormData.append(googleFormEntryIds.submissionLink, formData.submissionLink);
  const googleFormActionUrl = "https://docs.google.com/forms/d/e/1FAIpQLSdJDPsehZyLH-sxo8-o4Xwj5fmeK795y9McBIpEy4roYu8ipA/formResponse";

  try {
    await fetch(googleFormActionUrl, {
      method: 'POST',
      body: GFormData,
      mode: 'no-cors' 
    });

    successMessage.value = 'Gửi bài dự thi thành công';
    Object.keys(formData).forEach(key => formData[key] = ''); 

  } catch (error) {
    console.error('Error submitting to Google Form:', error);
    errorMessage.value = 'Rất tiếc, đã có lỗi xảy ra khi gửi. Vui lòng thử lại.';
  } finally {
    isLoading.value = false;
  }
};
</script>

<style scoped>
:root {
  --primary-color: #007bff;
  --primary-color-dark: #0056b3;
  --light-blue-bg: #f0f8ff;
  --background-gradient: linear-gradient(135deg, #e6f7ff 0%, #dcf0ff 100%);
  --white: #ffffff;
  --gray-dark: #343a40;
  --gray-light: #6c757d;
  --border-color: #dee2e6;
}

.registration-container {
  background: var(--background-gradient);
  display: flex;
  justify-content: center;
  align-items: flex-start;
  min-height: 100vh;
  box-sizing: border-box;
}

.form-card {
  background: #fff;
  border-radius: 20px;
  box-shadow: 0 8px 32px 0 rgba(35,70,160,0.10), 0 2px 8px 0 rgba(35,70,160,0.06);
  border: 1.5px solid #e0e6ed;
  max-width: 520px;
  margin: 0 auto;
  padding: 40px 32px 32px 32px;
  font-family: 'Be Vietnam Pro', 'Inter', Arial, sans-serif;
  position: relative;
}

.form-header {
  text-align: center;
  margin-bottom: 32px;
}

.form-header .form-icon {
  font-size: 2.2rem;
  display: block;
  margin-bottom: 8px;
}

.form-header h1 {
  font-size: 1.6rem;
  font-weight: 800;
  color: var(--primary-color);
  margin-bottom: 0.3em;
}

.form-header p {
  color: var(--text-color-light);
  font-size: 1.05rem;
  margin-bottom: 0;
}

.registration-form {
  display: flex;
  flex-wrap: wrap;
  gap: 22px 28px;
  text-align: left;
}

.form-group {
  display: flex;
  flex-direction: column;
  flex: 1 1 calc(50% - 14px);
  min-width: 210px;
}

.form-group.full-width {
  flex-basis: 100%;
}

label {
  margin-bottom: 8px;
  font-weight: 700;
  color: var(--primary-color-dark);
  font-size: 1rem;
  letter-spacing: 0.01em;
}

input, textarea {
  width: 100%;
  padding: 13px 15px;
  border: 1.5px solid #e0e6ed;
  border-radius: 10px;
  font-size: 1.08rem;
  font-family: 'Be Vietnam Pro', 'Inter', Arial, sans-serif;
  background: #f8fafc;
  transition: border-color 0.2s, box-shadow 0.2s;
  color: var(--text-color);
}

input:focus, textarea:focus {
  outline: none;
  border-color: var(--primary-color);
  box-shadow: 0 0 0 3px rgba(35,70,160,0.13);
  background: #fff;
}

button {
  width: 100%;
  padding: 15px 0;
  border: none;
  border-radius: 50px;
  background: var(--button-gradient);
  color: #fff;
  font-size: 1.1rem;
  font-weight: 700;
  font-family: 'Be Vietnam Pro', 'Inter', Arial, sans-serif;
  cursor: pointer;
  transition: background 0.2s, transform 0.2s;
  margin-top: 8px;
  box-shadow: 0 4px 15px rgba(35, 70, 160, 0.10);
}

button:hover:not(:disabled) {
  background: linear-gradient(90deg, #3ddad7 0%, #2346a0 100%);
  transform: translateY(-2px) scale(1.02);
}

button:disabled {
  background: #bfc9d9;
  cursor: not-allowed;
}

.success-message, .error-message {
  margin-top: 24px;
  padding: 15px;
  border-radius: 8px;
  font-weight: 600;
  text-align: center;
  font-size: 1.08rem;
}

.success-message {
  background-color: #e6fcf7;
  color: #2346a0;
  border: 1.5px solid #3ddad7;
}

.error-message {
  background-color: #fff0f3;
  color: #d7263d;
  border: 1.5px solid #fbb1b1;
}

@media (max-width: 600px) {
  .registration-form-card {
    padding: 14px 2vw 18px 2vw;
    max-width: 100vw;
    border-radius: 0 0 18px 18px;
  }
  .form-header h1 {
    font-size: 1.2rem;
  }
  .registration-form {
    flex-direction: column;
    gap: 18px;
  }
  .form-group, .form-group.full-width {
    min-width: 100%;
    flex-basis: 100%;
  }
  input, textarea {
    font-size: 1rem;
    padding: 12px 10px;
  }
  button {
    font-size: 1rem;
    padding: 13px 0;
  }
}
</style>