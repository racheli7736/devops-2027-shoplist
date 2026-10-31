
FROM python:3.11-slim

WORKDIR /app

RUN apt-get update && apt-get install -y --no-install-recommends ca-certificates && rm -rf /var/lib/apt/lists/*

COPY netfree.crt /usr/local/share/ca-certificates/netfree.crt

RUN update-ca-certificates

ENV PIP_CERT=/etc/ssl/certs/ca-certificates.crt

COPY requirements.txt .

RUN pip install --no-cache-dir --trusted-host pypi.org --trusted-host files.pythonhosted.org -r requirements.txt
COPY app.py .

EXPOSE 5000

CMD ["python", "app.py"]
