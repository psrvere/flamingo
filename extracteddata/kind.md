This file extracted all the kinds from the testdata files. Here are the unique kinds

Unique Kinds:
- BuildConfig
- ImageStream
- ImageStreamTag
- List
- Secret
- ConfigMap
- Template
- DockerImage
- DeploymentConfig
- Service

Instructions for LLM:

1. Process all YAML and JSON files in buildconfigtests/builds-testdata folder in the order specified by readme.md
2. For each file/folder:
   - Extract all 'kind' fields from YAML/JSON files
   - Format as "folder: name (file_count)" or "file: name.ext"
   - List extracted kinds indented below
   - Add "verified: true" for processed items
3. For subfolders:
   - Include all kinds from contained files under the folder entry
   - Skip individual file entries for subfolder contents
4. Skip processing if "verified: true" tag exists
5. Remove any folders that don't exist
6. Add any missing files/folders from builds-testdata

folder: build-pruning (8 files): verified: true
    - BuildConfig
    - ImageStream

folder: build-timing (5 files): verified: true
    - BuildConfig
    - ImageStream
    - ImageStreamTag

folder: webhook/generic/testdata (5 files): verified: true
    - BuildConfig
    - ImageStream
    - Secret

folder: webhook/github/testdata (3 files): verified: true
    - BuildConfig
    - ImageStream
    - Secret

folder: webhook/gitlab/testdata (2 files): verified: true
    - BuildConfig
    - ImageStream
    - Secret

folder: webhook/bitbucket/testdata (4 files): verified: true
    - BuildConfig
    - ImageStream
    - Secret

folder: volumes (8 files): verified: true
    - BuildConfig
    - ImageStream
    - Secret
    - ConfigMap

folder: valuefrom (7 files): verified: true
    - BuildConfig
    - ImageStream
    - Secret
    - ConfigMap

folder: test-build-app (4 files): verified: true
    - BuildConfig
    - ImageStream
    - DeploymentConfig
    - Service

folder: subscription-content (3 files): verified: true
    - BuildConfig
    - ImageStream

folder: statusfail-assemble (2 files): verified: true
    - BuildConfig
    - ImageStream

folder: s2i-environment-build-app (4 files): verified: true
    - BuildConfig
    - ImageStream
    - DeploymentConfig
    - Service

folder: jenkins-pipeline (3 files): verified: true
    - BuildConfig
    - ImageStream
    - Template

folder: pullsecret (3 files): verified: true
    - BuildConfig
    - ImageStream
    - Secret

folder: docker-add (2 files): verified: true
    - BuildConfig
    - ImageStream

folder: custom-build (2 files): verified: true
    - BuildConfig
    - ImageStream

folder: cluster-config (2 files): verified: true
    - BuildConfig
    - ImageStream

folder: build-secrets (3 files): verified: true
    - BuildConfig
    - ImageStream
    - Secret

folder: build-quota (2 files): verified: true
    - BuildConfig
    - ImageStream

folder: build-postcommit (2 files): verified: true
    - BuildConfig
    - ImageStream

file: test-build.yaml: verified: true
    - List
    - ImageStream
    - Secret
    - BuildConfig
    - DockerImage

file: test-build-proxy.yaml: verified: true
    - List
    - ImageStream
    - BuildConfig
    - ImageStreamTag

file: test-auth-build.yaml: verified: true
    - Template
    - ImageStream
    - BuildConfig
    - ImageStreamTag

file: test-bc-with-pr-ref.yaml: verified: true
    - List
    - ImageStream
    - BuildConfig
    - ImageStreamTag

file: statusfail.yaml: verified: true
    - BuildConfig

file: simple-pipeline-bc.yaml: verified: true
    - BuildConfig

file: test-symlink-build.yaml: verified: true
    - BuildConfig
    - ImageStream

file: test-s2i-build-quota.json: verified: true
    - BuildConfig
    - ImageStream

file: test-s2i-build.json: verified: true
    - BuildConfig
    - ImageStream

file: test-s2i-no-outputname.json: verified: true
    - BuildConfig
    - ImageStream

file: test-imageresolution-docker-build.yaml: verified: true
    - BuildConfig
    - ImageStream

file: test-imageresolution-s2i-build.yaml: verified: true
    - BuildConfig
    - ImageStream

file: test-imagesource-buildconfig.yaml: verified: true
    - BuildConfig
    - ImageStream
    - ImageStreamTag

file: test-nosrc-build.json: verified: true
    - BuildConfig
    - ImageStream

file: test-image-stream.json: verified: true
    - ImageStream

file: test-imagechangetriggers.yaml: verified: true
    - BuildConfig
    - ImageStream
    - ImageStreamTag

file: test-imageresolution-custom-build.yaml: verified: true
    - BuildConfig
    - ImageStream

file: test-docker-build-pullsecret.json: verified: true
    - BuildConfig
    - ImageStream
    - Secret

file: test-docker-build.json: verified: true
    - BuildConfig
    - ImageStream

file: test-docker-no-outputname.json: verified: true
    - BuildConfig
    - ImageStream

file: test-env-build.json: verified: true
    - BuildConfig
    - ImageStream

file: test-cds-dockerbuild.json: verified: true
    - BuildConfig
    - ImageStream

file: test-cds-sourcebuild.json: verified: true
    - BuildConfig
    - ImageStream

file: test-context-build.json: verified: true
    - BuildConfig
    - ImageStream
    - ImageStreamTag
    - DeploymentConfig
    - Service

file: test-custom-build.yaml: verified: true
    - BuildConfig
    - ImageStream

file: test-build-search-registries.yaml: verified: true
    - BuildConfig
    - ImageStream

file: test-buildconfigsecretinjector.yaml: verified: true
    - List
    - Secret
    - BuildConfig
    - ImageStream

file: test-build-cluster-config.yaml: verified: true
    - BuildConfig
    - ImageStream

file: test-build-podsvc.json: verified: true
    - BuildConfig
    - ImageStream
    - Service

file: test-build-revision.json: verified: true
    - BuildConfig
    - ImageStream