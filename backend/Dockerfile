FROM python:3.8
WORKDIR /usr/src/app
COPY requirements.txt ./requirements.txt
COPY run.py ./run.py
COPY start-backend.sh ./start-backend.sh
COPY guess ./guess
COPY repository ./repository
RUN pip install --no-cache-dir -r requirements.txt
RUN chmod +x start-backend.sh
# EXPOSE 5001
CMD ["./start-backend.sh"]