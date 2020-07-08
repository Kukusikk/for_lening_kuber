# docker build  -t sa-logic .
# docker run -d -p 5050:5000 sa-logic
FROM python:3.6.6-alpine
COPY sa /app
WORKDIR /app
RUN apk update && apk add libressl-dev gcc python3-dev build-base 
RUN pip install --upgrade pip
RUN pip3 install -r requirements.txt && \
    python3 -m textblob.download_corpora
EXPOSE 5000
ENTRYPOINT ["python3"]
CMD ["sentiment_analysis.py"]
