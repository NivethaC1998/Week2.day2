package week2.day2;

import org.openqa.selenium.By;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.support.ui.Select;

import io.github.bonigarcia.wdm.WebDriverManager;

public class NTCreateAccount {
	public static void main(String[] args) throws InterruptedException {
		//To setup driver
		WebDriverManager.chromedriver().setup();	
		ChromeDriver driver=new ChromeDriver();
		//To Load URL
		driver.get("http://leaftaps.com/opentaps/control/login");
		//To Maximize the window
		driver.manage().window().maximize();
		//To capture user name WebElement Element =
		driver.findElement(By.id("username")).sendKeys("Demosalesmanager");
		//To capture password
		driver.findElement(By.id("password")).sendKeys("crmsfa"); 
		//To Login
		driver.findElement(By.className("decorativeSubmit")).click();
		//To click on CRM/SFA Link
		driver.findElement(By.linkText("CRM/SFA")).click();
		//To click on Accounts tab
		driver.findElement(By.linkText("Accounts")).click();
		//To click on Create Account
		driver.findElement(By.linkText("Create Account")).click();
		//driver.findElement(By.id("currencyUomId")).sendKeys("Indian Rupee");
		Select obj = new Select(driver.findElement(By.id("currencyUomId")));
		obj.selectByValue("INR");
		//To Enter Description
		driver.findElement(By.xpath("(//textarea[@name='description'])")).sendKeys("NRI Account");
		//To Enter Local Name
		driver.findElement(By.xpath("(//input[@id='groupNameLocal'])")).sendKeys("Current Account");
		//To Enter Site Name
		driver.findElement(By.xpath("(//input[@id='officeSiteName'])")).sendKeys("Chennai");
		//To Enter Annual Revenue
		driver.findElement(By.xpath("(//input[@class='inputBox'])[5]")).sendKeys("200000");
		//To click on create account
		driver.findElement(By.xpath("//input[@class='smallSubmit']")).click();
		Thread.sleep(5000);
		//To get error message
		System.out.println(driver.findElement(By.className("errorMessage")).getText());
		//To close browser
		driver.close();
	}
}
