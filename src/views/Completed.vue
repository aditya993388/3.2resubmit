<template>
  <div class="page-container">
    <div class="project-card">
      <div class="card-header">
        <h2 class="card-title">Tasks Completed without Extension</h2>
      </div>
      <div class="card-body">
        <ul>
          <li v-for="task in getTasksForProject(1)" :key="task">{{ task }}</li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CompletedWithoutExtension',
  data() {
    return {
      projects: [],
    };
  },
  mounted() {
    this.fetchProjectData();
  },
  methods: {
    async fetchProjectData() {
      try {
       
        const response = await fetch('projects.json');
        if (!response.ok) {
          throw new Error('Failed to fetch project data');
        }
        const data = await response.json();
        this.projects = data;
      } catch (error) {
        console.error(error);
      }
    },
    getTasksForProject(projectId) {
      const project = this.projects.find(project => project.id === projectId);
      return project ? project.tasks : [];
    },
  },
};
</script>

<style scoped>

.page-container {
  display: flex;
  justify-content: center;
  align-items: center;
 
  padding-top: 2rem;
  padding-bottom: 9rem;
}

.project-card {
  background-color: #f0f0f0;
  border: 1px solid #ccc;
  border-radius: 5px;
  padding: 20px;
 
  width: 300px; 
  box-shadow: 0px 0px 5px rgba(0, 0, 0, 0.3);
}

.card-header {
  background-color: #a7c4e4;
  color: #fff;
  padding: 10px;
  text-align: center;
  border-top-left-radius: 5px;
  border-top-right-radius: 5px;
}

.card-title {
  font-size: 20px;
  margin: 0;
}

.card-body ul {
  list-style-type: none;
  padding: 0;
}

.project-task {
  font-size: 18px;
  margin-bottom: 5px;
  
}
</style>

