# rabbitmq-golang-docker-example
The purpose of this project is to create a simple sender and receiver for RabbitMQ using Docker.

# Introduction
The project is composed of two files: *send.go* and *receive.go*.

* *send.go*: On this file we start a connection with RabbitMQ, create a queue and send a message to the queue.
* *receive.go*: On this file we start a connect with RabbitMQ, start listening the queue, and print messages from the queue.

# How to run
There are some steps to follow in order to run the code.

**Docker**

Start RabbitMQ on docker
 
`docker run -d -p 5672:5672 --hostname my-rabbit --name some-rabbit rabbitmq:3`

The command above will start a RabbitMQ docker container attaching the container port to the local machine port (5672), so it wil lbe possible to access RabbitMQ from local machine. 

**Golang**

First of all, we should have the RabbitMQ lib for *golang* installed on your machine. Run:

`go get github.com/streadway/amqp`

Now, just run the sender, in order to add some message to the queue.

`go run send.go`

It should be shown something like this on the terminal:

`2019/05/30 08:28:47  [x] Sent Hello World!`

The last step is to run the receiver, which will stay listening on the queue until the process is killed.

`go run receive.go`

It should be shown something like this on the terminal:

```
2019/05/30 08:33:04  [*] Waiting for messages. To exit press CTRL+C
2019/05/30 08:33:04 Received a message: Hello World!
```

# Conclusion

Golang has a nice library to deal with RabbitMQ. It is pretty straightforward.

Of course, there are several different usages for queues, and this a simple one. As much as I start studying, I will add more examples.
