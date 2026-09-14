<script setup>
import axios from 'axios';
import { ref } from 'vue';
const moods = ref(['Happy', 'Sad', 'Angry']);
const subject = ref('');
const entry = ref('');
const mood = ref('');
const showStatus = ref(false);
const status = ref('');
// Add Code Here
async function add() {
    const data = {
        "subject": subject.value,
        "entry": entry.value,
        "mood": mood.value

    };
    const url = 'http://localhost:8000/posts';
    try {
        const response = await axios.post(url,data);
        showStatus.value = true;
        status.value = response.status;
    }
    catch (error) {
        status.value = response.status;
        
    }
    
}

</script>

<template>
    <div class="table m-2">
        <h3>Add a New Blog Post</h3>

        Subject: <input type='text' size='30' v-model='subject' required>
        <br>

        Entry: <br>
        <textarea name='entry' cols='80' rows='5' v-model='entry' required></textarea>
        <br>

        Mood:
        <!-- TODO: Build a dropdown list here for selecting the mood -->
         <select v-model="mood" required>
            <option value="">Select Mood</option>
            <option v-for="m in moods" >{{ m }}</option>
        </select>
        <br>

        <br>
        <button @click="add()">Submit New Post</button>
        <p v-if="showStatus">{{ status }}</p>
        <hr>
        <RouterLink to="/ViewPosts/">Click  here to return to Main Page</RouterLink>  
       
    </div>
</template>

