PROJECT_PATH = ../../

deploy-local-frontend:
	docker build -t localhost:32000/frontend:1.0.0 -f "${PROJECT_PATH}/Dockerfile" "${PROJECT_PATH}"
	docker push localhost:32000/frontend:1.0.0
