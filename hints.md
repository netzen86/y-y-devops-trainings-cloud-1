# docker build . -t catgpt
# docker run --publish 8080:8080 --publish 9090:9090 catgpt
# docker tag catgpt cr.yandex/crpbccj0cfhnv6t6ocnd/catgpt:latest
# docker push cr.yandex/crpbccj0cfhnv6t6ocnd/catgpt:latest
sudo docker container logs {container id}

docker logs [container ID]
docker top [container ID]


# yc iam key create --service-account-name nz-catgpt-sa -o key.json

yc config set service-account-key key.json
yc config set cloud-id b1g0vh6uspd0m39d5er6
yc config set folder-id b1g5tv4fsuuk2l9gvd1p
