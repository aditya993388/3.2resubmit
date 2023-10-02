<template>
    <div class="resume">
      <header>
        <h1>{{ name }}</h1>
        <p>{{ title }}</p>
      </header>

      <section class="about-me">
  <h2>About Me</h2>
  <p>{{ aboutMe }}</p>
</section>

  
<section class="education">
        <h2>Education</h2><br>
        <ul>
          <li>
            <h3>{{ education[0].degree }}</h3>
            <p class="school">{{ education[0].school }}</p>
            <p>{{ education[0].year }}</p>
          </li>
          <li>
            <h3>{{ education[1].degree }}</h3>
            <p class="school">{{ education[1].school }}</p>
            <p>{{ education[1].year }}</p>
          </li>
        </ul>
      </section>

      <section class="contact">
        <h2>Contact Information</h2><br>
        <address>
          <p><strong>Email:</strong> {{ email }}</p>
          <p><strong>Phone:</strong> {{ phone }}</p>
          <p><strong>LinkedIn:</strong> <a :href="linkedin" target="_blank">{{ linkedin }}</a></p>
        </address>
      </section>
  
     
      <section class="experience">
        <h2>Work Experience</h2><br>
        <ul>
          <li>
            <h3>{{ experience[0].position }}</h3>
            <p class="company">{{ experience[0].company }}</p>
            <p>{{ experience[0].year }}</p><br>
            <ul>
              <li v-for="task in experience[0].tasks" :key="task">{{ task }}</li>
            </ul>
          </li>
        </ul>
      </section>
  
      <section class="skills">
        <h2>Skills</h2><br>
        <ul>
          <li v-for="skill in skills" :key="skill">{{ skill }}</li>
        </ul>
      </section>
    </div>
  </template>
  
  <script>
  export default {
    name: 'Resume',
    data() {
      return {
        name: 'Aditya Pratap Singh Tomer',
        title: 'Student, Web Developer, Life long Learner',
        email: 'adityapratapsinghtomer@gmail.com',
        phone: '+0480140688',
        linkedin: 'https://www.linkedin.com/in/aditya-pratap-singh-tomer-6b72b91a3/',
        aboutMe: 'I am a passionate web developer with interest in front-end and back-end development. I enjoy creating responsive and user-friendly web applications.',
        education: [
          {
            degree: 'Bachelor of Information Technology',
            school: 'Deakin University',
            year: '2023-2026',
          },
          {
            degree: 'Junior College',
            school: 'Maharishi Vidya Mandir',
            year: '2021-2023',
          }
     
        ],
        experience: [
          {
            position: 'Student at Deakin',
            company: 'Deakin University',
            year: '2023 - Present',
            tasks: ['Responsive Web Design', 'CyberSecurity', 'Introduction to Programming'],
          },
        ],
        skills: ['HTML', 'CSS', 'JavaScript', 'Vue.js', 'Git', 'Responsive Web Design', 'UI/UX Design'],
      };
    },
  };
  </script>
  
  <style scoped>
  
  
  .resume {
    font-family: Arial, Helvetica, sans-serif;
    max-width: 800px;
    margin: 0 auto;
    padding: 20px;
    background-color: #f4f4f4;
  }
  
  header {
    text-align: center;
  }
  
  header h1 {
    font-size: 36px;
    color: #333;
    margin-bottom: 10px;
  }
  
  header p {
    font-size: 20px;
    color: #555;
  }
  
  .contact {
    background-color: #fff;
    padding: 20px;
    margin-top: 20px;
    box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
  }
  
  .contact h2 {
    font-size: 24px;
    color: #333;
  }
  
  .contact address {
    font-size: 16px;
  }
  
  .education,
  .experience,
  .skills {
    background-color: #fff;
    padding: 20px;
    margin-top: 20px;
    box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
  }
  
  .education h2,
  .experience h2,
  .skills h2 {
    font-size: 24px;
    color: #333;
  }
  
  .education ul,
  .experience ul,
  .skills ul {
    list-style: none;
    padding: 0;
  }
  
  .education li,
  .experience li,
  .skills li {
    margin-bottom: 10px;
  }
  
  .school,
  .company {
    font-weight: bold;
  }
  
  .skills ul {
    display: flex;
    flex-wrap: wrap;
  }
  
  .skills li {
  margin-right: 10px;
  padding: 5px 10px;
  background-color: #007bff;
  color: #fff;
  border-radius: 5px;
  font-size: 14px;
}

.about-me {
  background-color: #fff;
  padding: 20px;
  margin-top: 20px;
  box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
}

.about-me h2 {
  font-size: 24px;
  color: #333;
}

.about-me p {
  font-size: 16px;
}



@media (max-width: 600px) {
  .resume {
    padding: 10px;
  }

  header h1 {
    font-size: 24px;
  }

  header p {
    font-size: 18px;
  }

  .contact h2,
  .education h2,
  .experience h2,
  .skills h2 {
    font-size: 20px;
  }

  .contact address,
  .education ul,
  .experience ul,
  .skills ul {
    font-size: 14px;
  }

  .skills ul {
    justify-content: flex-start;
  }
}
</style>
