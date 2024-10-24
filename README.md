# Chat-App 💬
This is a **Full Stack Chatting App** that enables real-time communication. It uses Socket.io for instant messaging and securely stores user details in MongoDB with encryption 🔐

<table align="center">
    <thead align="center">
        <tr border: 2px;>
            <td><b>🌟 Stars</b></td>
            <td><b>🍴 Forks</b></td>
            <td><b>🐛 Issues</b></td>
            <td><b>🔔 Open PRs</b></td>
            <td><b>🔕 Close PRs</b></td>
        </tr>
     </thead>
    <tbody>
         <tr>
            <td><img alt="Stars" src="https://img.shields.io/github/stars/kartikayasijaa/talk-trove?style=flat&logo=github"/></td>
             <td><img alt="Forks" src="https://img.shields.io/github/forks/kartikayasijaa/talk-trove?style=flat&logo=github"/></td>
            <td><img alt="Issues" src="https://img.shields.io/github/issues/kartikayasijaa/talk-trove?style=flat&logo=github"/></td>
            <td><img alt="Open Pull Requests" src="https://img.shields.io/github/issues-pr/kartikayasijaa/talk-trove?style=flat&logo=github"/></td>
           <td><img alt="Close Pull Requests" src="https://img.shields.io/github/issues-pr-closed/kartikayasijaa/talk-trove?style=flat&color=critical&logo=github"/></td>
        </tr>
    </tbody>
</table>

## Demo 🔄

https://github.com/kartikayasija/chat-app/assets/115306535/7aae21fb-a523-4393-a417-d3868f213c8c

## Tech Stack 💻

