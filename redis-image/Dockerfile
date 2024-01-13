# Use an existing Docker image as a base
FROM alpine

# Downlaod and install dependency
RUN apk add --update redis

# Tell the image what to do when it starts as a container
CMD ["redis-server"]
