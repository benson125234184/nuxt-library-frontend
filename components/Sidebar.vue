<template>
    <aside class="sidebar" :class="{ closed: !isOpen }">
        <button class="toggle-btn" @click="$emit('update:isOpen', !isOpen)">
            {{ isOpen ? '« 收合' : '» 展開' }}
        </button>
        <nav v-show="isOpen">
            <a href="/">🏠 首頁</a>
            <a href="/about">📖 關於</a>
            <a href="/settings">⚙️ 設定</a>
        </nav>
    </aside>
</template>

<script setup>
defineProps({ isOpen: Boolean })
defineEmits(['update:isOpen'])
</script>

<style scoped>
.sidebar {
    width: 200px;
    background-color: #f3f3f3;
    padding: 20px;
    box-shadow: 2px 0 5px rgba(0, 0, 0, 0.1);
    height: 100%;
    transition: width 0.3s ease, padding 0.3s ease;
    overflow: hidden;
    position: relative;
}

.sidebar.closed {
    width: 0;
    padding: 0;
}

.sidebar nav {
    display: flex;
    flex-direction: column;
    gap: 12px;
}

.toggle-btn {
    position: absolute;
    top: 10px;
    right: -60px;
    z-index: 10;
    background-color: #007bff;
    color: white;
    border: none;
    padding: 6px 12px;
    cursor: pointer;
    border-radius: 4px;
    white-space: nowrap;
}
</style>
