FROM python:3.6.8

RUN apt-get update && apt-get -o Acquire::BrokenProxy="true" -o Acquire::http::No-Cache="true" -o Acquire::http::Pipeline-Depth="0" install -y libgl1-mesa-glx
ADD requirements.txt /

RUN pip install --upgrade pip
RUN pip install -r /requirements.txt

WORKDIR /app

EXPOSE 5000
CMD ["gunicorn", "app:app", "--bind", "0.0.0.0:5000", "--workers", "4", "--threads", "2"]


