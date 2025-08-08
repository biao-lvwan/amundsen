docker build -t amundsen/amundsensearch:v0.0.1 -f Dockerfile.search.public .

docker build -t amundsen/amundsenmetadata:v0.0.1 -f Dockerfile.metadata.public .

docker build -t amundsen/amundsenfrontend:v0.0.1 -f Dockerfile.frontend.public .

docker build --build-arg SEARCHSERVICE_BASE=http://amundsensearch:5001 --build-arg METADATASERVICE_BASE=http://amundsenmetadata:5002  -t amundsen/amundsenfrontend-local:v0.0.1 -f Dockerfile.frontend.local .


docker-compose -f docker-amundsen-local.yml up -d 


conda activate amundsen

pip install -r requirements-common.txt

# 使用hive等
https://www.jianshu.com/p/93f4dbf480ce