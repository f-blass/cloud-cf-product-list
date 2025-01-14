# Cloning sample application git from Github

## Estimated time

:clock4: 5 minutes

## Objective

In this exercise you'll learn how you can clone the Product List sample application, import it in your local Eclipse environment as Maven Project and build it.

# Exercise description

## 1. Download the sample code as zip
1. Go to the root of the project in github: https://github.com/SAP/cloud-cf-product-list-sample. Make sure that you are in the right branch: ```teched2019```.

2. Click on **Clone or download** button and select ```Download ZIP```
<br><br>
![Download ZIP](/img/github_download_zip.png?raw=true)
<br><br>

3.  Unzip the downloaded file in your students directory - a new directory ```cloud-cf-product-list-sample-teched2019``` will be created.

## 2. Import the sample project into Eclipse
1. Open the Windows Start menu and enter ```CPL...``` in the input field. Under ```Programs``` you will see ```ABAP in Eclipse - CPL...```. Click on this entry to open Eclipse.
2. Now import the two sample projects as Maven project into your Eclipse workspace: In the Eclipse menu, chose ```File```> ```Import...```.
3. In the ```Import``` wizard, select ```Maven``` > ```Existing Maven Projects``` and click ```Next```.
<br><br>
![Import Maven Project](/img/import_maven_project.png?raw=true)
<br><br>

4. In the next step of the ```Import Maven Projects``` popup, click ```Browse```, navigate into the unziped root folder of ```cloud-cf-product-list-sample-teched2019``` project in your student directory folder (```D:\Files\Session\CPL...```). In the wizard select both projects (java and spring) and finally click ```Finish```.
5. Both projects are now imported in Eclipse. You should see them in the Project Explorer like in the screenshot below.  
<br><br>
![Import Maven Project](/img/imported_project_eclipse.png?raw=true)
<br><br>

## 3. Build the project in Eclipse using Maven  

1. Now build the project in Eclipse: Select the project in the Project Explorer, open its context menu and click on ```Run As``` > ```Maven build...```.
<br><br>
![Import Maven Project](/img/run_maven_build.png?raw=true)
<br><br>

2. In the ```Edit Configuration```popup, enter ```clean install``` into the ```Goals```field and click ```Run```. 
<br><br>
![Import Maven Project](/img/maven_clean_install.png?raw=true)
<br><br>

3. The Maven build should fail with some JUnit Test errors which will be fixed along this Exercise:
   <br><br>
   ![Import Maven Project](/img/maven_clean_install_build_error.png?raw=true)
   <br><br>


***
<dl>
  <dd>
  <div class="footer">&copy; 2019 SAP SE</div>
  </dd>
</dl>
<hr>
<a href="/exercises/01_setup/README.md">
  <img src="/img/arrow_left.png" height="80" border="10" align="left" alt="Previous Exercise" title="Previous Exercise: Setup environment">
</a>
<a href="/exercises/09_secure/README.md">
  <img src="/img/arrow_right.png" height="80" border="10" align="right" alt="Next Exercise" title="Next Exercise: Secure your application">
</a>

