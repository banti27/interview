#Steps to follow when deploying a new application in heroku

https://devcenter.heroku.com/articles/deploying-spring-boot-apps-to-heroku

***
Creating app... done, ⬢ tranquil-shelf-44550
https://tranquil-shelf-44550.herokuapp.com/ | https://git.heroku.com/tranquil-shelf-44550.git
***
  
### After getting this error

```
 Failed to execute goal org.apache.maven.plugins:maven-compiler-plugin:3.8.1:compile (default-compile) on project speedbreaker-service: Fatal error compiling: invalid target release: 15 -> [Help 1]
```

We have to add **system.properties** file in root folder and pass the value **java.runtime.version=$yourCurrentJavaVersion**
