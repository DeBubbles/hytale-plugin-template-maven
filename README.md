# Hytale Plugin Template (Maven)

This repository is a starter template for creating Hytale server plugins using Java + Maven.

It provides:

- A ready-to-build Maven project
- A basic plugin structure
- Example plugin entry point
- Correct dependency setup for the Hytale Server API

Use this template to quickly bootstrap a new plugin.

---

## 🚀 Getting Started
### 1. Create a new repository from this template

Click Use this template on GitHub and create a new repository.

Clone your new repo locally:
```markdown
git clone https://github.com/DeBubbles/hytale-plugin-template-maven
cd your-plugin
```

### 2. Install the Hytale Server API into your local Maven repo

The Hytale server API is not available in a public Maven repository, so you must install it locally.

⚠️ **Important:** The Hytale server jar contains internal Maven metadata that references a parent POM which is not publicly available.  
Because of this, we must install it using a custom minimal POM file instead of letting Maven generate one automatically.

---

#### 2.1 Create a minimal POM file

In the same folder as `HytaleServer.jar`, create a file named:tId=hytale-server \
-Dversion=0.1.0 \
-Dpackaging=jar

Paste the following into it:

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.hytale</groupId>
  <artifactId>hytale-server</artifactId>
  <version>0.1.0</version>
  <packaging>jar</packaging>
  <name>hytale-server</name>
</project>
```
#### 2.2 Install the jar
Run:
````markdown
mvn install:install-file \
  -Dfile=path/to/HytaleServer.jar \
  -DpomFile=path/to/hytale-server-0.1.0.pom
````
Replace `path/to/...` with the actual paths on your machine.

This only needs to be done once per machine.

---
### 3. Rename the project

Edit the following values:

### pom.xml
  - groupId
  - artifactId
  - version

### Rename the folder:

- src/main/java/com/example/Main

to your own package

And update the package line in your main class accordingly.

### Plugin manifest
Edit manifest.json (or equivalent) and update:
  - plugin name
  - main class
  - description
  - author
---
### 4. Build the plugin

Run:
````markdown
mvn clean package
````

Your plugin jar will be generated in:<br>
`target/`<br>
Example:
`target/my-plugin.jar`
---
### 5. Install the plugin on your server

Copy the jar into your Hytale server plugin folder:
`/mods/my-plugin.jar`
Start the server and check the logs:

```markdown
[PluginManager] - com.example:MyPlugin.jar from path MyPlugin-1.0.0.jar
```
---
### 📦 Requirements

- Java 21+

- Maven 3.9+

- Hytale Server build (with plugin support)
---
### 📜 License
This template is released under the MIT license.
You may use it freely for personal or commercial projects.