node {
    stage 'checkout'
        echo 'Hello chekcing out first ...'
        checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/NaughtyPhil/maven-jenkins.git']]])

    stage 'build'
        echo 'Beging building...'
        def mvnHome = tool 'M3'
        sh '/Users/phil/Java/apache-maven-3.1.1/bin/mvn -Dmaven.test.failure.ignore clean test package"
        step([$class: 'JUnitResultArchiver', testResults: '**/target/surefire-reports/TEST-*.xml'])
}
