✅ Option 1: Use Locally Built JAR (Simple & Fast)
🔨 Step 1: Install the Recipe Locally
Go into the recipe project (from the ZIP), then run:

bash
Copy
Edit
mvn clean install
This will install your custom recipe JAR into your local Maven repository (~/.m2/repository).

🔍 Step 2: Add Plugin to Your Target Project’s pom.xml
In the target Java project (the one you want to refactor), add the Rewrite plugin and dependencies:

xml
Copy
Edit
<plugin>
  <groupId>org.openrewrite.maven</groupId>
  <artifactId>rewrite-maven-plugin</artifactId>
  <version>5.10.0</version>
</plugin>
🏃 Step 3: Run the Recipe
From the target project folder:

bash
Copy
Edit
mvn rewrite:run -DactiveRecipes=com.example.BanThreadSleep
You can also try:

bash
Copy
Edit
mvn rewrite:discover
To list available recipes including your custom ones.

✅ Option 2: Publish to GitHub + Maven (Reusable by Team/CI)
This is useful if you want to reuse recipes across many repos or share with teammates.

🔨 Step 1: Push Recipe Project to GitHub
Initialize the project and push:

bash
Copy
Edit
git init
git remote add origin git@github.com:krunaldeshpande/rewrite-scalability-recipes.git
git push -u origin main
🧪 Step 2: Publish to a Maven Repo (Optional but Ideal)
 GitHub Packages (free)

 Jitpack.io (very easy to use for private/public GitHub)

 Internal Nexus/Artifactory

<details> <summary>🔧 Use JitPack (Easy)</summary>
Add to target project pom.xml:

xml
Copy
Edit
<repositories>
  <repository>
    <id>jitpack.io</id>
    <url>https://jitpack.io</url>
  </repository>
</repositories>

<dependency>
  <groupId>com.github.krunaldeshpande</groupId>
  <artifactId>rewrite-scalability-recipes</artifactId>
  <version>main</version> <!-- or a tag -->
</dependency>
Run as normal with:

bash
Copy
Edit
mvn rewrite:run -DactiveRecipes=com.example.BanThreadSleep
</details>
🧠 Tips
Need	Solution
Quickly apply recipes on your machine	Use local mvn install
Share across team	Push to GitHub + Jitpack/Maven
Run on many repos	Use Moderne
Discover your custom recipes	Run mvn rewrite:discover
