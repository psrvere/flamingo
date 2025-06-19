# Context

## BuildConfig

BuildConfig folder has documentation for Openshift BuildConfig product

## Builds

Builds has documentation for Openshift Builds product.
Builds used Shipwright codebase as is under the hood.

## Shipwright

Shipwright/build folder has the codebase for Shipwright.
Shipwright/website folder has the documentation for Shipwright in content/docs folder.

## OpenshiftTestsWithBuildConfig

OpenshiftTestsWithBuildConfig/builds-test folder has the tests for Openshift Builds product.
OpenshiftTestsWithBuildConfig/builds-testdata folder has the test data for Openshift Builds product.

# Instructions for LLM:

1. List down all the tests in OpenshiftTestsWithBuildConfig/builds-test folder in a markdown format. I should be able to copy paste the tests in a new markdown file. - This is done
2. Look at the list belowand list down all the tests in each file in a markdown format and add to this file below each file name in the list and indent the tests with 4 spaces. - This is done
3. Look at each test in each test file and add the resource requirements for each test below the test. Indent the resource requirements with 4 spaces. Use this format: [Resources][Before - ABC, XYZ][During - YUT]. Do this only for the first file.
4. We want to migrate BuildConfig to Builds. For each of the following tests, we need to create new yaml files buildstest/build-testdata/abc folder where abc is the test name matching folders in buildconfigtests/builds-testdata folder. Let's do this for the first test. The files are already created for the first test. What's the best way to represent this visually?

# Openshift Builds Tests in each test file

1. **build_pruning.go** - Tests for build pruning functionality [Before - ImageStream, BuildConfig]
    - should prune completed builds based on the successfulBuildsHistoryLimit setting
    - should prune failed builds based on the failedBuildsHistoryLimit setting
    - should prune canceled builds based on the failedBuildsHistoryLimit setting
    - should prune errored builds based on the failedBuildsHistoryLimit setting
        - Basic Structure --> 
        - Retention Configuration
        - Source Configuration
        - Strategy Configuration
        - Output Configuration
    - should prune builds after a buildConfig change
    - buildconfigs should have a default history limit set when created via the group api
2. **build_timing.go** - Tests for build timing and duration
    - should record build stages and durations for s2i
    - should record build stages and durations for docker
3. **buildconfigsecretinjector.go** - Tests for secret injection in build configs
    - should inject secrets to the appropriate buildconfigs
4. **cluster_config.go** - Tests for cluster configuration
    - should default registry search to docker.io for image pulls
    - should apply registry blacklist configuration
    - should apply registry whitelist configuration
    - should apply proxy configuration
    - should apply resource configuration
    - should apply invalid proxy configuration
    - should apply build defaults configuration
5. **completiondeadlineseconds.go** - Tests for build completion deadline settings
    - Source: should start a build and wait for the build failed and build pod being killed by kubelet
    - Docker: should start a build and wait for the build failed and build pod being killed by kubelet
6. **contextdir.go** - Tests for build context directory handling
    - should s2i build an application using a context directory
    - should docker build an application using a context directory
7. **controller_compat.go** - Tests for controller compatibility
    - should succeed (RunBuildCompletePodDeleteTest)
    - should succeed (RunBuildDeleteTest)
    - should succeed (RunBuildRunningPodDeleteTest) [skipped]
8. **controllers.go** - Tests for build controllers
    - RunImageChangeTriggerTest - Tests image change trigger functionality
    - RunBuildDeleteTest - Tests build deletion functionality
    - RunBuildRunningPodDeleteTest - Tests running pod deletion functionality
    - RunBuildCompletePodDeleteTest - Tests completed pod deletion functionality
    - RunBuildConfigChangeControllerTest - Tests build config change controller functionality
9. **custom_build.go** - Tests for custom build functionality
    - should complete build with custom builder image
10. **digest.go** - Tests for image digest handling
    - S2I build started with normal log level
        - should save the image digest when finished
    - S2I build started with log level >5
        - should save the image digest when finished
    - Docker build started with normal log level
        - should save the image digest when finished
    - Docker build started with log level >5
        - should save the image digest when finished
11. **docker_pullsearch.go** - Tests for Docker pull search functionality
    - should create a docker build that has buildah search from our predefined list of image registries and succeed
12. **docker_pullsecret.go** - Tests for Docker pull secret handling
    - should create a docker build that pulls using a secret run it
13. **dockerfile-test.go** - Tests for Dockerfile build functionality
    - should create a image via new-build
    - should create a image via new-build and infer the origin tag
    - should be able to start a build from Dockerfile with FROM reference to scratch
    - testing build image with invalid dockerfile content
    - testing build image with dockerfile contains a file path uses a variable in its name
14. **failure_status.go** - Tests for build failure status handling
    - should contain the post commit hook failure reason and message
    - should contain the Docker build fetch image content reason and message
    - should contain the Docker build fetch source failure reason and message
    - should contain the S2I fetch source failure reason and message
    - should contain OutOfMemoryKilled failure reason and message
