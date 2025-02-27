FROM python:3.9

WORKDIR /app

RUN mkdir -p /tmp/thriftpy_compat && \
    echo 'import thriftpy2 as thriftpy' > /tmp/thriftpy_compat/thriftpy.py && \
    echo 'from thriftpy2 import *' >> /tmp/thriftpy_compat/thriftpy.py

# Install requirements with thriftpy2
COPY requirements.txt .
RUN pip install --upgrade pip setuptools wheel && \
    pip install -r requirements.txt

# Ensure the compatibility layer is in Python's import path
ENV PYTHONPATH=/tmp/thriftpy_compat:/usr/local/lib/python3.9/site-packages

COPY . .

CMD ["python", "main.py"]