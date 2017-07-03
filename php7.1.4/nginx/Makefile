PROJECT := project
DOCKER_COMPOSE_FILES_OPTIONS := -f docker-compose.yml
DOCKER_COMPOSE_OPTIONS := $(DOCKER_COMPOSE_FILES_OPTIONS)
TIME := $(shell /bin/date "+%Y-%m-%d--%H-%M-%S")

# Construire et démarrer les machines virtuelles
restart:
	make stop $(c)
	make start $(c)
start:
	docker-compose $(DOCKER_COMPOSE_OPTIONS) start $(c)
up:
	docker-compose $(DOCKER_COMPOSE_OPTIONS) up -d $(c)
build:
	docker-compose $(DOCKER_COMPOSE_OPTIONS) build $(c)
stop:
	docker-compose $(DOCKER_COMPOSE_OPTIONS) stop $(c)
clean:
	make stop
	docker network rm $(shell docker network ls | grep $(PROJECT) | awk '{print $$1}')
	docker rm $(shell docker ps -a -q)
clean-full:
	make stop
	docker rmi $(shell docker images | grep $(PROJECT) | awk '{print $$1}')
logs:
	docker-compose $(DOCKER_COMPOSE_OPTIONS) logs -f $(c)

# Se loguer sur les conteneurs
exec:
	docker-compose $(DOCKER_COMPOSE_OPTIONS) exec $(c) bash
cli:
	docker-compose $(DOCKER_COMPOSE_OPTIONS) exec cli bash
exec-php:
	docker-compose $(DOCKER_COMPOSE_OPTIONS) exec php bash
exec-nginx:
	docker-compose $(DOCKER_COMPOSE_OPTIONS) exec nginx bash
run:
	docker-compose $(DOCKER_COMPOSE_OPTIONS) run $(C) bash
shell-command:
	@echo docker-compose $(DOCKER_COMPOSE_OPTIONS) exec -T cli
