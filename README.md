# nextjs-multistage

refrence : https://solomou.dev/multi-stage-production-dockerfile-for-next-js/

Thanks to solomou i can achive smaller size my docker images from 1 GB to less than 200 MB

so the basic dockerfile for nodejs is look like these 

```shell
FROM node:22-alpine
WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .

RUN npm run build

CMD npm start
```

but with these docker images its will make your docker images 1GB more, when using npm install its will generate node modules with size around 500MB. Then your npm run build will compile the app size around 300MB

![image](https://github.com/user-attachments/assets/6ef477ea-cf7f-4ac0-8a03-dc27372d948d)

and the node its self around 150 MB 

![{18101618-A1FB-43C1-BF5C-0AAC2A3E7DA3}](https://github.com/user-attachments/assets/4f9cc6da-ba0e-4f98-9a15-bfea1b99e80b)

so when build the image with basic docker file will generate around 1GB images size.
