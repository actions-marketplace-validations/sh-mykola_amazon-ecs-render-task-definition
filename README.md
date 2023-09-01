## Amazon ECS "Render Task Definition" Action for GitHub Actions

Inserts the container definition into an Amazon ECS task definition JSON file, creating a new task definition file.

## Usage

```yaml
    - name: Render Amazon ECS task definition
      id: render-web-container
      uses: brunocascio/amazon-ecs-render-task-definition@v1
      with:
        task-definition: task-definition.json
        container-name: web
        image: amazon/amazon-ecs-sample:latest
        environment-variables: "LOG_LEVEL=info"
        aws-sm-name: MySecretName

    - name: Deploy to Amazon ECS service
      uses: aws-actions/amazon-ecs-deploy-task-definition@v1
      with:
        task-definition: ${{ steps.render-web-container.outputs.task-definition }}
        service: my-service
        cluster: my-cluster
```

## License Summary

This code is made available under the MIT license.
