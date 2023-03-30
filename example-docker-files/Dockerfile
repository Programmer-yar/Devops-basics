FROM node:12-alpine AS frontend-build-stage
WORKDIR /app
RUN npm i -g @angular/cli@12.2.14
COPY ./assets/fe/package.json /app/package.json
RUN npm install
COPY ./assets/fe/ /app/
RUN ng build --configuration production

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
CMD [ "./startup.sh" ]


