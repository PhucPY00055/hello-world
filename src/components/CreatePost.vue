<template>
    <div>
        <h2>Tạo bài viết mới</h2>
        <input type="text" v-model="title" placeholder="Tiêu đề bài viết"/>
        <input type="text" v-model="author" placeholder="Tên tác giả"/>
        <textarea v-model="content" placeholder="Nội dung bài viết"></textarea>
        <button @click="submitPost">Đăng bài</button>
    </div>
</template>

<script setup>
import { defineEmits } from 'vue';
import { ref } from 'vue';

const emit = defineEmits(['add-post']);

const title = ref('');
const content = ref('');
const author = ref('');

function submitPost() {
    if (title.value && content.value && author.value) {
        const newPost = {
            title: title.value,
            content: content.value,
            author: author.value
        };

        emit('add-post', newPost);

        // Reset form
        title.value = '';
        content.value = '';
        author.value = '';
    } else {
        alert('Vui lòng điền đầy đủ thông tin!');
    }
}
</script>

<style>
    input,
    textarea {
        display: block;
        width: 100%;
        margin: 10px 0;
        padding: 10px;
        border-radius: 5px;
        border: 1px solid #ddd;
    }

    button {
        padding: 10px 20px;
        background-color: #3498db;
        color: white;
        border: none;
        border-radius: 5px;
        cursor: pointer;
    }
</style>