15. **gitauth.go** - Tests for Git authentication
    - should be able to clone source code via an HTTP token
    - should be able to clone source code via ssh
    - should be able to clone source code via ssh using SCP-style URIs
16. **hooks.go** - Tests for build hooks
    - should run s2i postCommit hooks
    - should run docker postCommit hooks
17. **image_source.go** - Tests for image source handling
    - buildconfig with input source image and s2i strategy
        - should complete successfully and contain the expected file
    - buildconfig with input source image and docker strategy
        - should complete successfully and contain the expected file
    - creating a build with an input source image and s2i strategy
        - should resolve the imagestream references and secrets
    - creating a build with an input source image and docker strategy
        - should resolve the imagestream references and secrets
18. **imagechangetriggers.go** - Tests for image change triggers
    - imagechangetriggers should trigger builds of all types
19. **labels.go** - Tests for build labels
    - S2I build from a template
        - should create a image from template with proper Docker labels
    - Docker build from a template
        - should create a image from template with proper Docker labels
20. **multistage.go** - Tests for multi-stage builds
    - should succeed with multi-stage Docker build
        - creates a build with multiple stages
        - verifies build logs and success
        - tests the resulting image with curl and file checks
21. **new_app.go** - Tests for new application builds
    - should succeed with a --name of 58 characters
    - should fail with a --name longer than 58 characters
    - should succeed with an imagestream
22. **no_outputname.go** - Tests for builds without output names
    - building from templates
        - should create an image from a docker template without an output image reference defined
        - should create an image from a S2i template without an output image reference defined
23. **nosrc.go** - Tests for builds without source
    - started build
        - should build even with an empty source in build config
24. **optimized.go** - Tests for optimized builds
    - should succeed with optimized image builds
        - creates a build with skip layers optimization
        - verifies build logs and success
        - checks for installed packages and environment variables
25. **pipeline_origin_bld.go** - Tests for pipeline origin builds
    - jenkins pipeline build config strategy
        - using a jenkins instance launched with the ephemeral template
            - should build and complete successfully
            - verifies job logs and success message
26. **proxy.go** - Tests for proxy settings
    - should start an s2i build and wait for the build to succeed with broken proxy and no_proxy override
    - should start a docker build and wait for the build to succeed with broken proxy and no_proxy override
    - should mount the custom PKI into the build if specified
27. **pullsecret.go** - Tests for pull secret handling
    - should be able to use a pull secret in a build
28. **remove_buildconfig.go** - Tests for build config removal
    - should start builds and delete the buildconfig
29. **revision.go** - Tests for build revision handling
    - should contain source revision information
30. **run_fs_verification.go** - Tests for filesystem verification
    - should not have unexpected content using a simple Docker Strategy Build
    - should be writeable using a simple Docker Strategy Build
31. **run_policy.go** - Tests for build run policies
    - should handle build run policies correctly
32. **s2i_dropcaps.go** - Tests for S2I drop capabilities
    - should not be able to switch to root with an assemble script
33. **s2i_env.go** - Tests for S2I environment variables
    - should create a image from template and run it in a pod
34. **s2i_incremental.go** - Tests for S2I incremental builds
    - should create a build from template and run it
    - should create a build using the image produced by the last build
    - should instantiate a pod and service with the new image
35. **s2i_quota.go** - Tests for S2I quota handling
    - should create an s2i build with a quota and run it
    - should verify build logs contain correct cgroups values
36. **s2i_root.go** - Tests for S2I root user handling
    - should create a root build and fail without a privileged SCC
    - should create a root build and pass with a privileged SCC
37. **secrets.go** - Tests for secret handling
    - should contain secrets during the source strategy build
38. **service.go** - Tests for build service
    - should be able to run a build that references a cluster service
39. **start.go** - Tests for build start functionality
    - should accept --from-dir as input
    - should accept --from-repo as input
    - should accept --from-file with https URL as an input
    - should accept --from-archive with https URL as an input
    - should checkout the config branch, not config directory
40. **subscription_content.go** - Tests for subscription content
    - should succeed for RHEL 7 base images
    - should succeed for RHEL 8 base images
    - should succeed for RHEL 9 base images
41. **valuefrom.go** - Tests for value from functionality
    - should successfully resolve valueFrom in s2i build environment variables
    - should successfully resolve valueFrom in docker build environment variables
    - should fail resolving unresolvable valueFrom in sti build environment variable references
    - should fail resolving unresolvable valueFrom in docker build environment variable references
42. **volumes.go** - Tests for volume handling
    - should mount given secrets and configmaps into the build pod for source strategy builds
    - should mount given secrets and configmaps into the build pod for docker strategy builds
43. **webhook.go** - Tests for webhook functionality
    - should handle generic webhooks
    - should handle github webhooks
    - should handle gitlab webhooks
    - should handle bitbucket webhooks
    - should reject unauthenticated webhook requests

## Note
This list contains all test files found in the OpenshiftTestsWithBuildConfig/builds-test directory. Each test file focuses on a specific aspect of the Openshift Builds product functionality.
