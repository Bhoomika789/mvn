//program 6
pipeline {
    agent any

    stages {
        stage('SCM') {
            steps {
               git branch: 'main', url: 'https://github.com/Bhoomika789/mvn.git'
            }
        }
       stage('BUILD'){
    steps{
        bat """
        cd "E:\\aws & devops\\apache-maven-3.9.9\\bin"
        mvn clean install
        """
    }
}

    }
}
//program 2
pom.xml file

<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>org.example</groupId>
    <artifactId>sample_vtricks</artifactId>
    <version>1.0-SNAPSHOT</version>

    <dependencies>
        <dependency>
            <groupId>org.junit.jupiter</groupId>
            <artifactId>junit-jupiter-api</artifactId>
            <version>5.9.2</version>
            <scope>test</scope>
        </dependency>
    </dependencies>

    <properties>
        <maven.compiler.source>17</maven.compiler.source>
        <maven.compiler.target>17</maven.compiler.target>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
    </properties>

    <build>
        <plugins>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-compiler-plugin</artifactId>
                <version>3.8.1</version>
                <configuration>
                    <source>17</source>
                    <target>17</target>
                </configuration>
            </plugin>

            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-jar-plugin</artifactId>
                <version>3.2.0</version>
                <configuration>
                    <archive>
                        <manifest>
                            <mainClass>org.example.Main</mainClass>
                        </manifest>
                    </archive>
                </configuration>
            </plugin>
        </plugins>
    </build>

</project>

//program 3
Build.gradle file
plugins {
    id 'java'
    id 'application'  // Add this line
}
group = 'org.example'
version = '1.0-SNAPSHOT'
repositories {
    mavenCentral()
}
dependencies {
    testImplementation platform('org.junit:junit-bom:5.10.0')
    testImplementation 'org.junit.jupiter:junit-jupiter'
}
test {
    useJUnitPlatform()
}
application {
    mainClass = 'org.example.Main'  // Specify the main class
}
jar {
    manifest {
        attributes(
                'Main-Class': 'org.example.Main' // Specify the main class here as well
        )
    }
}
