#set a base image
FROM python:3.11.13-alpine3.22
#Working directory
WORKDIR /usr/src/app


#Copy vs Add?
COPY . . /usr
# Run execute build command during docke image build 
RUN /bin/sh -c pip install -r project.yaml


RUN adduser pythonuser -s /sbin/nologin --disabled-password


#Prevent writing PYC files
ENV PYTHONDONTWRITEBYTECODE=1
ENV PYTHONUNBUFFERED=1




#Switch to user
USER pythonuser


#Aplication Port
EXPOSE 8000


#start application - ENTRYPOINT vs CMD
#If CMD and entrypoint is used together, CMD is a passing argument to ENTRYPOINT


CMD uvicorn main:app --reload --host 0.0.0.0
#Instraction used to start application, container or process
