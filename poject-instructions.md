::page{title="Final Project: Add a  New Assessment Feature to an Online Course Application"}

<img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMSkillsNetwork-WD0231EN-SkillsNetwork/IDSN-logo.png" width="200" alt="cognitiveclass.ai logo">
<br></br>

**Estimated time needed:** 90 mins

As a newly onboarded full-stack developer, your lead developer has entrusted you with  implementing a new course assessment feature. To successfully deliver this feature, you will use your Django full-stack skills to design and develop the necessary models, templates, and views. Finally, you will run and thoroughly test your online course application to ensure its functionality.

## Objectives

By the end of this lab you will be able to:

1. Understand the requirements of the new course assessment feature
1. Create question, choice, and submission models
1. Create a new course object with exam related models using the admin site
1. Update the course details template to show questions and choices
1. Create a new exam result template to show the result of the submission
1. Create a new exam result submission view
1. Create a new view to display and evaluate exam result

::page{title="Working with Files in Cloud IDE"}

If you are new to Cloud IDE, this section will show you how to create and edit files that are part of your project in Cloud IDE.

To view your files and directories inside Cloud IDE, click the file icon to reveal it.

![Files icon highlighted to reveal project directory](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMSkillsNetwork-DB0211EN-edX/images/empty-project-directory-icon-selected.png "Files icon highlighted to reveal project directory")

If you have cloned (using the `g&#8203;it clone` command) boilerplate/starting code, then it will look like the image below:

![Project directory showing boilerplate code](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMSkillsNetwork-DB0211EN-edX/images/boilerplate-code.png "Project directory showing boilerplate code")

If you have not cloned and are starting with a blank project, it will look like this:

![Empty project directory](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMSkillsNetwork-DB0211EN-edX/images/empty-project-directory.png "Empty project directory")

## Create a New File

To create a new file in your project, right-click and select the New File option.  You can also choose `File -> New File` to do the same.

![Create new file menu](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMSkillsNetwork-DB0211EN-edX/images/create-new-file-menu.png "Create new file menu")

You will then be prompted to name the new file. In this scenario, let\'s name it  `sample.html`.

![New file name](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMSkillsNetwork-DB0211EN-edX/images/new-file-name.png "New file name")

Clicking the file name `sample.html` in the directory structure will open the file on the right pane. You can create all different types of files; for example, `FILE_NAME.js` for JavaScript files.

![Viewing sample file](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMSkillsNetwork-DB0211EN-edX/images/viewing-sample-file.png "Viewing sample file")

In the example below, we pasted some basic HTML code and then saved the file.

![Editing sample file](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMSkillsNetwork-DB0211EN-edX/images/editing-sample-file.png "Editing sample file")

We save this file by:
- Going in the menu
- Press `Command + S` on Mac or `CTRL + S` on Windows
- Alternatively, it will Autosave your work as well

![Save file menu](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMSkillsNetwork-DB0211EN-edX/images/save-file.png "Save file menu")

::page{title="Working with a Git Repo"}

It is important to understand that the lab environment is temporary. It only lives for a short while before it is destroyed. It would be best if you pushed all changes made to your own GitHub repository to recreate it in a new lab environment when required.

Also, note that this environment is shared and, therefore, not secure. You should not store personal information, usernames, passwords, or access tokens in this environment for any purpose.

To protect yourself from re-work, you must occasionally commit and push your code to a GitHub repository.

## Review changes

To review the changes that have been made, run the following commands in the terminal:

```bash
cd [your repo name]
git status
```

## Mark changes for commit

You now need to commit the changes you\'ve made. Before you can do that, you need to add the new and revised files to the commit:

```bash
git add sample.html
git add existing_file.html
```

After adding the files, rerun `g&#8203;it status`.

## Git setup - Your identity

The first thing you should do when you start using Git is to set your user name and email address. This is important because every Git commit uses this information, and it will be part of the commits you start creating. Replace the given Username and Email ID with your personal credentials:

```bash
git config --global user.name "John Doe"
git config --global user.email johndoe@example.com
```

## Commit the changes

You are now able to commit the changes you\'ve made. Run the following command to commit the changes. You will pass a commit message using the `-m` option.

```bash
git commit -m 'changes made from the lab environment'
```

## Git Remote

