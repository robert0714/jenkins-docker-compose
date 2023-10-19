#  Jenkins Mirror Sites 
* cn 
  * http://mirrors.tuna.tsinghua.edu.cn/jenkins/
* jp
  * http://ftp.yz.yamagata-u.ac.jp/pub/misc/jenkins/
  * http://mirror.esuni.jp/jenkins/
* us 
  * ftp://mirror.xmission.com/jenkins/
  * http://mirror.xmission.com/jenkins/
  * http://archives.jenkins-ci.org/
  * ftp://ftp-chi.osuosl.org/pub/jenkins/
  * http://ftp-chi.osuosl.org/pub/jenkins/

# Manually install plugins
## Examples
```bash
docker exec -it jenkins bash
export JENKINS_UC_DOWNLOAD=http://ftp.yz.yamagata-u.ac.jp/pub/misc/jenkins/
jenkins-plugin-cli --verbose -d $JENKINS_HOME/plugins/ --plugins cloudbees-folder
```
## Jenkins Recommended Plugins
* https://plugins.jenkins.io/cloudbees-folder
* https://plugins.jenkins.io/antisamy-markup-formatter
* https://plugins.jenkins.io/build-timeout
* https://plugins.jenkins.io/credentials-binding
* https://plugins.jenkins.io/timestamper
* https://plugins.jenkins.io/ws-cleanup
* https://plugins.jenkins.io/ant
* https://plugins.jenkins.io/gradle
* https://plugins.jenkins.io/workflow-aggregator
* https://plugins.jenkins.io/github-branch-source
* https://plugins.jenkins.io/pipeline-github-lib
* https://plugins.jenkins.io/pipeline-stage-view
* https://plugins.jenkins.io/git
* https://plugins.jenkins.io/ssh-slaves
* https://plugins.jenkins.io/matrix-auth
* https://plugins.jenkins.io/pam-auth
* https://plugins.jenkins.io/ldap
* https://plugins.jenkins.io/email-ext
* https://plugins.jenkins.io/mailer
## Using jenkins-plugin-cli
```bash
docker exec -it jenkins bash
export JENKINS_UC_DOWNLOAD=http://ftp.yz.yamagata-u.ac.jp/pub/misc/jenkins/

jenkins-plugin-cli -d $JENKINS_HOME/plugins/ --plugins cloudbees-folder antisamy-markup-formatter build-timeout credentials-binding timestamper ws-cleanup ant gradle workflow-aggregator github-branch-source pipeline-github-lib pipeline-stage-view git ssh-slaves matrix-auth pam-auth ldap email-ext mailer locale

exit

docker restart jenkins
```
### Install Pluging - Pipeline: AWS Steps
* Reference:
  * https://plugins.jenkins.io/pipeline-aws/
  * https://dev.to/aws-builders/how-to-set-up-jenkins-and-a-pipeline-on-aws-2pak
* Using jenkins-plugin-cli (including dependncies):
  ```bash
  docker exec -it jenkins bash
  export JENKINS_UC_DOWNLOAD=http://ftp.yz.yamagata-u.ac.jp/pub/misc/jenkins/

  jenkins-plugin-cli -d $JENKINS_HOME/plugins/ --plugins  jdk-tool aws-java-sdk-sqs aws-java-sdk-sns \
  aws-java-sdk-cloudformation aws-java-sdk-elasticbeanstalk \
  aws-java-sdk-ecs aws-java-sdk-iam aws-java-sdk-ecr \
  aws-java-sdk-efs aws-java-sdk-ssm aws-java-sdk-kinesis \
  aws-java-sdk-logs aws-java-sdk-codebuild \
  aws-java-sdk-secretsmanager  \
  aws-java-sdk \
  pipeline-aws
  ```
  * ⚠ **aws-java-sdk** is too big ( 265 MB ) . You can [direct download it](https://plugins.jenkins.io/aws-java-sdk/releases/).
