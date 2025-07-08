FROM python:3.11.13-alpine3.22
#Working directory
WORKDIR /usr/src/app
RUN apk add --no-cache gcc musl-dev libffi-dev openssl-dev python3-dev

# Copy requirements folder and main file
COPY requirements ./requirements
COPY requirements.txt .

RUN pip install --no-cache-dir -r requirements.txt

COPY manage.py /usr/src/app/manage.py
COPY fabric.yaml /usr/src/app/fabric.yaml


# Run execute build command during docke image build 
RUN pip install -r requirements.txt


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
