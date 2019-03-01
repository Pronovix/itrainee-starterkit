# iTrainee starter kit

This repository is using Amazee's containers.

## Setup

### Clone the repository

```
git clone https://github.com/Pronovix/itrainee-starterkit.git local
```

### Requirements

* git
* docker

### Install and start pygmy (Linux and macOS only)

To install `pygmy`, run `gem install pygmy`. This is only needed if you don't already have `pygmy` installed.

Start pygmy: `pygmy up` 

## Usual commands

* `docker-compose run --rm cli sh`

  To run commands inside the container.
  
* `docker-compose up -d`

  Starts the containers.
  
* `docker-compose stop`

  Shuts down the containers (keeps the state).
  
* `docker-compose down`

  Destroys the containers (permanently deletes the state).
