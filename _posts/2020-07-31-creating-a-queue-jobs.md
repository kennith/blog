---
title: Creating a Queue Jobs
layout: post
categories: ["programming"]
---

The Laravel Queue is very powerful, but if you are not processing a job from Laravel, it will not work.

The setup below is an idea on how to create a queue worker and setup a runner.

## Create a worker to retrieve message from SQS.

```php
// Retreive messages
$works = $this->sqsClient->receiveMessage([
    'MaxNumberOfMessages' => 1,
    'QueueUrl' => '<your-queue-url',
])->get('Messages');

foreach ($works as $work) {
    // Run the job
    // If the job ran successfully, remove the message from SQS.
}
```

## Make a command to run the worker

```php
//...
while (true) {
    $worker = new Worker();
    $worker->run();
    sleep(5); // A delay is optional.
}
```

## Configure supervisor

```ini
[program:worker]
process_name=%(program_name)s_%(process_num)02d
command=php /path-to-app/artisan app:run-worker
autostart=true
autorestart=true
user=ubuntu
numprocs=2
redirect_stderr=true
stdout_logfile=/path-to-app/worker.log
stopwaitsecs=3600
```
