FROM python:3.9.1-buster

EXPOSE 5000

WORKDIR /app

COPY . /app
RUN pip install --upgrade pip
RUN pip install -r requirements.txt

ENTRYPOINT ["python"]
CMD ["main.py"]