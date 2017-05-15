# Install Scala pulgin:  
Configure->Plugins->Browse repositiries->Scala->install  
  
# Configure build.sbt[for SpareCore libaries]:  
```
name := "HotelHODRequestParsing_SBT"

version := "1.0"

scalaVersion := "2.10.4"

libraryDependencies ++= {
  val sparkVersion =  "1.5.0"
  Seq(
    "org.apache.spark" %% "spark-core" % sparkVersion,
    "org.apache.spark" %% "spark-sql" % sparkVersion
  )
}
```  
  
# Compile Jar:  
File->ProjectStructure->Artifacts->JAR->Build from Modules with dependencies->Select main Class(Module, Main Class).    
Build->Build Artifact->Build  
  
# If resulted in error:  
Exception in thread "main" java. lang.SecurityException: Invaild Signature file digest for Mainest main attributes.   
zip -d your_jar.jar 'META-INF/.SF' 'META-INF/.RSA' 'META-INF/*SF'  
  
# Running:  
spark-submit --master yarn --num-executors 40 --driver-memory 20G --executor-cores 20 --executor-memory 45G your_jar.jar your_arguments_location_in _HDFS 2  
  
# ToCheck of Jar file Contents:  
jar -tvf your_jar.jar  
