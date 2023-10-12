# Build
custom_build(
    # Name of the container image
    ref = 'ghcr.io/corlovito/spring_k8s:latest',
    #ref = 'catalog-service',
    # Command to build the container image
    #command = './gradlew bootBuildImage --imageName ghcr.io/corlovito/spring_k8s:latest',
    command = './gradlew bootBuildImage --imageName $EXPECTED_REF',
    # Files to watch that trigger a new build
    deps = ['build.gradle', 'src']
)

# Deploy
k8s_yaml(['k8s/deployment.yml', 'k8s/service.yml'])

# Manage
k8s_resource('catalog-service', port_forwards=['9001'])
allow_k8s_contexts('kubernetes-admin@kubernetes')
