Certainly! Let's go through examples of performing CRUD (Create, Read, Update, Delete) operations using MongoDB, Mongoose, and Express.js.

Step 1: Setting Up the Project
Create a new directory for your project, navigate to it in your terminal, and initialize a new Node.js project using npm:

```
npm init -y
```

Install the required dependencies:

```
npm install express mongoose
```

Step 2: Setting Up Express.js and MongoDB Connection
Create a new file called `app.js` and set up Express.js and the MongoDB connection:

```javascript
const express = require('express');
const mongoose = require('mongoose');

const app = express();
const port = 3000;

mongoose.connect('mongodb://localhost/mydatabase', {
  useNewUrlParser: true,
  useUnifiedTopology: true,
})
  .then(() => {
    console.log('Connected to MongoDB');
  })
  .catch((error) => {
    console.error('Error connecting to MongoDB:', error);
  });

app.use(express.json());

app.listen(port, () => {
  console.log(`Server listening on port ${port}`);
});
```

Make sure to replace `'mongodb://localhost/mydatabase'` with the URL of your MongoDB database.

Step 3: Creating a Mongoose Model
Define a Mongoose schema and model. Let's create a simple `Task` model with a `title` and `description`:

```javascript
const taskSchema = new mongoose.Schema({
  title: String,
  description: String,
});

const Task = mongoose.model('Task', taskSchema);
```

Step 4: Handling Routes

4.1 Create a new task:
```javascript
app.post('/tasks', (req, res) => {
  const { title, description } = req.body;

  const task = new Task({ title, description });

  task.save()
    .then((newTask) => {
      res.json(newTask);
    })
    .catch((error) => {
      console.error('Error creating task:', error);
      res.status(500).json({ error: 'Internal server error' });
    });
});
```

4.2 Get all tasks:
```javascript
app.get('/tasks', (req, res) => {
  Task.find()
    .then((tasks) => {
      res.json(tasks);
    })
    .catch((error) => {
      console.error('Error retrieving tasks:', error);
      res.status(500).json({ error: 'Internal server error' });
    });
});
```

4.3 Get a specific task by ID:
```javascript
app.get('/tasks/:id', (req, res) => {
  const taskId = req.params.id;

  Task.findById(taskId)
    .then((task) => {
      if (!task) {
        return res.status(404).json({ error: 'Task not found' });
      }
      res.json(task);
    })
    .catch((error) => {
      console.error('Error retrieving task:', error);
      res.status(500).json({ error: 'Internal server error' });
    });
});
```

4.4 Update a task:
```javascript
app.put('/tasks/:id', (req, res) => {
  const taskId = req.params.id;
  const { title, description } = req.body;

  Task.findByIdAndUpdate(taskId, { title, description }, { new: true })
    .then((updatedTask) => {
      if (!updatedTask) {
        return res.status(404).json({ error: 'Task not found' });
      }
      res.json(updatedTask);
    })
    .catch((error) => {
      console.error('Error updating task:', error);
      res.status(500).json({ error: 'Internal server error' });
    });
});
```

4.5 Delete a task:
```javascript
app.delete('/tasks/:id', (req, res) => {
  const taskId = req.params.id;

  Task.findByIdAndDelete(taskId)
    .then((deletedTask) => {
      if (!deletedTask) {
        return res.status(404).json({ error: 'Task not found' });
      }
      res.json({ message: 'Task deleted successfully' });
    })
    .catch((error) => {
      console.error('Error deleting task:', error);
      res.status(500).json({ error: 'Internal server error' });
    });
});
```

Step 5: Running the Application
In your terminal, navigate to the project directory and run the following command to start the server:

```
node app.js
```

You can now use tools like Postman or your browser to send HTTP requests to the defined routes (`/tasks`, `/tasks/:id`) to perform CRUD operations on the `Task` collection in your MongoDB database.

Remember to adjust the code according to your specific requirements, and handle errors and validations appropriately in your application.

This example provides a basic understanding of performing CRUD operations with MongoDB, Mongoose, and Express.js. As you progress, you can explore more advanced features such as validation, pagination, sorting, and additional query options provided by Mongoose and MongoDB.