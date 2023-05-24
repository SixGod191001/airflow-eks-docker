# airflow-eks-docker
Airflow Docker image used in AWS EKS cluster


## How to run the unittest locally
  - cd ~/environment
  - docker build -t airflow-test airflow-eks-docker/
  - docker images ls
  - docker run --rm airflow-test bash -c "airflow db init && pytest unittests/test_dag_validation.py"


## How to run the unittest on codepipeline
  - aws cloudformation update-stack --stack-name=airflow-dev-pipeline --template-body=file://airflow-materials-aws/section-6-cicd-pipeline/code-pipeline/airflow-dev-pipeline.cfn.yml --parameters ParameterKey=GitHubUser,ParameterValue=$GIT_USERNAME ParameterKey=GitHubToken,ParameterValue=$GITHUB_TOKEN ParameterKey=GitSourceRepo,ParameterValue=airflow-eks-docker ParameterKey=GitBranch,ParameterValue=dev
  - edit docker file and the pipeline will be auto triggered.