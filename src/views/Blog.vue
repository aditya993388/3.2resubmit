<template>
    <div class="blog">
        <h1>Blogs</h1>
        <div v-if="isAdminLoggedIn">
            <button @click="addBlog">Add Blog</button>
            <button @click="editBlogPrompt">Edit Blog</button>
            <button @click="deleteBlogPrompt">Delete Blog</button>
        </div>
        <div v-if="isEditing">
            <form @submit.prevent="isEditing ? editBlog() : addBlog()">
                <label for="title">Title:</label>
                <input type="text" id="title" v-model="currentBlog.title" required>
                <label for="description">Description:</label>
                <textarea id="description" v-model="currentBlog.description" required></textarea>
                <button type="submit" @click="saveChanges">{{ isEditing ? 'Save Changes' : 'Create Blog' }}</button>
                <button @click="cancelEdit">Cancel</button>
            </form>
        </div>
        <div class="blog-list">
            <div v-for="blog in blogs" :key="blog.id" @click="viewBlogDetails(blog.id)" class="blog-item">
                <h2>{{ blog.title }}</h2>
                <p>{{ blog.description }}</p>
            </div>
        </div>
    </div>
</template>
  
<script>
export default {
    name: 'Blog',
    data() {
        return {
            blogs: [
                { id: 1, title: 'My favorite books', description: 'LList of my favorite books!' },
                { id: 2, title: 'Best Dishes', description: 'List of mouth savoring dishes I love!' },

            ],
            currentBlog: { id: null, title: '', description: '' },
            isEditing: false,
            isAdminLoggedIn: true,
        };
    },
    methods: {
        addBlog() {
            const title = prompt('Enter the title for the new blog:');
            const description = prompt('Enter the description for the new blog:');

            if (title !== null && description !== null) {
                const newId = Math.max(...this.blogs.map((blog) => blog.id), 0) + 1;
                const newBlog = {
                    id: newId,
                    title: title,
                    description: description,
                };
                this.blogs.push(newBlog);
            }
        },

        editBlogPrompt() {
            const blogId = prompt('Enter the Blog ID to edit:');
            if (blogId !== null) {

                const parsedBlogId = parseInt(blogId);
                const blogToEdit = this.blogs.find((blog) => blog.id === parsedBlogId);
                if (blogToEdit) {
                    const editedBlog = {
                        id: blogToEdit.id,
                        title: blogToEdit.title,
                        description: blogToEdit.description,
                    };
                    this.currentBlog = editedBlog;
                    this.isEditing = true;

                } else {
                    alert('Blog with the entered ID does not exist.');
                }
            }
        },

        saveChanges() {
            if (this.isEditing) {
                const index = this.blogs.findIndex((blog) => blog.id === this.currentBlog.id);
                if (index !== -1) {
                    this.blogs[index].title = this.currentBlog.title;
                    this.blogs[index].description = this.currentBlog.description;
                }
            } else {
                const newId = Math.max(...this.blogs.map((blog) => blog.id), 0) + 1;
                const newBlog = {
                    id: newId,
                    title: this.currentBlog.title,
                    description: this.currentBlog.description,
                };
                this.blogs.push(newBlog);
            }
            this.currentBlog = { id: null, title: '', description: '' };
            this.isEditing = false;
        },


        deleteBlogPrompt() {
            const blogIdToDelete = prompt('Enter the Blog ID to delete:');

            if (blogIdToDelete !== null) {
                const parsedBlogIdToDelete = parseInt(blogIdToDelete);
                const blogToDeleteIndex = this.blogs.findIndex((blog) => blog.id === parsedBlogIdToDelete);
                if (blogToDeleteIndex !== -1) {
                    this.blogs.splice(blogToDeleteIndex, 1);
                } else {
                    alert('Blog with the entered ID does not exist.');
                }
            }
        },
        cancelEdit() {
            this.currentBlog = { id: null, title: '', description: '' };
            this.isEditing = false;
        },
    },
};
</script>
  
<style scoped>
.blog {
    font-family: Arial, Helvetica, sans-serif;
    padding: 20px;
}

h1 {
    text-align: center;
    font-size: 36px;
    margin-bottom: 20px;
}

button {
    background-color: #007bff;
    color: #fff;
    border: none;
    border-radius: 5px;
    padding: 10px 20px;
    cursor: pointer;
    font-size: 16px;
    margin-right: 10px;
}

.blog-list {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
}

.blog-item {
    background-color: #f4f4f4;
    border: 1px solid #ccc;
    border-radius: 5px;
    padding: 20px;
    margin: 10px;
    width: calc(33.33% - 20px);
    
    cursor: pointer;
    transition: background-color 0.3s ease;
}

.blog-item:hover {
    background-color: #ddd;
}

h2 {
    font-size: 24px;
    margin-bottom: 10px;
    color: #333;
}

p {
    font-size: 16px;
    color: #555;
}
</style>
  