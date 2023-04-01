# These files are taken from wellness app
# FROM <image>, node is a base image in this case
# Our image will be based on node:12-alpine image
# If we check the Dockerfile of node:12-alpine image, we will see it is based on alpine image
# this will install node in the container which will be available in container terminal
FROM node:12-alpine AS frontend-build-stage
WORKDIR /app

# lets us run linux commands in container environment only
RUN npm i -g @angular/cli@12.2.14

# copy files from host machine to container, basically executes on host
COPY ./assets/fe/package.json /app/package.json
RUN npm install
COPY ./assets/fe/ /app/
RUN ng build --configuration production

# python is base image
# This will install python version 3.10.2
FROM python:3.10.2 AS production-stage
WORKDIR /app
RUN python3 -m pip install --upgrade pip
RUN pip install wheel
RUN pip install Pillow
COPY requirements.txt /app/requirements.txt
RUN pip install -r requirements.txt
COPY . /app/
COPY --from=frontend-build-stage /app/dist/ /app/assets/fe/dist/ 
RUN python manage.py collectstatic
RUN chmod a+x /app/startup.sh
EXPOSE 8000

# executes entry point linux commands
CMD [ "./startup.sh" ]


