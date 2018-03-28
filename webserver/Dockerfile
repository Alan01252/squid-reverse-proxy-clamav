FROM python:2.7
ADD server.py /
ADD server.pem /
RUN pip install pystrich 
CMD [ "python", "./server.py" ]
