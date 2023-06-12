# ecs_composite_action
# Arguments needs to be passed for using this plugin
    AWS_ACCESS_KEY_ID:  your_aws_access_key
    AWS_SECRET_ACCESS_KEY: your_aws_secret_key
    AWS_REGION: your_aws_region
    AWS_TASK_DEFINTION: your_aws_task_name
    ECS_CLUSTER: your_aws_cluster_name
    ECS_SERVICE: your_aws_service_name
    CONTAINER_NAME: your_aws_container_name
    Dockerimage: your_docker_image_name
# Sample pipeline example
       steps:
       - name: checkout repo
         uses: actions/checkout@v2
       - name: build image
         run: |
          docker build -t Dockerimage:latest .
        
      - name: configure aws ecs pipeline
        uses: actions/ecs_composite_action@main
        with:
          AWS_ACCESS_KEY_ID: ${{ secrets.AWS_ACCESS_KEY_ID }}
          AWS_SECRET_ACCESS_KEY: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
          AWS_REGION: ${{ secrets.AWS_REGION }}
          AWS_TASK_DEFINTION: ${{ secrets.AWS_TASK_DEFINTION }}
          ECS_CLUSTER: ${{ secrets.ECS_CLUSTER }}
          ECS_SERVICE: ${{ secrets.ECS_CLUSTER }}
          CONTAINER_NAME: ${{ secrets.CONTAINER_NAME }}
          Dockerimage: Dockerimage:latest
