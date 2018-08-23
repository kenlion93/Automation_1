# Automation_1
Main value in the FW
- Suite?
- Browser?
- Maven -> manage the libary

Find element:
- By name, id
- By xpath (bao nhiu loai xpath?)

package first_test;

import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.testng.Assert;
import org.testng.annotations.Test;

import automationCore.DriverFactory;

public class TMA_solution extends DriverFactory {

	@Test
	public void searchTMA() throws Exception {
		// Open browser
		WebDriver driver = getDriver();

		// Maximum browser
		driver.manage().window().maximize();

		// Rediect to Google.com
		driver.get("https://www.google.com");

		// Input value to Google search textbox
		WebElement input = driver.findElement(By.name("q"));

		input.sendKeys("TMA Solution");
		input.submit();

		Thread.sleep(2000);

		// select the 1st repsonse value
		WebElement firstitem = driver.findElement(By.xpath("//*[@id=\"rso\"]/div[1]/div/div[1]/div/div/h3/a"));
		firstitem.click();
		Thread.sleep(2000);

		// verift the right website
		Assert.assertTrue(driver.getCurrentUrl().equals("https://www.tma.vn/"));
		Thread.sleep(3000);

		System.out.print("Welcome to TMA website");

	}
}
