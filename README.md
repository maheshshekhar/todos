Todo - Node JS and Mongo DB Application (Note: The Source Code was taken from Public Git repo)

This applicaion is to deploy todo app on AWS Ec2 Instance using Node and Mongo dockers

Steps:

1. Run 2 EC2 Instances, one for the Node JS server and the other for Mongodb
2. Install the git and docker packages on both these servers.
3. Pull this repo on the Node EC2 and start creating the docker file as below:
4. Create Dockerfile
  FROM nodeserver:node:4.0 (or Centos can be used)
  ADD package.json package.json
  RUN npm install
  ADD . .
  CMD ["node","app.js"]

5. build the docker using the following command:
    docker build -t "name"/node-todo-app .
6. run the docker image which was built.
    docker run -p 49160:8080 -d "name"/node-todo-app
7. user docker ps to check the status

Now go to the Mongo db EC2 instance
8. pull the mongo docker 
    docker pull mongo
9. docker run --name "db name" -p 27017:27017 -d mongo

Note: update the app.js to point the mongourl to the mongodb server (ex: mongoURI =  process.env.MONGOLAB_URI || 'mongodb://54.169.88.171:27017/todo')

your app will be running on the pubic ip of Node server (EC2) with the port 49160 (ex: http://54.169.112.245:49160/)

Thanks for viewing this repo.