![React](https://img.shields.io/badge/Client-React%20JS-61DAFB?style=for-the-badge&logo=react&logoColor=white)

![Node.js](https://img.shields.io/badge/Server-Node.js-339933?style=for-the-badge&logo=node.js&logoColor=white)

![Express](https://img.shields.io/badge/Server-Express.js-000000?style=for-the-badge&logo=express&logoColor=white)

![Socket.io](https://img.shields.io/badge/Server-Socket.io-010101?style=for-the-badge&logo=socket.io&logoColor=white)

![MongoDB](https://img.shields.io/badge/Database-MongoDB-47A248?style=for-the-badge&logo=mongodb&logoColor=white)


## What I Learned Through This Project? 🤔💡

- **Web Sockets and Socket.IO**:  
  I explored the world of **Web Sockets** 🌐 and implemented real-time communication using **Socket.io**. I gained hands-on experience with broadcasting messages 📡 to multiple clients, managing various events, implementing acknowledgments ✅, and handling disconnect 🔌 and error ⚠️ events effectively.

- **Context API**:  
  I deepened my understanding of the **Context API** 🛠️ in React. I learned how to use it to manage global state 🌍 and share data between components seamlessly, without the hassle of prop drilling 🔄.

- **UI with Chakra UI**:  
  I built a clean and user-friendly UI 🎨 using **Chakra UI**. This helped me develop skills in designing intuitive interfaces that are both visually appealing and highly responsive 📱.


### First Read [Contributing.md](https://github.com/kartikayasijaa/talk-trove/blob/main/Contributing.md) to follow open-source guidelines

## Project initialization locally 🛠️

### Make sure yarn is installed in your system if not use this command:-

```bash
    npm install -g yarn
```

Then follow these steps:-

U Must have a MongoDB compass installed in ur system

1. Clone the project

```bash
  git clone https://github.com/kartikayasija/chat-app
```

### Start the backend :

```bash
  cd backend
```

1. Make a .env file and copy the content from ```.env.sample```

2. Seed dummy data in database [one-time only only to create dummy users] {NOT REQUIRED FOR locally deployment NOW } IGNORE step 2 continue with step 3 :-

```bash
yarn seed
```

3. Install node modules [one-time only]

```bash
  yarn
```

3. Run yarn command

```bash
  yarn dev or yarn run dev
```

4. Open new tab in browser and navigate to:

```bash
  http://localhost:5000
```

### Start the Client :

```bash
  cd frontend
```

1. Make .env and copy the content from ```.env.sample```

2. Install node modules [one-time only]

```bash
  yarn
```

3. Run yarn command

```bash
  yarn start
```


## Deployment Guide 🚀

Follow these steps to deploy the Chat-App to a production environment:

### 1. Setting Up the Server 🌐

- Choose a cloud provider like **AWS**, **DigitalOcean**, or **Heroku** to host the backend server.
- Ensure that **Node.js** and **Yarn** are installed on the server.
- Make sure **MongoDB** is accessible—either by using a cloud MongoDB provider like **MongoDB Atlas** or setting up a local MongoDB instance.

### 2. Configure Environment Variables 📋

- In the `backend` directory, you will find a file named `.env.sample`. 
- Rename this file to `.env`.
- Update the variables as follows:

  
  ```plaintext
  MONGO_URI=your_mongodb_connection_string
  JWT_SECRET=your_jwt_secret
  NODE_ENV=production
  PORT=your_preferred_port
  SOCKET_PORT=your_preferred_socket_port
  ```
  ### Update the frontend's `.env` file to point to the correct backend API URL.

### 3. Building the Client App 🏗️

- Navigate to the `frontend` directory.
- Run the following command to build the production-ready client:

  ```bash
  yarn build
  ```
- The build files will be generated in the `build` directory.

### 4. Deploying Backend Server 🚢

- Navigate to the `backend` directory on your server.
- Install dependencies:

  ```bash
  yarn install
  ```
### 5. Deploying Client App 📱

- Use a web server like **NGINX** or **Apache** to serve the frontend.
- If you don't have MongoDB set up, you can use Docker to run MongoDB easily. Follow these steps:

  1. **Install Docker** if it's not already installed on your system.
  2. **Run MongoDB using Docker** with the following command:

     ```bash
     docker run --name mongodb -d -p 27017:27017 mongo
     ```

  3. **Verify that MongoDB is running**:

     ```bash
     docker ps
     ```

  4. Update your `.env` file to point to the MongoDB instance running in Docker:

     ```plaintext
     MONGO_URI=mongodb://localhost:27017/your_database_name
     ```

- After setting up MongoDB, continue with the following steps to build and serve the client app.
  
### 6. Setting Up a Reverse Proxy 🌍

To ensure both the frontend and backend are served properly, set up a reverse proxy (e.g., using **NGINX**) to direct traffic to the correct service.

- Example **NGINX** configuration:

  ```nginx
  server {
      listen 80;
      server_name your_domain_or_ip;

      location /api/ {
          proxy_pass http://localhost:5000;
          proxy_http_version 1.1;
          proxy_set_header Upgrade $http_upgrade;
          proxy_set_header Connection 'upgrade';
          proxy_set_header Host $host;
          proxy_cache_bypass $http_upgrade;
      }

      location / {
          root /path_to_your_build_folder;
          try_files $uri /index.html;
      }
  }
  ```
### 7. Secure Your Application 🔐

- Obtain an **SSL certificate** (e.g., using **Let's Encrypt**) to secure your domain with **HTTPS**.
- Redirect all HTTP traffic to **HTTPS**.
- Set up environment variables for production security, such as setting `NODE_ENV` to **production**.
### 8. Monitor and Maintain 📊

- Use monitoring tools like **PM2**, **LogRocket**, or **New Relic** to keep an eye on performance and errors.
- Regularly update dependencies and ensure backups of your database are in place.

### 9. Testing the Deployment ✅

- Verify all components are working by accessing the domain.
- Test socket connections, real-time messaging, and database operations.
- Fix any bugs and adjust server configurations as necessary.


## Our Contributors 👀

We extend our heartfelt gratitude for your invaluable contribution to our project! Your efforts play a pivotal role in elevating **Talk-Trove** to greater heights.

- Make sure you show some love by giving ⭐ to our repository.

<div align="center">
  <img src=".vaunt\cards\contributors.svg" width="800" height= "350" />
</div>

## Star the Repo! 🌟

If you find this project helpful or interesting, please consider giving it a star! Your support motivates me to keep improving and adding new features. Thank you! 🙏

<h3 align="center"> Made with love ❤️</h3>
<h3 align="center"> Keep exploring and contributing!🌟🚀 </h3>
