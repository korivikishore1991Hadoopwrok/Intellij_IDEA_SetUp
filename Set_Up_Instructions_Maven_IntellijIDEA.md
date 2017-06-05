# Install Scala Plugin:  
Configure->Plugins->Browse repositiries->Scala->install  
  
# Configure Maven:    
for Plugin, pluginRepositories, dependencies, Configuration(Include 'Meta' filters for "Invalid Signature file attempt" error.)
Code->Reformate Code.  
  
# Maven:  
include Maven dependies for invalid signature errors  
```
    <configuration>
        <filters>
            <filter>
                <artifact>*:*</artifact>
                <excludes>
                    <exclude>META-INF/*.SF</exclude>
                    <exclude>META-INF/*.DSA</exclude>
                    <exclude>META-INF/*.RSA</exclude>
                </excludes>
            </filter>
        </filters>
    </configuration>
```  

# Configure Project:  
Project Root -> Add FrameWorkSupport(Add)-> Scala  
src->main->new->Directory(create)->scala  
src/main/scala->Mark Directory as->Source Root  
  
# Buliding Jar:  
File->Project Structure->Artifacts->JAR->Build from Modules with dependencies->Select main Class(Module, Main Class)   
Build->Build Artifacts->Build  
  
# Running:  
spark-submit --master yarn --num-executors 40 --driver-memory 20G --executor-cores 20 --executor-memory 45G your_jar.jar your_arguments_location_in _HDFS 2  
