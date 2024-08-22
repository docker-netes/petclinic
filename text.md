mvn deploy -s settings.xml #ok do
gradle build -Pmaven.settings.location=$(Agent.TempDirectory)/settings.xml

edit build.gradle

tasks.withType(JavaCompile) {
    options.encoding = 'UTF-8'
}
if (project.hasProperty('maven.settings.location')) {
    mavenSettings {
        userSettingsFileName = project.property('maven.settings.location')
    }
}