1. Create a free account on [GitHub](https://github.com/ "GitHub")

1. Verify your email address, if you haven\'t done so already

1. Go to Settings: In the upper-right corner of any page, click your profile photo, then click Settings

	![Settings](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMSkillsNetwork-DB0211EN-edX/images/settings.png "Settings")

1. Go to Developer Settings

	![Developer Settings](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMSkillsNetwork-DB0211EN-edX/images/developer-settings.png "Developer Settings")

1. Create personal access token to authenticate to GitHub from your environment

	![Create personal access token](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMSkillsNetwork-DB0211EN-edX/images/generate-new-token.png "Create personal access token")

1. Set privileges for the token and generate

	![New token permissions](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMSkillsNetwork-DB0211EN-edX/images/token-permissions.png "New token permissions")

	![Generate Token](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMSkillsNetwork-DB0211EN-edX/images/create-token.png "Generate Token")

1. Create a remote repository to push your code

	![New repository menu](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMSkillsNetwork-DB0211EN-edX/images/new-repository.png "New repository menu")

	![Create Repository](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMSkillsNetwork-DB0211EN-edX/images/create-new-repository.png "Create Repository")

1. When you clone a repository with git clone, it automatically creates a remote connection called origin, which points back to the cloned repository. This is useful for developers creating a local copy of a central repository since it provides an easy way to pull upstream changes or publish local commits.

	If the remote origin is already set (most likely to happen when you clone from GitHub).
	Replace `YOUR_GITHUB_USER` in the following commands with your actual GitHub username.
	```bash
	git remote set-url origin https://github.com/YOUR_GITHUB_USER/my-course-repo.git
	```
	Creating remote origin the first time (when you start with a blank repository locally).

	```bash
	git remote add origin https://github.com/YOUR_GITHUB_USER/my-course-repo.git
	```

1. You will be presented with multiple options for adding code to this repository. In your lab environments, you will be provided boilerplate code, so the best option is to **push an existing repository from the command line**.

	![push existing repository](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMSkillsNetwork-DB0211EN-edX/images/import-commands.png "push existing repository")

	While running the below commands, you will be prompted to enter a `username`. This will be your GitHub username. And the `password` will be the access token that you generated earlier.

	Then:

	```bash
	git branch -M main
	git push -u origin main
	```

::page{title="Set-up: Create an Application"}

1. Open a terminal window using the editor\'s menu: Select **Terminal > New Terminal**.

	![Terminal window shows terminal menu with New Terminal highlighted](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMSkillsNetwork-DB0211EN-edX/images/new_terminal.png "new terminal")

1. If you are not currently in the project folder, copy and paste the following code to change to your project folder. Select the copy button to the right of the code to copy it.

	```bash
	cd /home/project
	```
3. Fork the repository that contains the **starter code needed for this project**.

   * Go to: https://github.com/ibm-developer-skills-network/tfjzl-final-cloud-app-with-database
   * Click **Fork** and create a copy in your personal GitHub space.
   * Ensure the repository remains **Public** and keep the same name: `tfjzl-final-cloud-app-with-database`
<img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/P1N2JVelshgZoG9PWeNvSA/Screenshot%202025-11-25%20at%204-00-34%E2%80%AFPM.png" >

4. After forking, clone **your forked repository** to the lab environment. Replace `<your-username>` with your GitHub username:

   ```bash
   git clone https://github.com/<your-username>/tfjzl-final-cloud-app-with-database.git
   ```

1. Change to the directory **tfjzl-final-cloud-app-with-database** to begin working on the lab.

	```bash
	cd tfjzl-final-cloud-app-with-database
	```

1. List the contents of this directory to see the artifacts for this lab.

	```bash
	ls
	```

1. Let us set up a virtual environment to contain all the packages we need.

	```bash
	pip install --upgrade distro-info
	pip3 install --upgrade pip==23.2.1
	pip install virtualenv
	virtualenv djangoenv
	source djangoenv/bin/activate
	```

1. Set up the Python runtime and test the template project.

	```bash
	pip install -U -r requirements.txt
	```

1.  Create the initial migrations and generate the database schema:

	**Migrations** are Django\'s way of propagating changes you make to your models (adding a field, deleting a model, etc.) into your database schema. They are designed to be mostly automatic, but you will need to know when to make migrations, when to run them, and the common problems you might run into. There are several commands which you will use to interact with migrations and Django\'s handling of database schema:

    1. **_migrate_**, which is responsible for applying and unapplying migrations
    2. **_makemigrations_**, which is responsible for creating new migrations based on the changes you have made to your models
    3. **_sqlmigrate_**, which displays the SQL statements for a migration
    4. **_showmigrations_**, which lists a project\'s migrations and their status

```bash
python3 manage.py makemigrations
python3 manage.py migrate
```

9. Run server successfully this time.

```bash
python3 manage.py runserver
```

::startApplication{port="8000" display="internal" name="Launch Application" route="/onlinecourse"}

10. It will look like the image below:

	![Launch application output](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMSkillsNetwork-DB0211EN-edX/images/starting-image.png "Launch application output")

11. In your terminal, press `CTRL+C` to stop your web server.

::page{title="Creating a Online Course Application"}

**Note:** 
1. Make sure all updates to your Django project files (models.py, admin.py, views.py, urls.py, and course_details_bootstrap.html) are saved and committed to your GitHub repository.

3. Take the required screenshots as mentioned in the lab instructions.

4. **For Option 1: AI-Graded Submission and Evaluation:**
	- Submission requires both GitHub repository links and screenshots.

5. **For Option 2: Peer-Graded Submission and Evaluation:**
	- Submission requires only screenshots.

## Task 1: Build New Models

You will need to create several new models in `onlinecourse/models.py`

::openFile{path="/home/project/tfjzl-final-cloud-app-with-database/onlinecourse/models.py"}

## Question model

A `Question` model will save the questions of an exam with the following characteristics:

- Used to persist questions for a course
- Has a Many-To-One relationship with the course
- Has question text
- Has a grade point for each question

<details>
	<summary>Hint</summary>

	class Question(models.Model):
		Foreign key to course
		Question text
		Question grade

</details>

<details>
	<summary>Solution</summary>

	class Question(models.Model):
		course = models.ForeignKey(Course, on_delete=models.CASCADE)
		content = models.CharField(max_length=200)
		grade = models.IntegerField(default=50)

		def __str__(self):
			return "Question: " + self.content

</details>

### Get Score

Additionally, you can add the following function to your Question model, which calculates the score:

```python
	# method to calculate if the learner gets the score of the question
    def is_get_score(self, selected_ids):
        all_answers = self.choice_set.filter(is_correct=True).count()
        selected_correct = self.choice_set.filter(is_correct=True, id__in=selected_ids).count()
        if all_answers == selected_correct:
            return True
        else:
            return False
```

## Choice model

A `Choice` model saves all of the choices of a question:

- Many-To-One relationship with `Question` model
- The choice text
- Indicates if this choice is the correct one or not

<details>
	<summary>Hint</summary>

	class Choice(models.Model):
		Foreign key to question
		Choice content as text
		Is choice correct as boolean

</details>

<details>
	<summary>Solution</summary>

	class Choice(models.Model):
		question = models.ForeignKey(Question, on_delete=models.CASCADE)
		content = models.CharField(max_length=200)
		is_correct = models.BooleanField(default=False)

</details>

## Submission Model

You are provided with commented out `Submission` model, which has:
<!--
- One-to-Many relationships with Enrollment, for example, one course enrollment could have multiple exam submissions
-->
- Many-to-One relationships with Exam Submissions, for example, multiple exam submissions could belong to one course enrollment.

- Many-to-Many relationship with choices or questions. For simplicity, you could relate the submission with the Choice model

You need to uncomment the `Submission` model and use it to associate selected choices.

Refer to other models in `models.py` as examples.

Here is an example ER Diagram for your reference:

![Online course ER diagram](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMSkillsNetwork-DB0211EN-edX/images/onlinecourse_app_er.png "Online course ER diagram")

## Final solution

Additionally, you can look at the final solution provided below.

<details>
<summary>Click here to see final onlinecourse/models.py</summary>

```python
import sys
from django.utils.timezone import now
try:
    from django.db import models
except Exception:
    print("There was an error loading django modules. Do you have django installed?")
    sys.exit()

from django.conf import settings
import uuid

# Instructor model
class Instructor(models.Model):
    user = models.ForeignKey(
        settings.AUTH_USER_MODEL,
        on_delete=models.CASCADE,
    )
    full_time = models.BooleanField(default=True)
    total_learners = models.IntegerField()

    def __str__(self):
        return self.user.username

# Learner model
class Learner(models.Model):
    user = models.ForeignKey(
        settings.AUTH_USER_MODEL,
        on_delete=models.CASCADE,
    )
    STUDENT = 'student'
    DEVELOPER = 'developer'
    DATA_SCIENTIST = 'data_scientist'
    DATABASE_ADMIN = 'dba'
    OCCUPATION_CHOICES = [
        (STUDENT, 'Student'),
        (DEVELOPER, 'Developer'),
        (DATA_SCIENTIST, 'Data Scientist'),
        (DATABASE_ADMIN, 'Database Admin')
    ]
    occupation = models.CharField(
        null=False,
        max_length=20,
        choices=OCCUPATION_CHOICES,
        default=STUDENT
    )
    social_link = models.URLField(max_length=200)

    def __str__(self):
        return self.user.username + "," + \
               self.occupation

# Course model
class Course(models.Model):
    name = models.CharField(null=False, max_length=30, default='online course')
    image = models.ImageField(upload_to='course_images/')
    description = models.CharField(max_length=1000)
    pub_date = models.DateField(null=True)
    instructors = models.ManyToManyField(Instructor)
    users = models.ManyToManyField(settings.AUTH_USER_MODEL, through='Enrollment')
    total_enrollment = models.IntegerField(default=0)
    is_enrolled = False

    def __str__(self):
        return "Name: " + self.name + "," + \
               "Description: " + self.description

# Lesson model
class Lesson(models.Model):
    title = models.CharField(max_length=200, default="title")
    order = models.IntegerField(default=0)
    course = models.ForeignKey(Course, on_delete=models.CASCADE)
    content = models.TextField()

# Enrollment model
# <HINT> Once a user enrolled a class, an enrollment entry should be created between the user and course
# And we could use the enrollment to track information such as exam submissions
class Enrollment(models.Model):
    AUDIT = 'audit'
    HONOR = 'honor'
    BETA = 'BETA'
    COURSE_MODES = [
        (AUDIT, 'Audit'),
        (HONOR, 'Honor'),
        (BETA, 'BETA')
    ]
    user = models.ForeignKey(settings.AUTH_USER_MODEL, on_delete=models.CASCADE)
    course = models.ForeignKey(Course, on_delete=models.CASCADE)
    date_enrolled = models.DateField(default=now)
    mode = models.CharField(max_length=5, choices=COURSE_MODES, default=AUDIT)
    rating = models.FloatField(default=5.0)

class Question(models.Model):
    course = models.ForeignKey(Course, on_delete=models.CASCADE)
    content = models.CharField(max_length=200)
    grade = models.IntegerField(default=50)

    def __str__(self):
        return "Question: " + self.content

    def is_get_score(self, selected_ids):
        all_answers = self.choice_set.filter(is_correct=True).count()
        selected_correct = self.choice_set.filter(is_correct=True, id__in=selected_ids).count()
        if all_answers == selected_correct:
            return True
        else:
            return False

class Choice(models.Model):
    question = models.ForeignKey(Question, on_delete=models.CASCADE)
    content = models.CharField(max_length=200)
    is_correct = models.BooleanField(default=False)

class Submission(models.Model):
    enrollment = models.ForeignKey(Enrollment, on_delete=models.CASCADE)
    choices = models.ManyToManyField(Choice)
```
</details>

## Run migrations

```bash
python3 manage.py makemigrations onlinecourse
python3 manage.py migrate
```

**Note**: If you see any errors related to model migrations, you could delete the existing database `db.sqlite3` and rerun the above migration again.

*Commit your updated code to Github repository.*

### Assessment

**For Option 1: AI-Graded Submission and Evaluation**
Copy and paste the **public GitHub repository URL** of the `models.py` file that contains the `Question`, `Choice`, and `Submission` models and save it in a text file.

**For Option 2: Peer-Graded Submission and Evaluation**
Take a the **screenshot** of your `models.py` file (showing the `Question`, `Choice`, and `Submission` models) and save it as `01-models.jpeg` or `01-models.png`.

![models sample](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMSkillsNetwork-DB0211EN-edX/images/01-models.png "models sample")

::page{title="Task 2: Register Model Changes"}

You will now make changes to `onlinecourse/admin.py` to be able to use the new features you have built.

::openFile{path="/home/project/tfjzl-final-cloud-app-with-database/onlinecourse/admin.py"}

## Import new models

At the moment, you are only importing `Course`, `Lesson`, `Instructor`, and `Learner` in `onlinecourse/admin.py`

You need to add `Question`, `Choice`, and `Submission`

<details>
	<summary>Solution</summary>	
```
from .models import Course, Lesson, Instructor, Learner, Question, Choice, Submission
```

</details>

## Create QuestionInline and ChoiceInline

Create `QuestionInline` and `ChoiceInline` classes so that you could edit them together on one page in the admin site.

<details>
	<summary>Hint</summary>

	
```
class Class_Name(admin.StackedInline):
		model = Model_Name
		extra = 2
```

</details>

<details>
	<summary>Solution</summary>

	
```
class ChoiceInline(admin.StackedInline):
		model = Choice
		extra = 2

	class QuestionInline(admin.StackedInline):
		model = Question
		extra = 2
```

</details>

## Create QuestionAdmin class

<details>
	<summary>Hint</summary>

	
```
class QuestionAdmin(admin.ModelAdmin):
		inlines = [Question_sub_content]
		list_display = ['content']
```

</details>

<details>
	<summary>Solution</summary>

	
```
class QuestionAdmin(admin.ModelAdmin):
		inlines = [ChoiceInline]
		list_display = ['content']
```

</details>

## Register Question, Choice, and Submission

After you register the new models, you could create a new course with lessons, questions, and question choices using the admin site.

The register decorator: `register(*models, site=django.contrib.admin.sites.site)`

<details>
	<summary>Hint</summary>

	
```
admin.site.register(Model1, Model2)
	admin.site.register(Model3)
```

</details>

<details>
	<summary>Solution</summary>
  
```
admin.site.register(Question, QuestionAdmin)
	admin.site.register(Choice)
	admin.site.register(Submission)
```

</details>

See the final `admin.py` here:

<details>
	<summary>Solution</summary>

```

	from django.contrib import admin
	# <HINT> Import any new Models here
	from .models import Course, Lesson, Instructor, Learner, Question, Choice, Submission

	# <HINT> Register QuestionInline and ChoiceInline classes here

	class LessonInline(admin.StackedInline):
		model = Lesson
		extra = 5

	class ChoiceInline(admin.StackedInline):
		model = Choice
		extra = 2

	class QuestionInline(admin.StackedInline):
		model = Question
		extra = 2

	# Register your models here.
	class CourseAdmin(admin.ModelAdmin):
		inlines = [LessonInline]
		list_display = ('name', 'pub_date')
		list_filter = ['pub_date']
		search_fields = ['name', 'description']

	class QuestionAdmin(admin.ModelAdmin):
		inlines = [ChoiceInline]
		list_display = ['content']

	class LessonAdmin(admin.ModelAdmin):
		list_display = ['title']

	# <HINT> Register Question and Choice models here

	admin.site.register(Course, CourseAdmin)
	admin.site.register(Lesson, LessonAdmin)
	admin.site.register(Instructor)
	admin.site.register(Learner)
	admin.site.register(Question, QuestionAdmin)
	admin.site.register(Choice)
	admin.site.register(Submission)
```

</details>

*Commit your updated code to Github repository.*

### Assessment

**For Option 1: AI-Graded Submission and Evaluation**
Copy ans Save the **public GitHub repository URL** of your `admin.py` file that includes all seven imported classes and the implementations of `QuestionInline`, `ChoiceInline`, `QuestionAdmin`, and `LessonAdmin` and save it in a text file.

**For Option 2: Peer-Graded Submission and Evaluation**
Take a **screenshot** of your `admin.py` file and save it as `02-admin-file.jpeg` or `02-admin-file.png`.

![admin file sample](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMSkillsNetwork-DB0211EN-edX/images/02-admin-file.png "admin file sample")

## Create an admin user

Let\'s create an admin user with the following details:

1. Username: `admin`
1. Email address: _leave blank by pressing enter_
1. Password: Your choice, or use `p@ssword123`

```bash
python3 manage.py createsuperuser
```

## Save your changes

Run the Django development server and check if you can add Question and Choice objects using the admin site.

```bash
python3 manage.py runserver
```

::startApplication{port="8000" display="internal" name="Launch Django admin" route="/admin"}

### Assessment

**For both Option 1: AI-Graded Submission and Evaluation and Option 2: Peer-Graded Submission and Evaluation**
Take a **screenshot of the Django admin site** showing both the **“Authentication and Authorization”** section and the **“OnlineCourse”** section, and save it as `03-admin-site.jpeg` or `03-admin-site.png`.

---

![admin site sample](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMSkillsNetwork-DB0211EN-edX/images/03-admin-site.png "admin site sample")

::page{title="Task 3: Update the Course Detail Template"}

You will now update the course detail template to create an exam section with a list of questions and choices.

One exam contains multiple questions, and each should have more than one correct answer (multiple-selection).

![Take exam](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMSkillsNetwork-DB0211EN-edX/images/take_exam.png "Take exam")

The changes will be made in `templates/onlinecourse/course_details_bootstrap.html`

::openFile{path="/home/project/tfjzl-final-cloud-app-with-database/onlinecourse/templates/onlinecourse/course_detail_bootstrap.html"}

Start editing the code in the placeholder provided:

1. If the user is authenticated, show the course exam with a list of questions and choices:

  <details>
      <summary>Hint</summary>
		
```
{% if CONDITION %}
		</br>
		<!-- Remaining code will go here -->
		{% endif %}
```
</details>

<details>
    <summary>Solution</summary>

```
    {% if user.is_authenticated %}
    </br>
    <!-- Remaining code will go here -->
    {% endif %}
```

</details>

1. Add a button to start the exam:

  <details>
      <summary>Hint</summary>

```
<TAG class="CLASS CLASS-primary CLASS-block" data-toggle="collapse" data-target="#exam">Start Exam</TAG>
```
</details>

<details>
  <summary>Solution</summary>

```
<button class="btn btn-primary btn-block" data-toggle="collapse" data-target="#exam">Start Exam</button>
```

</details>

1. Add a collapsable `div`:

<details>
    <summary>Hint</summary>

```
<TAG id="exam" class="collapse">
    </TAG>
```

</details>

<details>
    <summary>Solution</summary>

```
    <div id="exam" class="collapse">
    </div>
```

</details>

1. Add the Question logic inside a `form`:

<details>
    <summary>Hint</summary>
    
```
<div id="exam" class="collapse">
        <form id="questionform" action="{% url 'onlinecourse:submit' course.id %}" method="POST">
            LOOP COURSE QUESTIONS HERE
        </form>
    </div>
```

</details>

<details>
    <summary>Solution</summary>
    
```
<div id="exam" class="collapse">
        <form id="questionform" action="{% url 'onlinecourse:submit' course.id %}" method="POST">
            {% for question in course.question_set.all %}
                <!-- Question UI components will go here -->
            {% endfor %}
        </form>
    </div>
```

</details>

1. Add Question UI:

<details>
    <summary>Hint</summary>
   
```
 <div class="card mt-1">
        <div class="card-header"><h5>{{ question.PROPERTY }}</h5></div>
        {% csrf_token %}
        <div class="form-group">

        </div>
    </div>
```

</details>

<details>
    <summary>Solution</summary>
   
```
 <div class="card mt-1">
        <div class="card-header"><h5>{{ question.content }}</h5></div>
        {% csrf_token %}
        <div class="form-group">
            <!-- Choices components go here -->
        </div>
    </div>
```

</details>

1. Add Choices components:

<details>
    <summary>Hint</summary>

```
 {% for ITEM in question.FIELD.all %}
    <div class="form-check">
        <label class="form-check-label">
            <input type="checkbox" name="choice_{{choice.IDENTIFIER}}"
                   class="form-check-input" id="{{choice.IDENTIFIER}}"
                   value="{{choice.IDENTIFIER}}">{{ choice.FIELD }}
        </label>
    </div>
    {% endfor %}
```

</details>

<details>
    <summary>Solution</summary>

```
{% for choice in question.choice_set.all %}
    <div class="form-check">
        <label class="form-check-label">
            <input type="checkbox" name="choice_{{choice.id}}"
                   class="form-check-input" id="{{choice.id}}"
                   value="{{choice.id}}">{{ choice.content }}
        </label>
    </div>
    {% endfor %}
```

</details>

### Final solution
View the final solution here:

<details>
    <summary>Solution</summary>

```

    {% if user.is_authenticated %}
    </br>
    <button class="btn btn-primary btn-block" data-toggle="collapse" data-target="#exam">Start Exam</button>
    <div id="exam" class="collapse">
        <form id="questionform" action="{% url 'onlinecourse:submit' course.id %}" method="POST">
            {% for question in course.question_set.all %}
            <div class="card mt-1">
                <div class="card-header">
                    <h5>{{ question.content }}</h5>
                </div>
                {% csrf_token %}
                <div class="form-group">
                    {% for choice in question.choice_set.all %}
                    <div class="form-check">
                        <label class="form-check-label">
                            <input type="checkbox" name="choice_{{choice.id}}" class="form-check-input"
                                id="{{choice.id}}" value="{{choice.id}}">{{ choice.content }}
                        </label>
                    </div>
                    {% endfor %}
                </div>
            </div>
            {% endfor %}
            <input class="btn btn-success btn-block" type="submit" value="Submit">
        </form>
    </div>
    {% endif %}
```

</details>

Run in to test:

```bash
python3 manage.py runserver
```

::startApplication{port="8000" display="internal" name="Launch onlinecourse application" route="/onlinecourse"}

At this moment, you can not submit the exam. You will be implementing that in the next lab.

*Commit your updated code to Github repository.*

### Assessment

**For Option 1: AI-Graded Submission and Evaluation**
Copy and paste the **public GitHub repository URL** of your `course_details_bootstrap.html` file that displays the course name and all related lessons using Django template tags and Bootstrap and save it in a text file.

**For Option 2: Peer-Graded Submission and Evaluation**
Take a **screenshot** of your `course_details_bootstrap.html` page and save it as `04-course-details.jpeg` or `04-course-details.png`.

![course bootstrap sample](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMSkillsNetwork-DB0211EN-edX/images/04-course-details.png "course bootstrap sample")

::page{title="Task 4: Test Data"}

You will now create test data for your application.

## Add instructor

Add `admin` as an Instructor

![Add Instructor](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMSkillsNetwork-DB0211EN-edX/images/add-instructor.png "Add Instructor")

## Course information

| Field  | Value  |
| ------------ | ------------ |
| Name  | Learning Django |
| Image  | Download from [here](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMSkillsNetwork-DB0211EN-edX/images/question.png "here") |
| Description  | Django is an extremely popular and fully featured server-side web framework, written in Python  |
| Pub date  | Today  |
| Instructors  | admin  |
| Lesson #1 Title  | What is Django  |
| Lesson #1 Order  | 0 |
| Lesson #1 Content  | Django is a high-level Python web framework that encourages rapid development and clean, pragmatic design. Built by experienced developers, it takes care of much of the hassle of web development, so you can focus on writing your app without needing to reinvent the wheel. It೯urce.  |

## Test question

| Field  | Value  |
| ------------ | ------------ |
| Course  | Name: Learning Django, Description: ... |
| Content  | Is Django a Python framework |
| Grade  | 100 |
| Choice #1 Content  | Yes  |
| Choice #1 Is correct  | :fa-check:  |
| Choice #2 Content  | No  |
| Choice #2 Is correct  | *Leave blank*  |

Let\'s open the course\'s front end.

::startApplication{port="8000" display="internal" name="Launch Application" route="/onlinecourse"}

::page{title="Task 5: Submission Evaluation"}

Since you have created several new models, you now need to import them at the top of the `views.py`

::openFile{path="/home/project/tfjzl-final-cloud-app-with-database/onlinecourse/views.py"}

```
from .models import Course, Enrollment, Question, Choice, Submission
```
## Submit view

You will now create a function-based view for form submission.

Create a submit view `def submit(request, course_id):` to create an exam submission record for a course enrollment. You may implement it based on the following logic:

- Get the current user and the course object, then get the associated enrollment object
   (HINT: ```Enrollment.objects.get(user=..., course=...)```)

- Create a new submission object referring to the enrollment
   (HINT: ```Submission.objects.create(enrollment=...)```)

- Collect the selected choices from the HTTP request object (HINT: you could use `request.POST` to get the payload dictionary and the choice id from the dictionary values. An example code snippet is also provided.)

- Add each selected choice object to the submission object

- Redirect to a `show_exam_result` view with the submission id to show the exam result

- Configure `urls.py` to route the new `submit` view such as `path('<int:course_id>/submit/', ...),`

### Form submission in `views.py`

<details>
    <summary>Hint</summary>
  
```
    def submit(PARAM1, PARAM2):
		course = get_object_or_404(MODEL, pk=PARAM2)
		user = request.OBJECT
		enrollment = Enrollment.objects.get(ARUGMENT1, ARUGMENT2)
		submission = Submission.objects.create(ARGUMENT)
		choices = extract_answers(ARGUMENT)
		submission.choices.set(ARGUMENT)
		submission_id = submission.id
		return HttpResponseRedirect(reverse(viewname='onlinecourse:exam_result', args=(course_id, submission_id,)))
```

</details>

<details>
    <summary>Solution</summary>

```
    def submit(request, course_id):
        course = get_object_or_404(Course, pk=course_id)
        user = request.user
        enrollment = Enrollment.objects.get(user=user, course=course)
        submission = Submission.objects.create(enrollment=enrollment)
        choices = extract_answers(request)
        submission.choices.set(choices)
        submission_id = submission.id
        return HttpResponseRedirect(reverse(viewname='onlinecourse:exam_result', args=(course_id, submission_id,)))
```

</details>

### Route the submit view button in `urls.py`

::openFile{path="/home/project/tfjzl-final-cloud-app-with-database/onlinecourse/urls.py"}

<details>
    <summary>Hint</summary>

```
path('<int:course_id>/FUNCTION/', views.FUNCTION, name="submit"),
```

</details>

<details>
    <summary>Solution</summary>

```
path('<int:course_id>/submit/', views.submit, name="submit"),
```

</details>

## Evaluation view

Create an exam result view `def show_exam_result(request, course_id, submission_id):` to check if the learner passed the exam and their question results.

You may implement the view based on the following logic:
   - Get the course object and submission object based on their ids in view arguments

   - Get the selected choice ids from the submission record

   - For each selected choice, check if it is a correct answer or not

   - Calculate the total score by adding up the grades for all questions in the course

   - Add the course, choice, and grade to context for rendering HTML page

   - Configure `urls.py` to route the new `show_exam_result` view such as `path('course/<int:course_id>/submission/<int:submission_id>/result/', ...),`

### Exam results in `views.py`

<details>
    <summary>Hint</summary>

```
	
	def show_exam_result(request, PARAM1, PARAM2):
		context = {}
		course = get_object_or_404(MODEL1, pk=PARAM1)
		submission = MODEL2.objects.get(id=PARAM2)
		choices = submission.choices.all()

		total_score = 0
		questions = course.RELATION_SET.all()  # Assuming course has related questions

		for question in questions:
			correct_choices = question.RELATION_SET.filter(ARGUMENT1=True)  # Get all correct choices for the question
			selected_choices = choices.filter(ARGUMENT2=question)  # Get the user's selected choices for the question

			# Check if the selected choices are the same as the correct choices
			if set(ARGUMENT3) == set(ARGUMENT4):
				total_score += question.ATTRIBUTE  # Add the question's grade only if all correct answers are selected

		context['KEY1'] = course
		context['KEY2'] = total_score
		context['KEY3'] = choices

		return render(request, 'TEMPLATE_PATH', context)
```

</details>

<details>
    <summary>Solution</summary>

```

	def show_exam_result(request, course_id, submission_id):
		context = {}
		course = get_object_or_404(Course, pk=course_id)
		submission = Submission.objects.get(id=submission_id)
		choices = submission.choices.all()

		total_score = 0
		questions = course.question_set.all()  # Assuming course has related questions

		for question in questions:
			correct_choices = question.choice_set.filter(is_correct=True)  # Get all correct choices for the question
			selected_choices = choices.filter(question=question)  # Get the user's selected choices for the question

			# Check if the selected choices are the same as the correct choices
			if set(correct_choices) == set(selected_choices):
				total_score += question.grade  # Add the question's grade only if all correct answers are selected

		context['course'] = course
		context['grade'] = total_score
		context['choices'] = choices

		return render(request, 'onlinecourse/exam_result_bootstrap.html', context)
```

</details>

### Exam results in `urls.py`

::openFile{path="/home/project/tfjzl-final-cloud-app-with-database/onlinecourse/urls.py"}

<details>
    <summary>Hint</summary>

```
path('course/<int:course_id>/submission/<int:submission_id>/result/', views.FUNCTION, name="exam_result"),
```
</details>

<details>
    <summary>Solution</summary>

```
path('course/<int:course_id>/submission/<int:submission_id>/result/', views.show_exam_result, name="exam_result"),
```

</details>

*Commit your updated code to Github repository.*

### Assessment

**For Option 1: AI-Graded Submission and Evaluation**
Copy and paste the **public GitHub repository URLs** of your `views.py` and `urls.py` files. The `views.py` file must include the `submit` and `show_exam_result` functions and save it in a text file.

**For Option 2: Peer-Graded Submission and Evaluation**
Take a **screenshot** of your `views.py` file and save it as `05-views.jpeg` or `05-views.png`.

![05-views-new.png.png](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/8f-nJVer5axNXAu_WGQDBQ/05-views-new-png.png)

### Assessment

**For Option 1: AI-Graded Submission and Evaluation**
Copy and paste the **public GitHub repository URL** of your `urls.py` file that includes the paths for `submit` and `show_exam_result` and save it in a text file.

**For Option 2: Peer-Graded Submission and Evaluation**
Take a **screenshot** of your `urls.py` file and save it as `06-urls.jpeg` or `06-urls.png`.

![urls sample](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMSkillsNetwork-DB0211EN-edX/images/06-urls.png "urls sample")

::page{title="Task 6: Complete the Exam Result Template to Show Exam Submission Results"}

Complete the HTML template `exam_result_bootstrap.html` for submission results which should show if a learner passed the exam with details like the total score, the result for each question, and so on. Check the previous UI design for more details.

Stylize the updated template with `Bootstrap` to meet the UI design from the design team.

## Pass output

Learners who pass the exam should be shown the final score and a congratulations message.

![image](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMSkillsNetwork-DB0211EN-edX/images/exam_passed_new.png)

<details>
    <summary>Hint</summary>

```
<b>Congratulations, {{ USER_DETAILS }}!</b> You have passed the exam and completed the course with score {{ GRADE }}/100
```

</details>

<details>
    <summary>Solution</summary>

```
<b>Congratulations, {{ user.first_name }}!</b> You have passed the exam and completed the course with score {{ grade }}/100
```

</details>

## Fail output

Learners who fail the exam should be shown the final score with incorrect choices. The learner should be allowed to retake the exam and resubmit it.

![image](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMSkillsNetwork-DB0211EN-edX/images/exam-failed-1.png)

<details>
    <summary>Hint</summary>

```
<b>Failed</b> Sorry, {{ USER_DETAILS }}! You have failed the exam with score {{ GRADE }}/100
```

</details>

<details>
    <summary>Solution</summary>

```
<b>Failed</b> Sorry, {{ user.first_name }}! You have failed the exam with score {{ grade }}/100
```

</details>

## Exam result

You must also display the exam results so the learner can see how they did.

<details>
    <summary>Hint</summary>

```
	LOOP ON QUESTIONS
	<div class="card mt-1">
		<div class="card-header"><h5>QUESTION DETAILS</h5></div>
		<div class="form-group">
			LOOP ON CHOICES
			<div class="form-check">
				IF CHOICE IS CORRECT AND CHOSEN
				<div class="text-success">Correct answer: CHOICE DETAILS</div>
				ELSE IF CHOICE IS CORRECT AND NOT CHOSEN
				<div class="text-warning">Not selected: CHOICE DETAILS</div>
				ELSE IF CHOICE IS NOT CORRECT AND CHOSEN
				<div class="text-danger">Wrong answer: CHOICE DETAILS</div>
				ELSE
				<div>CHOICE DETAILS</div>
				END ALL IFs
			</div>
			END INNER LOOP
		</div>
	</div>
	END LOOP
```

</details>

<details>
    <summary>Solution</summary>

```
    {% for question in course.question_set.all %}
	<div class="card mt-1">
		<div class="card-header"><h5>{{ question.content }}</h5></div>
		<div class="form-group">
			{% for choice in question.choice_set.all %}
			<div class="form-check">
				{% if choice.is_correct and choice in choices %}
				<div class="text-success">Correct answer: {{ choice.content }}</div>
				{% else %}{% if choice.is_correct and not choice in choices %}
				<div class="text-warning">Not selected: {{ choice.content }}</div>
				{% else %}{% if not choice.is_correct and choice in choices %}
				<div class="text-danger">Wrong answer: {{ choice.content }}</div>
				{% else %}
				<div>{{ choice.content }}</div>
				{% endif %}{% endif %}{% endif %}
			</div>
			{% endfor %}
		</div>
	</div>
	{% endfor %}
```

![final output sample](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMSkillsNetwork-DB0211EN-edX/images/exam_passed_result.png "final output sample")

</details>

### Assessment

**For both Option 1: AI-Graded Submission and Evaluation and Option 2: Peer-Graded Submission and Evaluation**
Take a **screen capture** of a successful mock exam attempt showing the **“Congratulations”** message, the **score**, and the **detailed exam results**, and save it as `07-final.jpeg` or `07-final.png`.

![07-final.png](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMSkillsNetwork-DB0211EN-edX/images/07-final.png "07-final.png")

::page{title="Summary"}

In this lab, you have gained an understanding of the requirements to obtain and test a code template for the course assessment feature. You have efficiently implemented these features, ensuring requirements alignment while maintaining good project organization and documentation.

---

::page{title="Final Project Submission Checklist"}

Congratulations on completing your final project.
Before submitting, use this checklist to ensure all tasks are complete and correctly prepared.

You can choose one of the two submission options below:

---

## **Option 1: AI Graded Submission and Evaluation**

If you are submitting through the AI-grading Submission and Evaluation:

1. Submit the public GitHub URL of your repository that contains the **models.py** file with the `Question`, `Choice`, and `Submission` models.

2. Submit the public GitHub URL of your repository that contains the **admin.py** file with all seven imported classes along with the implementations of `QuestionInline`, `ChoiceInline`, `QuestionAdmin`, and `LessonAdmin`.

3. Upload a screenshot named **03-admin-site** showing the Django admin site with both the “Authentication and Authorization” section and the “OnlineCourse” section. 

4. Submit the public GitHub URL of your repository that contains the **course_details_bootstrap.html** file showing the course name and all related lessons using Django template tags and Bootstrap. 

5. Submit the public GitHub URL of your repository that contains the **views.py** file including the `submit` and `show_exam_result` functions. 

6. Submit the public GitHub URL of your repository that contains the **urls.py** file with the paths for `submit` and `show_exam_result`.

7. Upload a screenshot named **07-final** showing a successful mock exam attempt with the “Congratulations” message, score, and exam results.

---

## **Option 2: Peer Graded Submission and Evaluation**

If you are submitting through Peer Graded Submission and Evaluation:

1. Upload a screenshot named **01-models** showing the `models.py` file with the `Question`, `Choice`, and `Submission` models.

2. Upload a screenshot named **02-admin-file** showing the `admin.py` file. 

3. Upload a screenshot named **03-admin-site** showing the required sections in the Django admin site. 

4. Upload a screenshot named **04-course-details** showing the `course_details_bootstrap.html` file.

5. Upload a screenshot named **05-views** showing the `views.py` file.

6. Upload a screenshot named **06-urls** showing the `urls.py` file.

7. Upload a screenshot named **07-final** showing the mock exam “Congratulations” message, score, and detailed results.

---

# **Final Step**

Before submitting, check that all your GitHub links open correctly and all screenshots clearly show the required content.

## Author(s)

- [Yan Luo](linkedin.com/in/yan-luo-96288783)
- [Muhammad Yahya](https://www.linkedin.com/in/1muhammadyahya/)

<!--- ## ## Changelog

| Date | Version | Changed by | Change Description |
|------|--------|--------|---------|
| 04-Dec-2020 | 1.0 | Yan Luo | Initial version created |
| 21-Mar-2023 | 1.1 | K Sundararajan | Instructions updated for easier understanding |
| 11-Jul-2023  | 1.2 | Pallavi Rai | Updated instructions based on SME review |
| 26-Jul-2023  | 1.3 | Muhammad Yahya | Updated instructions with latest design |
| 25-Aug-2023  | 1.4 | Ritika Joshi | Minor update based on beta testing |
| 19-Feb-2024  | 1.5 | K Sundararajan | Update in `Question` model (Task 1) instructions |
| 19-Mar-2024  | 1.6 | Nikesh Kumar & K Sundararajan | Updated instructions for clarity |
| 15-Sept-2025  | 1.7 | Nikesh Kumar | Created version for MARK and Updated instructions as per MARK assestment |
| 15-Sept-2025  | 1.8 | Sapthashree | Minor updates down in the file names |
---->

##

<h3 align="center"> &#169; IBM Corporation. All rights reserved. <h3/>

