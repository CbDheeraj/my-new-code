import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;
import java.util.Set;
import java.util.concurrent.TimeUnit;

import org.openqa.selenium.By;
import org.openqa.selenium.JavascriptExecutor;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.support.ui.Select;
import org.testng.Assert;

public class AmazonTest {

	public static void main(String[] args) throws InterruptedException {
		// TODO Auto-generated method stub

		ChromeDriver driver = new ChromeDriver();
		driver.manage().window().maximize();
		driver.manage().timeouts().implicitlyWait(5000, TimeUnit.SECONDS);
		driver.get("https://www.amazon.in/");
		driver.findElement(By.id("twotabsearchtextbox")).sendKeys("iphone");
		driver.findElement(By.id("nav-search-submit-button")).click();
		List<WebElement>allList = driver.findElements(By.xpath("//div[@class=\"s-main-slot s-result-list s-search-results sg-row\"]/div//h2/a"));
		System.out.println(allList.size());
		for(int i=0;i<allList.size();i++){
			
			if(allList.get(i).getText().contains("Apple iPhone 15 (128 GB) - Black")) {
				
				allList.get(i).click();
			}
			
			
		}
		
		Set<String> s = driver.getWindowHandles();
		ArrayList ar = new ArrayList(s);
		System.out.println(ar.get(0));
		System.out.println(ar.get(1));
		
		driver.switchTo().window((String)ar.get(1));

		JavascriptExecutor js = (JavascriptExecutor) driver;
		js.executeScript("window.scrollBy(0,250)", "");
		
		driver.findElement(By.xpath("(//span[@id='submit.add-to-cart'])[2]")).click();
		Thread.sleep(5000);
		driver.findElement(By.xpath("(//span[@id='attach-sidesheet-checkout-button']/span)")).click();
		driver.findElement(By.name("email")).sendKeys("Dheerajgupta90@gmail.com");
		driver.findElement(By.id("continue")).click();
		driver.findElement(By.name("password")).sendKeys("Dhee@2707");
		driver.findElement(By.id("signInSubmit")).click();
		Scanner sc = new Scanner(System.in);
		String otp = "";
		System.out.println("Enter the otp code");
		otp = sc.next();
		driver.findElement(By.name("otpCode")).click();
		driver.findElement(By.name("otpCode")).sendKeys(otp);
	
	
		driver.findElement(By.id("auth-signin-button")).click();
		
		driver.findElement(By.xpath("//a[@id='add-new-address-popover-link']")).click();
		driver.findElement(By.xpath("//input[@id='address-ui-widgets-enterAddressFullName']")).sendKeys("Dheeraj Gupta");
		driver.findElement(By.xpath("//input[@id='address-ui-widgets-enterAddressPhoneNumber']")).sendKeys("9897776654");
		driver.findElement(By.id("address-ui-widgets-enterAddressPostalCode")).sendKeys("201307");
		driver.findElement(By.xpath("//input[@id='address-ui-widgets-enterAddressLine1']")).sendKeys("b-64 Arwali apartment noida sector 34");
		driver.findElement(By.xpath("//input[@id='address-ui-widgets-enterAddressLine2']")).sendKeys("Noida sector 34 ");
		driver.findElement(By.cssSelector("input[id='address-ui-widgets-landmark']")).sendKeys("Near 34 metro station ");
		driver.findElement(By.cssSelector("input[id='address-ui-widgets-enterAddressCity']")).sendKeys("Noida");
		//Select dropdown = new Select(driver.findElement(By.cssSelector("span[id='address-ui-widgets-enterAddressStateOrRegion']")));
		//dropdown.selectByVisibleText("Delhi");
		driver.findElement(By.xpath("//input[@aria-labelledby='address-ui-widgets-form-submit-button-announce']")).click();
		
		driver.findElement(By.xpath("//span/div/i[1]")).click();
		
		
		
		//driver.quit();
	}

}
