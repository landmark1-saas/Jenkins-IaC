node
{
def mavenHome = tool name: "maven3.6.3"
stage('1.Clone the source code from gitHub')
{
git branch: 'development', credentialsId: '38ccc03a-a799-4058-9851-668e192c96d5', url: 'https://github.com/Ftakang1/maven-web-app.git'
}
stage('2. Build Package')
{
sh "${mavenHome}/bin/mvn clean package" 
// bat "${mavenHome}/bin/mvn clean package"   for windows system
}

stage('3. SonarQube CodeQualityReport')
{
sh "${mavenHome}/bin/mvn sonar:sonar" 
// bat "${mavenHome}/bin/mvn sonar:sonar"   for windows system
}

stage('4. UploadBuildArtifacts to Nexus')
{
// sh "${mavenHome}/bin/mvn clean deploy"
// bat "${mavenHome}/bin/mvn clean deploy" for a windows system
}
stage('5. Deploy To Tomcat')
{
// deploy adapters: [tomcat9(credentialsId: 'Tomcat-Credentials', path: '', url: 'http://15.223.2.102:8888/')], contextPath: null, war: '**/maven-web-app.war'
}
stage('6. Email Notification') 
{
emailext body: '''Hello,
Build status
Landmark Technology
+(647) 997 4389
''', recipientProviders: [developers()], subject: 'Build Status', to: 'fritabes04@gmail.com'
}
}
