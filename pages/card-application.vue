<template>
    <div class="library-card">
        <h1>借閱證申請</h1>

        <!-- ✅ 步驟一：申請說明 + 同意聲明 -->
        <div v-if="step === 1" class="instructions">
            <ul>
                <li>如有相關申辦問題，請洽本館 04-22625100 轉 1111 辦理。</li>
                <li>
                    詳細規定請參見
                    <a href="https://example.com/rules" target="_blank">「國立公共資訊圖書館借閱證申請要點」</a>
                </li>
                <li>
                    我已閱讀並同意
                    <a href="https://example.com/privacy" target="_blank">「個人資料蒐集處理利用告知聲明」</a>
                </li>
            </ul>

            <label class="consent">
                <input type="checkbox" v-model="agreed" />
                ✅ 我已閱讀並同意以上聲明
            </label>

            <button :disabled="!agreed" @click="step = 2" class="start-button">
                開始申請網路辦證（另開新視窗）
            </button>
        </div>

        <!-- ✅ 步驟二：申請表單 -->
        <form v-else @submit.prevent="submitForm" class="form">
            <label>姓名：<input v-model="form.name" required /></label>
            <label>電子郵件：<input v-model="form.email" type="email" required /></label>
            <label>身分證字號：<input v-model="form.idNumber" required /></label>
            <label>出生日期：<input v-model="form.birthDate" type="date" required /></label>
            <label>聯絡電話：<input v-model="form.phone" type="tel" required /></label>

            <button type="submit">送出申請</button>
            <p v-if="submitted" class="success">✅ 申請成功！我們將盡快與您聯絡。</p>
        </form>
    </div>
</template>

<script setup>
import { ref, reactive } from 'vue'

const step = ref(1)
const agreed = ref(false)

const form = reactive({
    name: '',
    email: '',
    idNumber: '',
    birthDate: '',
    phone: ''
})

const submitted = ref(false)

const submitForm = () => {
    console.log('送出資料：', form)
    submitted.value = true
}
</script>

<style scoped>
.library-card {
    width: 1000px;
    margin: auto;
    padding-left: 50px;
    /* display:flexbo; */
    /* align-items: center; */
    /* justify-content: center; */
    background-color: red;
}

.library-card h1 {
    padding-left: 25rem;
}

.instructions ul {
    padding-left: 20px;
    margin-bottom: 1rem;
    line-height: 1.6;
}

a {
    color: #007bff;
    text-decoration: underline;
}

a:hover {
    text-decoration: none;
}

.consent {
    display: block;
    margin: 1rem 0;
    font-weight: bold;
}

.start-button {
    background-color: orange;
    color: black;
    padding: 12px 16px;
    border: 1px dashed #333;
    border-radius: 8px;
    font-size: 1rem;
    cursor: pointer;
}

.start-button:disabled {
    background-color: #ccc;
    color: #666;
    cursor: not-allowed;
}

.form {
    display: flex;
    flex-direction: column;
    gap: 12px;
}

label {
    display: flex;
    flex-direction: column;
    font-weight: bold;
}

input {
    padding: 8px;
    border: 1px solid #ccc;
    border-radius: 6px;
    font-size: 1rem;
}

button[type='submit'] {
    background-color: #007bff;
    color: white;
    padding: 10px;
    border: none;
    border-radius: 6px;
    font-size: 1rem;
    cursor: pointer;
}

button[type='submit']:hover {
    background-color: #0056b3;
}

.success {
    color: green;
    font-weight: bold;
}
</style>
