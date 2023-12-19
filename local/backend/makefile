PROJECT_PATH = ../../

deploy-local-users:
	CGO_ENABLE=0 GOOS=linux GOARCH=amd64 go build -p app .
	docker build -t localhost:32000/users.core.test:1.0.0 -f "${PROJECT_PATH}Dockerfile" .
	docker push localhost:32000/users.core.test:1.0.0
	rm -rf app
