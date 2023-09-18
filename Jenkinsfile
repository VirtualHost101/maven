pipeline
{
 agent any
 stages
 {
        stage('contdownload')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/maven.git'
            }
        }
        stage('contbuild')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('conttest-deployment')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: '5a6ea5e4-7879-443d-b2b8-ebf2af1f098b', path: '', url: 'http://172.31.21.163:8080')], contextPath: 'test1', war: '**/*.war'
            }
        }
        stage('conttestdownload')
        {
            steps
            {
               git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
            }
        }
        stage('conttestpackage')
        {
            steps
            {
               sh 'java -jar /var/lib/jenkins/workspace/declarative/testing.jar'
            }
        }
        stage('contprod-deployment')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: '5a6ea5e4-7879-443d-b2b8-ebf2af1f098b', path: '', url: 'http://172.31.21.163:8080')], contextPath: 'tt1', war: '**/*.war'
            }
        }
 }
}