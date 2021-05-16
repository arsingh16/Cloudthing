# Cloudthing
//Application form code

package cloudthing.test;

import org.testng.annotations.Parameters;
import org.testng.annotations.Test;

import cloudthing.pages.CloudthingNavigation;

import java.util.concurrent.TimeUnit;

import org.openqa.selenium.JavascriptExecutor;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.support.PageFactory;

public class FillApplicationForm {
	
	
	public static WebDriver driver;
	
	@Parameters({"cloudthing_url"})
	@Test
	public void fillFrormAndSubmit(String urlname) {
		
		System.out.println("!!!!!!!! Executing Test Suite in chrome for Success case !!!!!!!!!!");	 
		System.setProperty("webdriver.chrome.driver","C:/Users/Ashwin/eclipse-workspace/Zest/src/main/resources/chromedriver.exe");
		driver = new ChromeDriver();
		driver.manage().window().maximize();
		driver.manage().timeouts().implicitlyWait(10, TimeUnit.SECONDS);
	    driver.get(urlname);
	   	
	    //Navigation to career page
		CloudthingNavigation cloudthing_nav_page = PageFactory.initElements(driver,CloudthingNavigation.class);
		cloudthing_nav_page.right_menu_button.click();
		
		driver.manage().timeouts().implicitlyWait(5, TimeUnit.SECONDS);
		cloudthing_nav_page.career_page.click();		
		driver.manage().timeouts().implicitlyWait(10, TimeUnit.SECONDS);
		
		//Scrolling down to view search box
		JavascriptExecutor js = (JavascriptExecutor)driver;
		
		js.executeScript("window.scrollBy(0,500)");
		
		//Search Manager job on search box
		
		cloudthing_nav_page.search_text_box.sendKeys("Manager");
		driver.manage().timeouts().implicitlyWait(5, TimeUnit.SECONDS);
		cloudthing_nav_page.arrow_nav_form.click();
		
		//Scrolling down to view form
				
		js.executeScript("window.scrollBy(0,2200)");
		
		//Entering application details
		
		cloudthing_nav_page.name_field.sendKeys ("Arpita");
		cloudthing_nav_page.email_field.sendKeys("test123@gmail.com");
		cloudthing_nav_page.anything_you_like_field.sendKeys("Test");
		cloudthing_nav_page.resume_field.sendKeys("C:\\Users\\Ashwin\\Downloads\\Automation QA Task - October 2019 (2)");
		cloudthing_nav_page.submit.click();
		}
  }  


//Class for all the objects
package cloudthing.pages;

import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.support.FindBy;
import org.openqa.selenium.support.PageFactory;

public class CloudthingNavigation {
	

	public WebDriver driver = null;
	
	public CloudthingNavigation(WebDriver driver) {
		this.driver = driver;
		PageFactory.initElements(driver, this);
		}

    @FindBy(xpath="//*[@id=\'gatsby-focus-wrapper\']/div[1]/div[1]/div/img")
    public WebElement right_menu_button;
    
    @FindBy(xpath="//*[@id=\"gatsby-focus-wrapper\"]/div[1]/div[2]/div[2]/div/div[1]/div[10]/a")
    public WebElement career_page;
    
    @FindBy(xpath="//*[@id=\"gatsby-focus-wrapper\"]/div[3]/div/div/div/div[1]/div[1]/div[2]/input")
    public WebElement search_text_box;
   
    @FindBy(xpath="//*[@id=\"gatsby-focus-wrapper\"]/div[3]/div/div/div/div[2]/div[5]/a/div/img")
    public WebElement arrow_nav_form;
    
    @FindBy(id="name")
    public WebElement name_field;
    
    @FindBy(id="emailaddress")
    public WebElement email_field;
    
    @FindBy(id="anythingyoudliketotellus")
    public WebElement anything_you_like_field;
    
    @FindBy(id="resume")
    public WebElement resume_field;
    
    @FindBy(xpath="//*[@id=\"ctform\"]/button")
    public WebElement submit;  
	
	}

//Testng xml file
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE suite SYSTEM "https://testng.org/testng-1.0.dtd">
<suite name="Cloudthing">
<parameter name="cloudthing_url" value="www.cloudthing.com"></parameter>

<test name="TestCases">
  
    <classes>
      <class name="cloudthing.test.FillApplicationForm"/>
    </classes>
    
  </test> <!-- TestCases -->
</suite> <!-- Cloudthing -->

//pom xml file
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>
  <groupId>Cloudthing</groupId>
  <artifactId>Cloudthing</artifactId>
  <version>0.0.1-SNAPSHOT</version>
  <dependencies>
  <!-- https://mvnrepository.com/artifact/org.seleniumhq.selenium/selenium-java -->
  <dependency>
    <groupId>org.seleniumhq.selenium</groupId>
    <artifactId>selenium-java</artifactId>
    <version>3.141.59</version>
  </dependency>
   <dependency>
     <groupId>org.testng</groupId>
            <artifactId>testng</artifactId>
            <version>6.8.8</version>
    </dependency>
  </dependencies>
</project>
